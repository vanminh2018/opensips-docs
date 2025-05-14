Title: openSIPS | Documentation / Configuration File

URL Source: https://www.opensips.org/Documentation/Configure-File-3-6

Markdown Content:
##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Configuration File

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Configure-File-3-5 "Configuration File - 3.5") [3.4](https://www.opensips.org/Documentation/Configure-File-3-4 "Configuration File - 3.4") Older versions: [3.3](https://www.opensips.org/Documentation/Configure-File-3-3 "Configuration File - 3.3") [3.2](https://www.opensips.org/Documentation/Configure-File-3-2 "Configuration File - 3.2") [3.1](https://www.opensips.org/Documentation/Configure-File-3-1 "Configuration File - 3.1") [3.0](https://www.opensips.org/Documentation/Configure-File-3-0 "Configuration File - 3.0") [2.4](https://www.opensips.org/Documentation/Configure-File-2-4 "Configuration File - devel") [2.3](https://www.opensips.org/Documentation/Configure-File-2-3 "Configuration File - devel") [2.2](https://www.opensips.org/Documentation/Configure-File-2-2 "Configuration File - 2.2") [2.1](https://www.opensips.org/Documentation/Configure-File-2-1 "Configuration File - devel") [1.11](https://www.opensips.org/Documentation/Configure-File-1-11 "Configuration File - 1.11") [1.10](https://www.opensips.org/Documentation/Configure-File-1-10 "Configuration File - ver 1.10") [1.9](https://www.opensips.org/Documentation/Configure-File-1-9 "Configuration File - ver 1.9") [1.8](https://www.opensips.org/Documentation/Configure-File-1-8 "Configuration File - ver 1.8") [1.7](https://www.opensips.org/Documentation/Configure-File-1-7 "Configuration File - ver 1.7") [1.6](https://www.opensips.org/Documentation/Configure-File-1-6 "Configuration File - ver 1.6") [1.5](https://www.opensips.org/Documentation/Configure-File-1-5 "Configuration File - ver 1.5") [1.4](https://www.opensips.org/Documentation/Configure-File-1-4 "Configuration File - ver 1.4")

**Configuration File v3.6**

* * *

The OpenSIPS configuration file contains all the parameters that control the OpenSIPS core and modules, along with the actual routing logic that OpenSIPS will use to route the SIP traffic.

Upon installation, the default configuration file path is :

\[INSTALL\_PATH\]/etc/opensips/opensips.cfg

The configuration file is text-based, written in an OpenSIPS custom language, very similar to the C language. You will find different variables ( each with different scopes - explained further down the manual ), you can do the classical constructs like if / while / switch, etc, and you can also call sub-routines with parameters, so the script should be fairly easily read-able by somebody with some SIP & programming skills.

If you do any change to the configuration file, in order for them to take effect, you MUST restart OpenSIPS

Due to the fact that you must restart OpenSIPS every time you make a change to the configuration file, it is of vital importance to ensure that all the changes you have made are correct according to the OpenSIPS language syntax.

You can check the OpenSIPS configuration file validity by running

\[INSTALL\_PATH\]/sbin/opensips -C \[PATH\_TO\_CFG\]

When checking the configuration file for validity, If the cfg is OK, OpenSIPS will return 0.

If the config file contains any errors, they will be displayed in the console and OpenSIPS will return -1
