Title: openSIPS | Documentation / Script Syntax

URL Source: https://www.opensips.org/Documentation/Script-Syntax-3-6

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

##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Script Syntax

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Script-Syntax-3-5 "Script Syntax - 3.5") [3.4](https://www.opensips.org/Documentation/Script-Syntax-3-4 "Script Syntax - 3.4") Older versions: [3.3](https://www.opensips.org/Documentation/Script-Syntax-3-3 "Script Syntax - 3.3") [3.2](https://www.opensips.org/Documentation/Script-Syntax-3-2 "Script Syntax - 3.2") [3.1](https://www.opensips.org/Documentation/Script-Syntax-3-1 "Script Syntax - 3.1") [3.0](https://www.opensips.org/Documentation/Script-Syntax-3-0 "Script Syntax - 3.0") [2.4](https://www.opensips.org/Documentation/Script-Syntax-2-4 "Script Format - 2.4") [2.3](https://www.opensips.org/Documentation/Script-Syntax-2-3 "Script Format - 2.3") [2.2](https://www.opensips.org/Documentation/Script-Syntax-2-2 "Script Format - 2.2") [2.1](https://www.opensips.org/Documentation/Script-Syntax-2-1 "Script Format - 2.1") [1.11](https://www.opensips.org/Documentation/Script-Syntax-1-11 "Script Format - 1.11") [1.10](https://www.opensips.org/Documentation/Script-Syntax-1-10 "Script Format - ver 1.10") [1.9](https://www.opensips.org/Documentation/Script-Syntax-1-9 "Script Format - ver 1.9") [1.8](https://www.opensips.org/Documentation/Script-Syntax-1-8 "Script Format - ver 1.8") [1.7](https://www.opensips.org/Documentation/Script-Syntax-1-7 "Script Format - ver 1.7") [1.6](https://www.opensips.org/Documentation/Script-Syntax-1-6 "Script Format - ver 1.6") [1.5](https://www.opensips.org/Documentation/Script-Syntax-1-5 "Script Format - ver 1.5") [1.4](https://www.opensips.org/Documentation/Script-Syntax-1-4 "Script Format - ver 1.4")

**Script Syntax v3.6**

**Table of Content** (hide)

1.  1. [Script Format](https://www.opensips.org/Documentation/Script-Syntax-3-6#toc1)
    1.  1.1 [Global parameters](https://www.opensips.org/Documentation/Script-Syntax-3-6#toc2)
    2.  1.2 [Modules section](https://www.opensips.org/Documentation/Script-Syntax-3-6#toc3)
    3.  1.3 [Routing logic](https://www.opensips.org/Documentation/Script-Syntax-3-6#toc4)
2.  2. [Data Types](https://www.opensips.org/Documentation/Script-Syntax-3-6#toc5)
3.  3. [Function Calling Conventions](https://www.opensips.org/Documentation/Script-Syntax-3-6#toc6)

* * *

1.  Script Format
-----------------

The OpenSIPs configuration script has three main logical parts:

1.  global parameters
2.  modules section
3.  routing logic

* * *

#### 1.1  Global parameters

Usually, in the first part, you declare the [OpenSIPS global parameters](https://www.opensips.org/Documentation/Script-CoreParameters-3-6 "Core Parameters - 3.6") - these global or core parameters are affecting the OpenSIPS core and possible the modules.

Configuring the network listeners, available transport protocols, forking (and number of processes), the logging and other global stuff is provided by these global parameters.

Example:

disable\_tcp = yes
listen = udp:192.168.3.60:5060
listen = udp:192.168.3.60:5070
fork = yes
children = 4
log\_stderror = no

* * *

#### 1.2  Modules section

In regards to the OpenSIPS modules,the modules that are to be loaded (no module is loaded by default) are specified by using the directive **loadmodule**. Modules are to be specified by name and an optional path (to the _.so_ file). If no path is provided (and just the name of the module), the default path will be assumed for locating the loading the module (default path is _/usr/lib/opensips/modules_ if not other one configured at [compile time](https://www.opensips.org/Documentation/Install-CompileAndInstall-3-6 "Compile and Install - 3.6"). For configuring a different path, either the path is pushed directly with the module name (to get control per module) or it can be globally (for all modules) configured via the **mpath** global parameter.

Once the modules are loaded, the parameters of the modules may be set using the **modparam** directive - to list of available parameters for each module, the type of parameter value (integer or string) can be found in the [documentation of the modules](https://www.opensips.org/Documentation/Modules-3-6 "Modules - 3.6"), the _Parameters_ section.

Examples:

loadmodule "modules/mi\_datagram/mi\_datagram.so"
modparam("mi\_datagram", "socket\_name", "udp:127.0.0.1:4343")
modparam("mi\_datagram", "children\_count", 3)

or

mpath="/usr/local/opensips\_proxy/lib/modules"
loadmodule "mi\_datagram.so"
modparam("mi\_datagram", "socket\_name", "udp:127.0.0.1:4343")
modparam("mi\_datagram", "children\_count", 3)
loadmodule "mi\_fifo.so"
modparam("mi\_fifo", "fifo\_name", "/tmp/opensips\_fifo")

* * *

#### 1.3  Routing logic

The routing logic is actually a sum of routes (script routes) that contain the OpenSIPS logic for routing SIP traffic. The description of **OpenSIPS behavior in relation to the SIP traffic** is done via this routes.

There are different types of routes :

1.  **top routes** - routes that are directly triggered by OpenSIPs when some events occurs (like SIP request received, SIP reply received, transaction failed, etc)
2.  **sub-routes** - routes that are triggered / used from other routes in script.

What are the existing **top routes**, when they are triggered, what kind of SIP messages is handled, what SIP operations are allowed and other are documented in the [types of routes section](https://www.opensips.org/Documentation/Script-Routes-3-6 "Types of routes - 3.6").

The **sub-routes** have names and they are to be called from any other route (top or sub) in the script via their names. The **sub-routes** may take parameters (when called) or return a numerical code (avoid returning 0 value as this will terminate your whole script. The **sub-routes** are similar to functions / procedure in any programing language. See the [description of the _route_](https://www.opensips.org/Documentation/Script-CoreFunctions-3-6#toc41 "Core Functions - 3.6") directive.

2.  Data Types
--------------

The OpenSIPS scripting language supports the following data types:

### Basic

*   _integer_ (32-bit, signed).
    *   Max value: +2,147,483,647 == 2 ^ 31 - 1
    *   Min value: -2,147,483,648 == - 2 ^ 31
*   _string_ (unlimited size)
    *   note that some functions which use strings may have internal buffers which limit the maximum size of the strings (e.g. the [xlog()](https://www.opensips.org/Documentation/Script-CoreFunctions-3-6#toc54) function's output buffer is configurable via [xlog\_buf\_size](https://www.opensips.org/Documentation/Script-CoreParameters-3-6#toc96))
*   _double_ (packed as string), through the **[mathops](https://opensips.org/docs/modules/3.6.x/mathops.html)** module

### Complex

*   _list_ via the **[$avp variable](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc2)**
*   _map_ via the **[$json](https://opensips.org/docs/modules/3.6.x/json.html#pv_json)** and **[$xml](https://opensips.org/docs/modules/3.6.x/xml.html#pv_xml)** variables

3.  Function Calling Conventions
--------------------------------

All OpenSIPS [core](https://www.opensips.org/Documentation/Script-CoreFunctions-3-6) and [module](https://www.opensips.org/Documentation/Function-Index-3-6) functions internally share the same function interface, such that they benefit from the following calling convention:

*   **any integer or string function parameter may also be passed using a "holder" variable**

ds\_select\_dst(1, 1); 

... is equivalent to:

$var(x) = 1;
ds\_select\_dst($var(x), $var(x));

*   **any string function parameter can be passed as a format string**

set\_dlg\_profile("caller", "$var(country\_code)\_$var(area)\_$fU");

Literal **"$"** characters can be included in a format string using the **"$$"** escape sequence

**NOTE**: There still are a few exceptions for the conventions above in the case of string parameters, due to performance optimizations, as some functions still require some parameters to be plain, static strings (e.g. _save("location")_). Such cases will be noted in the function's documentation.

*   **input or output variables passed to functions must not be quoted**:

ds\_count(1, "a", $var(out\_result));

*   **integers no longer need to be passed as double-quoted strings**:

~ds\_select\_dst("1", "1");~

ds\_select\_dst(1, 1);




 |
