Title: openSIPS | Documentation / Asynchronous Statements

URL Source: https://www.opensips.org/Documentation/Script-Async-3-6

Markdown Content:
##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Asynchronous Statements

This page has been visited 632 times.

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Script-Async-3-5 "Asynchronous Statements - 3.5") [3.4](https://www.opensips.org/Documentation/Script-Async-3-4 "Asynchronous Statements - 3.4") Older versions: [3.3](https://www.opensips.org/Documentation/Script-Async-3-3 "Asynchronous Statements - 3.3") [3.2](https://www.opensips.org/Documentation/Script-Async-3-2 "Asynchronous Statements - 3.2") [3.1](https://www.opensips.org/Documentation/Script-Async-3-1 "Asynchronous Statements - 3.1") [3.0](https://www.opensips.org/Documentation/Script-Async-3-0 "Asynchronous Statements - 3.0") [2.4](https://www.opensips.org/Documentation/Script-Async-2-4 "Asynchronous Statements - 2.4") [2.3](https://www.opensips.org/Documentation/Script-Async-2-3 "Asynchronous Statements - 2.3") [2.2](https://www.opensips.org/Documentation/Script-Async-2-2 "Asynchronous Statements - 2.2") [2.1](https://www.opensips.org/Documentation/Script-Async-2-1 "Asynchronous Statements - 2.1")

**Asynchronous Statements v3.6**

* * *

**Table of Content** (hide)

1.  1. [Description](https://www.opensips.org/Documentation/Script-Async-3-6#toc1)
2.  2. [Serial asynchronous operations, async()](https://www.opensips.org/Documentation/Script-Async-3-6#toc2)
    1.  2.1 [Requirements](https://www.opensips.org/Documentation/Script-Async-3-6#toc3)
    2.  2.2 [Script syntax and usage](https://www.opensips.org/Documentation/Script-Async-3-6#toc4)
3.  3. [Parallel asynchronous operations, launch()](https://www.opensips.org/Documentation/Script-Async-3-6#toc5)
    1.  3.1 [Script syntax and usage](https://www.opensips.org/Documentation/Script-Async-3-6#toc6)
4.  4. [List of async functions](https://www.opensips.org/Documentation/Script-Async-3-6#toc7)
5.  5. [Limitations](https://www.opensips.org/Documentation/Script-Async-3-6#toc8)
    1.  5.1 [Async Engine Compatibility](https://www.opensips.org/Documentation/Script-Async-3-6#toc9)
    2.  5.2 [TCP Connect Issues](https://www.opensips.org/Documentation/Script-Async-3-6#toc10)
    3.  5.3 [Allowed Routes](https://www.opensips.org/Documentation/Script-Async-3-6#toc11)

### 1.  Description

Asynchronous statements are one of the key features of OpenSIPS 2.X. One of the main reasons to use them is that they allow the performance of the OpenSIPS script to scale with a high number of requests per second even when doing blocking I/O operations such as MySQL queries, exec commands or HTTP requests.

Using the asynchronous, "suspend-resume" logic instead of forking a large number of processes in order to scale also has the advantage of optimizing system resource usage, increasing its maximal throughput. By requiring less processes to complete the same amount of work in the same amount of time, process context switching is minimized and overall CPU usage is improved. Less processes will also eat up less system memory.

### 2.  Serial asynchronous operations, async() [🔗](https://www.opensips.org/Documentation/Script-Async-3-6#async)

The **async()** statement of the OpenSIPS script can be used in situations where the script writer both needs to perform blocking I/O and also depends on the result of this operation. Some example scenarios:

*   fetch SIP authentication data from a database
*   perform an HTTP query and act upon its result
*   pause script execution for X seconds
*   exec an external script and use its result

#### 2.1  Requirements

The **async()** statement depends on the transaction module (**tm**) - it must be loaded. The SIP transaction will be automatically and transparently created when an async operation is started, if necessary. This transaction contains all the necessary information to suspend script execution (e.g. it stores the updated SIP message, along with all $avp variables).

#### 2.2  Script syntax and usage

Usage is straightforward: if your blocking function supports asynchronous mode (read the module documentation for this), then you can just throw it in the following function call:

async(blocking\_function(...), resume\_route \[,timeout\]);

_Note that resume\_route must be a **[simple route](http://www.opensips.org/Documentation/Script-Routes-3-6#toc1)**_.

Because the **async()** statement is serial with script execution (see below), the script will be immediately halted when calling it, so any code placed after the async() call will be ignored! The current OpenSIPS worker will launch the asynchronous operation, after which it will continue to process other pending tasks (queued SIP messages, timer jobs or possibly other async operations!). As soon as all data is available, it will run the resume route - thus resuming script execution with a minimum of idle time.

The return code of the function executed in async mode is available in the very beginning of the resume route in the **$rc** or **$retcode** variable. Also, all output parameters (variables in function parameters used to carry output values) will be available in resume route.

The optional 'timeout' parameter is to control for how long the script should wait for the blocking function to complete (independently from its implementation). If the blocking I/O is not completed before the given timeout, the async layer will force the function to complete (with timeout) its I/O and to resume the script.

route
{
    /\* preparation code \*/
    ...
    async(avp\_db\_query("SELECT credit FROM users WHERE uid='$avp(uid)'", "$avp(credit)"), resume\_credit);
    /\* script execution is paused right away! \*/
}

route \[resume\_credit\]
{
    if ($rc < 0) {
        xlog("error $rc in avp\_db\_query()\\n");
        exit;
    }

    xlog("Credit of user $avp(uid) is $avp(credit)\\n");
    ...
    t\_relay();
}

Data is copied over to the resume route as follows:

**Preserved data (still available in resume route)**

*   **all $avp variables**
*   **all changes in current SIP message**

**Ignored data (not available anymore in resume route)**

*   **all $var variables**

### 3.  Parallel asynchronous operations, launch() [🔗](https://www.opensips.org/Documentation/Script-Async-3-6#launch)

The **launch()** statement of the OpenSIPS script can be used in situations where the script writer needs to perform blocking I/O, but does not depend on the result of this operation in order to continue the current SIP routing decision flow. Some example scenarios:

*   execute an external push notification trigger
*   push data into a custom database (e.g. call statistics, CDRs, etc.)
*   notify an HTTP service of the occurrence of an event (e.g. SIP traffic pattern, fraud detection, etc.)

The **launch()** statement comes with no additional module dependencies.

#### 3.1  Script syntax and usage

Similarly to the **async()** statement, if your blocking function supports asynchronous mode (read the module documentation for this), then you can just throw it in the following function calls:

launch(blocking\_function(...));
or
launch(blocking\_function(...), report\_route);
route\[report\_route\] {}
or
launch(blocking\_function(...), report\_route, "Something with $var(xx) to be passed to report route");
route\[report\_route\] {
   xlog("received as input the <$param(1)\> string\\n");
}

_Note that report\_route must be a **[simple route](http://www.opensips.org/Documentation/Script-Routes-3-6#toc1)**_.

The **launch()** statement is both asynchronous and parallel with the script execution that follows it (see below). Notice how the _"report\_route"_ can be omitted, as script execution does not depend on it. This route may be triggered at any of the following points in time:

*   right before the next code line following the **launch()** call
*   during the routing of the current SIP message
*   after the routing of the current SIP message

The return code of the function executed in async mode is available in the very beginning of the report route in the **$rc** or **$retcode** variable. Also, only the output parameters (variables in function parameters used to carry output values) will be available inside this route.

route
{
    /\* preparation code \*/
    ...

    # send a push notification asynchronously, in parallel
    launch(exec("/usr/local/bin/send-google-pn.py"), pn\_counter);
    t\_relay();
}

route \[pn\_counter\]
{
    if ($rc < 0) {
        xlog("error $rc in pn script!\\n");
        update\_stat("pn-failure", "1");
        exit;
    }

    update\_stat("pn-success", "1");
}

**Preserved data (still available in report route)**

*   output variables set by the async function

**Ignored data (not available anymore in report route)**

*   **any other variable**
*   **the initial SIP message**

### 4.  List of async functions [🔗](https://www.opensips.org/Documentation/Script-Async-3-6#async_functions)

The following functions may also be called asynchronously:

*   [avp\_db\_query](http://www.opensips.org/html/docs/modules/3.6.x/avpops.html#id294986)
*   [rest\_get](http://www.opensips.org/html/docs/modules/3.6.x/rest_client.html#id293741)
*   [rest\_post](http://www.opensips.org/html/docs/modules/3.6.x/rest_client.html#id293886)
*   [rest\_put](http://www.opensips.org/html/docs/modules/3.6.x/rest_client.html#id293886)
*   [exec](http://www.opensips.org/html/docs/modules/3.6.x/exec#id294052)
*   [ldap\_search](http://www.opensips.org/html/docs/modules/3.6.x/ldap.html#ldap-search-async-fn)
*   [sleep](http://www.opensips.org/html/docs/modules/3.6.x/cfgutils.html#id294676)

The async implementation is not limited to the above functions, but these are the first ones migrated to async support. More I/O related functions will be ported to the async support.

### 5.  Limitations [🔗](https://www.opensips.org/Documentation/Script-Async-3-6#async_limitations)

#### 5.1  Async Engine Compatibility

The async engine is heavily dependent on non-blocking I/O features exposed by the underlying libraries -- a blocking I/O operation, such as an HTTP or an SQL query can only be made asynchronous if the library additionally provides both:

*   a non-blocking equivalent of the same, originally blocking function
*   after the non-blocking equivalent function is launched, the library must also provide a mechanism to extract a valid Linux file descriptor corresponding to the data transfer operation that has just been launched. The OpenSIPS async engine will poll on this fd, and will trigger internal state updates each time new data is available. When the blocking operation is finished, the "resume route" gets called, and the async operation is finalized.

#### 5.2  TCP Connect Issues

Although they provide async functionality, some libraries only do this for the "transfer" part of the I/O operation, and NOT the initial TCP connect. Consequently, on some corner-case scenarios (e.g. the TCP connect hangs due to an unresponsive server, an in-between firewall which drops packets instead of rejecting them, etc.) the async operation may actually block!

Examples of modules which are affected by this limitation:

*   rest\_client - although it reuses TCP connections on further requests, libcurl will block until a TCP connection is established from a given OpenSIPS worker. Should these TCP connects ever hang, so will the corresponding OpenSIPS worker.
*   db\_mysql - similar to rest\_client: although it reuses DB connections heavily, establishing each connection is a blocking operation, and cannot be made async due to the nature of the library.

**Mitigation**: depending on your specific setup, you may be severely impacted by these blocking TCP connects or hardly at all. For the former case, we suggest forking external processes responsible for your blocking operations and invoke them asynchronously, using constructs such as:

`  async(exec("curl my_host", $var(response_body)), resume_route); `

or

`  async(exec("mysql-query 'SELECT * FROM subscriber...'", $var(result_row)), resume_route); `

#### 5.3  Allowed Routes [🔗](https://www.opensips.org/Documentation/Script-Async-3-6#async_routes)

Since the **async** operations are tightly coupled with the transactional engine, they can only be performed in routes where a SIP transaction is present and is awaiting completion:

*   request\_route
*   branch\_route (_may be included in the future_)
*   onreply\_route (_may be included in the future_)
*   local\_route (_may be included in the future_)

On the other hand, the **launch** statement should work from **any route**, as it is not dependent on the underlying SIP transaction.
