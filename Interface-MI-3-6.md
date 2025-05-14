Title: openSIPS | Documentation / Management Interface

URL Source: https://www.opensips.org/Documentation/Interface-MI-3-6

Markdown Content:
| Documentation

*   [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals")
*   [Advanced Tutorials](https://www.opensips.org/Documentation/Tutorials "Tutorials")
*   [Tips & FAQ](https://www.opensips.org/Documentation/TipsFAQ "TipsFAQ")
*   [Version Migration](https://www.opensips.org/Documentation/Migration "Migration")
*   [OpenSIPS Webinars](https://www.opensips.org/Documentation/Webinars "Webinars")
*   [Troubleshooting](https://www.opensips.org/Documentation/Troubleshooting "Troubleshooting")
*   [OpenSIPS Tools](https://www.opensips.org/Documentation/Tools "Tools")
*   [Devel Tutorial](https://www.opensips.org/Documentation/Development-Tutorials "Development-Tutorials")

 | 

##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Management Interface

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Interface-MI-3-5 "Management Interface - 3.5") [3.4](https://www.opensips.org/Documentation/Interface-MI-3-4 "Management Interface - 3.4") Older versions: [3.3](https://www.opensips.org/Documentation/Interface-MI-3-3 "Management Interface - 3.3") [3.2](https://www.opensips.org/Documentation/Interface-MI-3-2 "Management Interface - 3.2") [3.1](https://www.opensips.org/Documentation/Interface-MI-3-1 "Management Interface - 3.1") [3.0](https://www.opensips.org/Documentation/Interface-MI-3-0 "Management Interface - 3.0") [2.4](https://www.opensips.org/Documentation/Interface-MI-2-4 "Management Interface - devel") [2.3](https://www.opensips.org/Documentation/Interface-MI-2-3 "Management Interface - devel") [2.2](https://www.opensips.org/Documentation/Interface-MI-2-2 "Management Interface - 2.2") [2.1](https://www.opensips.org/Documentation/Interface-MI-2-1 "Management Interface - devel") [1.11](https://www.opensips.org/Documentation/Interface-MI-1-11 "Management Interface - 1.11") [1.10](https://www.opensips.org/Documentation/Interface-MI-1-10 "Management Interface - ver 1.10") [1.9](https://www.opensips.org/Documentation/Interface-MI-1-9 "Management Interface - ver 1.9") [1.8](https://www.opensips.org/Documentation/Interface-MI-1-8 "Management Interface - ver 1.8") [1.7](https://www.opensips.org/Documentation/Interface-MI-1-7 "Management Interface - ver 1.7") [1.6](https://www.opensips.org/Documentation/Interface-MI-1-6 "Management Interface - ver 1.6") [1.5](https://www.opensips.org/Documentation/Interface-MI-1-5 "Management Interface - ver 1.5") [1.4](https://www.opensips.org/Documentation/Interface-MI-1-4 "Management Interface - ver 1.4")

**Management Interface v3.6**

* * *

The **Management Interface** (or **MI**) is an OpenSIPS interface that allows external applications to trigger predefined commands inside OpenSIPS.

#### Overview

Such commands typically allows an external app to :

1.  push data into OpenSIPS (like setting debug level, registering a contact, etc)
2.  fetch data from OpenSIPS (see registered users, see ongoing calls, get statistics, etc)
3.  trigger an internal action in OpenSIPS (reloading data, sending a message, etc)

The **MI** commands are provided by the OpenSIPS core (see [full list](https://www.opensips.org/Documentation/Interface-CoreMI-3-6 "Core MI Functions - 3.6")) and also by modules (check the commands provided by [each module](https://www.opensips.org/Documentation/Modules-3-6 "Modules - 3.6")).

* * *

#### Protocols

The protocols available in order to connect (from external apps) to the OpenSIPS **MI** are JSON-RPC over several transports and XML-RPC. While the interface itself (tailored around the JSON format) is provided by the OpenSIPS core, each actual transport protocol is provided by a separate OpenSIPS module. You can load multiple MI modules in order to use multiple MI transport protocols at the same time.

The majority of the MI backend modules only provide the transport, while the command parsing and response formatting (as **JSON-RPC**) is done by the OpenSIPS core. The only exceptions are the _mi\_html_ and _mi\_xmlrpc\_ng_ modules, which use a different format.

The available MI modules are :

*   **mi\_fifo** - provides JSON-RPC transport via a FIFO file; OpenSIPS reads from a predefined FIFO file, where the external apps are writing down the MI commands. As the file is actually as stream of data, there is no restrictions here on the amount of data OpenSIPS may return (when fetching data from OpenSIPS).
*   **mi\_datagram** - provides JSON-RPC transport either via UNIX SOCKETS, or via UDP packets; OpenSIPS listens for MI commands on UDP port(s) or unisock files; The transported data is limited to the size of a Datagram (65K).
*   **mi\_http** - provides JSON-RPC transport over HTTP. As TCP is used, there is no limit in regards to the amount of transfered data.
*   **mi\_html**\- provides a way of issuing MI commands directly from a web browser via an HTML page. The command's parameters are passed in the URL's query string. Although not conforming to JSON-RPC, the MI responses are still delivered in JSON format within the page.
*   **mi\_xmlrpc\_ng** - implements XML-RPC by not only providing an HTTP transport but also by translating between the MI's internal JSON format and XML.
*   **mi\_script** - provides the ability to run MI commands directly from OpenSIPS' script, returning the result as a JSON string.

All protocols do allow multiple applications (clients) to connect at the same time to the MI interface.

* * *

#### Examples

A few examples of JSON-RPC calls for OpenSIPS:

\# Request with no parameters:
{
  "jsonrpc": "2.0",
  "method": "ps",
  "id": 10
}

# Response:
{
  "jsonrpc":  "2.0",
  "result": {
    "Processes":  \[{
        "ID": 0,
        "PID":  9467,
        "Type": "attendant"
      }, {
        "ID": 1,
        "PID":  9468,
        "Type": "HTTPD 127.0.0.1:8008"
      }, {
        "ID": 3,
        "PID":  9470,
        "Type": "time\_keeper"
      }, {
        "ID": 4,
        "PID":  9471,
        "Type": "timer"
      }, {
        "ID": 5,
        "PID":  9472,
        "Type": "SIP receiver udp:127.0.0.1:5060 "
      }, {
        "ID": 7,
        "PID":  9483,
        "Type": "Timer handler"
      }, \]
  },
  "id": 10
}

# Request with positional parameters:
{
  "jsonrpc": "2.0",
  "method": "log\_level",
  "params": \[4, 9472\],
  "id": 11
}

# Request with named parameters:
{
  "jsonrpc": "2.0",
  "method": "log\_level",
  "params": {
    "level": 4,
    "pid": 9472
  },
  "id": 11
}

# Request with an array type of parameter:
{
  "jsonrpc": "2.0",
  "method": "get\_statistics",
  "params": {
    "statistics": \["shmem:", "core:"\]
  },
  "id": 11
}

A simple example of interacting with OpenSIPS via MI interfaces is the **opensips-cli** utility - it uses FIFO to push MI commands into OpenSIPS:

    opensips-cli -x mi ps
    opensips-cli -x mi log\_level 4 9472

Example of sending a JSON-RPC OpenSIPS MI command from the command-line, using _curl_:

$ curl -X POST localhost:8888/mi -H 'Content-Type: application/json' -d '{"jsonrpc": "2.0", "id": "1", "method": "ps"}'




 |
