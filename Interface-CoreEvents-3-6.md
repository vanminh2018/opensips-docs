Title: openSIPS | Documentation / Core Events

URL Source: https://www.opensips.org/Documentation/Interface-CoreEvents-3-6

Markdown Content:
##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Core Events

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Interface-CoreEvents-3-5 "Core Events - 3.5") [3.4](https://www.opensips.org/Documentation/Interface-CoreEvents-3-4 "Core Events - 3.4") Older versions: [3.3](https://www.opensips.org/Documentation/Interface-CoreEvents-3-3 "Core Events - 3.3") [3.2](https://www.opensips.org/Documentation/Interface-CoreEvents-3-2 "Core Events - 3.2") [3.1](https://www.opensips.org/Documentation/Interface-CoreEvents-3-1 "Core Events - 3.1") [3.0](https://www.opensips.org/Documentation/Interface-CoreEvents-3-0 "Core Events - 3.0") [2.4](https://www.opensips.org/Documentation/Interface-CoreEvents-2-4 "Core Events - 2.4") [2.3](https://www.opensips.org/Documentation/Interface-CoreEvents-2-3 "Core Events - devel") [2.2](https://www.opensips.org/Documentation/Interface-CoreEvents-2-2 "Core Events - 2.2") [2.1](https://www.opensips.org/Documentation/Interface-CoreEvents-2-1 "Core Events - devel") [1.11](https://www.opensips.org/Documentation/Interface-CoreEvents-1-11 "Core Events - 1.11") [1.10](https://www.opensips.org/Documentation/Interface-CoreEvents-1-10 "Core Events - ver 1.10") [1.9](https://www.opensips.org/Documentation/Interface-CoreEvents-1-9 "Core Events - ver 1.9") [1.8](https://www.opensips.org/Documentation/Interface-CoreEvents-1-8 "Core Events - ver 1.8") [1.7](https://www.opensips.org/Documentation/Interface-CoreEvents-1-7 "Core Events - ver 1.7")

**Core Events v3.6**

* * *

**Table of Content** (hide)

1.  1. [Threshold limit exceeded](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#toc1)
2.  2. [Private memory threshold exceeded](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#toc2)
3.  3. [Shared memory threshold exceeded](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#toc3)
4.  4. [Process Auto-Scaling (upscale and downscale)](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#toc4)
5.  5. [TCP connection disconnected](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#toc5)
6.  6. [Status/Report status changed](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#toc6)
7.  7. [Log message produced](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#toc7)

Events are exported by the **OpenSIPS** core through the Event Interface.

* * *

### 1.  Threshold limit exceeded [🔗](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#E_CORE_THRESHOLD)

**Event**: E\_CORE\_THRESHOLD

This event is triggered when a particular action takes longer than a specific threshold. It can be raised when a MySQL or DNS query takes too long, or a SIP message processing goes beyond a specific limit. For more information please see [this](http://lists.opensips.org/pipermail/users/2011-February/016918.html) post.

Parameters:

*   **source**: the source of the event: mysql module, core (for DNS or message processing warnings).
*   **time**: the amount of time (in microseconds) spent by the operation
*   **extra**: extra information, depending on the source of the event

### 2.  Private memory threshold exceeded [🔗](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#E_CORE_PKG_THRESHOLD)

**Event**: E\_CORE\_PKG\_THRESHOLD

This event is triggered when the private memory usage goes above a threshold limit, specified by the **event\_pkg\_threshold** the core parameter. It warns external applications about low values of free private memory.

Parameters:

*   **usage**: the percentage of private memory usage. Can have values between **event\_pkg\_threshold** and 100.
*   **threshold**: the **event\_pkg\_threshold** specified in the script.
*   **used**: the amount of private memory used.
*   **size**: the total amount of private memory.
*   **pid**: the pid of the process that raises the event.

Note: If the **event\_pkg\_threshold** is not specified or 0, then this event is disabled.

### 3.  Shared memory threshold exceeded [🔗](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#E_CORE_SHM_THRESHOLD)

**Event**: E\_CORE\_SHM\_THRESHOLD

This event is triggered when the shared memory usage goes above a threshold limit, specified by the **event\_shm\_threshold** the core parameter. It warns external applications about low values of free shared memory.

Parameters:

*   **usage**: the percentage of private memory usage. Can have values between **event\_shm\_threshold** and 100.
*   **threshold**: the **event\_shm\_threshold** specified in the script.
*   **used**: the amount of private memory used.
*   **size**: the total amount of private memory.

Note: If the **event\_shm\_threshold** is not specified or 0, then this event is disabled.

### 4.  Process Auto-Scaling (upscale and downscale) [🔗](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#E_CORE_PROC_AUTO_SCALE)

**Event**: E\_CORE\_PROC\_AUTO\_SCALE

This event is triggered whenever a new process is created (forked) or a process is terminated due the auto-scaling logic. In order to have this event trigger, the [auto-scaling](https://www.opensips.org/Documentation/Script-CoreParameters-3-6#auto_scaling_profile) must be enabled in your configuration.

Parameters:

*   **group\_type**: the type/name of the scaling group (UDP/TCP/TIMER).
*   **group\_filter**: the filter (usually the socket/interface for UDP) of the scaling group.
*   **group\_load**: the load over the scaling group.
*   **scale**: "up" or "down"
*   **process\_id**: the process ID (at OpenSIPS level) of the scaled (up or down) process.
*   **pid**: the PID (OS level) of the scaled (up or down) process.

### 5.  TCP connection disconnected [🔗](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#E_CORE_TCP_DISCONNECT)

**Event**: E\_CORE\_TCP\_DISCONNECT

This event is triggered when a TCP connection is terminated/disconnected.

Parameters:

*   **src\_ip**: the source IP of the TCP connection
*   **src\_port**: the source PORT of the TCP connection
*   **dst\_ip**: the destination IP of the TCP connection
*   **dst\_port**: the destination PORT of the TCP connection
*   **proto**: the protocol of the underlying TCP connection ( ie. tcp, tls, ws, wss, etc )

### 6.  Status/Report status changed [🔗](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#E_CORE_SR_STATUS_CHANGED)

**Event**: E\_CORE\_SR\_STATUS\_CHANGED

This event is triggered the status of an SR identifier changes.

Parameters:

*   **group**: the name of the SR group
*   **identifier**: the name of the SR identifier
*   **status**: the new status (as numerical value) of the SR identifier
*   **details**: the details/text attached to the new status
*   **old\_status**: the old status (as numerical value) of the SR identifier

### 7.  Log message produced [🔗](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6#E_CORE_LOG)

**Event**: E\_CORE\_LOG

This event is triggered whenever a log message is produced by OpenSIPS. In order to have this event trigger, the [log\_event\_enabled](https://www.opensips.org/Documentation/Script-CoreParameters-3-4#log_event_enabled) must be enabled in your configuration.

Parameters:

*   **time**: time when the log message was produced
*   **pid**: the PID of the processes that produced this log message
*   **level**: the log level of this message ("DBG", "INFO" etc.)
*   **module**: module that produced this log message; NULL for logs triggered from the script by the **xlog()** function
*   **function**: internal function that produced this log message; NULL for logs triggered from the script by the **xlog()** function
*   **prefix**: logging prefix, configured via the [log\_prefix](https://www.opensips.org/Documentation/Script-CoreParameters-3-4#log_prefix) parameter. It is an empty string if the parameter is not configured.
*   **message**: the actual log message content

* * *
