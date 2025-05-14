Title: openSIPS | Documentation / Statistics Interface

URL Source: https://www.opensips.org/Documentation/Interface-Statistics-3-6

Markdown Content:
##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Statistics Interface

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Interface-Statistics-3-5 "Statistics Interface - devel") [3.4](https://www.opensips.org/Documentation/Interface-Statistics-3-4 "Statistics Interface - devel") Older versions: [3.3](https://www.opensips.org/Documentation/Interface-Statistics-3-3 "Statistics Interface - devel") [3.2](https://www.opensips.org/Documentation/Interface-Statistics-3-2 "Statistics Interface - devel") [3.1](https://www.opensips.org/Documentation/Interface-Statistics-3-1 "Statistics Interface - devel") [3.0](https://www.opensips.org/Documentation/Interface-Statistics-3-0 "Statistics Interface - devel") [2.4](https://www.opensips.org/Documentation/Interface-Statistics-2-4 "Statistics Interface - devel") [2.3](https://www.opensips.org/Documentation/Interface-Statistics-2-3 "Statistics Interface - devel") [2.2](https://www.opensips.org/Documentation/Interface-Statistics-2-2 "Statistics Interface - 2.2") [2.1](https://www.opensips.org/Documentation/Interface-Statistics-2-1 "Statistics Interface - devel") [1.11](https://www.opensips.org/Documentation/Interface-Statistics-1-11 "Statistics Interface - 1.11") [1.10](https://www.opensips.org/Documentation/Interface-Statistics-1-10 "Statistics Interface - ver 1.10") [1.9](https://www.opensips.org/Documentation/Interface-Statistics-1-9 "Statistics Interface - ver 1.9") [1.8](https://www.opensips.org/Documentation/Interface-Statistics-1-8 "Statistics Interface - ver 1.8") [1.7](https://www.opensips.org/Documentation/Interface-Statistics-1-7 "Statistics Interface - ver 1.7") [1.6](https://www.opensips.org/Documentation/Interface-Statistics-1-6 "Statistics Interface - ver 1.6") [1.5](https://www.opensips.org/Documentation/Interface-Statistics-1-5 "Statistics Interface - ver 1.5") [1.4](https://www.opensips.org/Documentation/Interface-Statistics-1-4 "Statistics Interface - ver 1.4")

**Statistics Interface v3.6**

* * *

The **Statistics Interface** is an OpenSIPS interface that provides access to various internal statistics of OpenSIPS. The statistic provide useful information about what is going on inside OpenSIPS - this can be used by external applications, for monitoring purposes, load evaluation, realtime integration with other services. The values of statistic variables are exclusively numerical.

* * *

#### Overview

**OpenSIPS** typically provides two types of statistic variables:

1.  counter like - variables that keep counting things that happened in OpenSIPS, like received requests, processed dialogs, failed DB queries, etc
2.  computed values - variables that are calculated in realtime, like how much memory is used, the current load, active dialogs, active transactions, etc

The statistic variables are not restart persistent, they all start with a 0 value (the counter like variables). The _counter like_ statistics can also be reset (to 0 value) during OpenSIPS runtime.

In OpenSIPS, the statistics variables are grouped in different sets, depending on their purposes or how is providing them. For example, the OpenSIPS core provides the **shmem**, **load**, **net**, etc groups, while each OpenSIPS module provides its own group (typically the group has the same name as the module).

All available statistic variables are listed and documented : statistics provided [by OpenSIPS core](https://www.opensips.org/Documentation/Interface-CoreStatistics-3-6 "Core Statistics - 3.6") or by [OpenSIPS modules](https://www.opensips.org/Documentation/Modules-3-6 "Modules - 3.6") (see the Statistics chapter for each module).

* * *

#### Usage

To get access to the statistics you have to use the [MI interface](https://www.opensips.org/Documentation/Interface-MI-3-6 "Management Interface - 3.6") which provides (directly from OpenSIPS core) several MI functions for:

**Fetching the value** of a statistic variable, of an entire group of variables or of all variables. The MI [get\_statistics](https://www.opensips.org/Documentation/Interface-CoreMI-3-6 "Core MI Functions - 3.6") command can be used here:

   # get one statistic variable, by name
   \> opensipsctl fifo get\_statistics rcv\_requests
   \> core:rcv\_requests = 3428
   \> opensipsctl fifo get\_statistics real\_used\_size 
   \> shmem:real\_used\_size = 2951864

   # get various statistic variables, by list of names
   \> opensipsctl fifo get\_statistics rcv\_requests inuse\_transactions
   \> core:rcv\_requests = 453
   \> tm:inuse\_transactions = 10


   # get all stats from a group
   \> opensipsctl fifo get\_statistics shmem:
   \> shmem:total\_size = 33554432
   \> shmem:used\_size = 2897024
   \> shmem:real\_used\_size = 2951864
   \> shmem:max\_used\_size = 2952304
   \> shmem:free\_size = 30602568
   \> shmem:fragments = 26

   # get all stats from OpenSIPS
   \> opensipsctl fifo get\_statistics all
   \>...........

**Reseting the value** of a statistic variable (to 0 value), but only if it is counter-type variable.

Reseting a computed-value statistic will be ignored and have no effect.

 The MI [reset\_statistics](https://www.opensips.org/Documentation/Interface-CoreMI-3-6 "Core MI Functions - 3.6") command can be used here:

   # reset one statistic variable, by name
   \> opensipsctl fifo reset\_statistics rcv\_requests
