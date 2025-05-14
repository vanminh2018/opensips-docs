Title: openSIPS | Documentation / Events Interface

URL Source: https://www.opensips.org/Documentation/Interface-Events-3-6

Markdown Content:
##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Events Interface

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Interface-Events-3-5 "Events Interface - 3.5") [3.4](https://www.opensips.org/Documentation/Interface-Events-3-4 "Events Interface - 3.4") Older versions: [3.3](https://www.opensips.org/Documentation/Interface-Events-3-3 "Events Interface - 3.3") [3.2](https://www.opensips.org/Documentation/Interface-Events-3-2 "Events Interface - 3.2") [3.1](https://www.opensips.org/Documentation/Interface-Events-3-1 "Events Interface - 3.1") [3.0](https://www.opensips.org/Documentation/Interface-Events-3-0 "Events Interface - devel") [2.4](https://www.opensips.org/Documentation/Interface-Events-2-4 "Events Interface - devel") [2.3](https://www.opensips.org/Documentation/Interface-Events-2-3 "Events Interface - devel") [2.2](https://www.opensips.org/Documentation/Interface-Events-2-2 "Events Interface - 2.2") [2.1](https://www.opensips.org/Documentation/Interface-Events-2-1 "Events Interface - 2.1") [1.11](https://www.opensips.org/Documentation/Interface-Events-1-11 "Events Interface - 1.11") [1.10](https://www.opensips.org/Documentation/Interface-Events-1-10 "Events Interface - ver 1.10") [1.9](https://www.opensips.org/Documentation/Interface-Events-1-9 "Events Interface - ver 1.9") [1.8](https://www.opensips.org/Documentation/Interface-Events-1-8 "Events Interface - ver 1.8") [1.7](https://www.opensips.org/Documentation/Interface-Events-1-7 "Events Interface - ver 1.7")

**Events Interface v3.6**

* * *

The **Events Interface** is an OpenSIPS interface that provides different ways to notify external applications about certain events triggered inside OpenSIPS.

#### Overview

In order to notify an external application about OpenSIPS internal events, the **Event Interface** provides the following functions:

1.  manages exported events
2.  manages subscriptions from different applications
3.  exports generic functions to raise an event (regardless the transport protocol used)
4.  communicates with different transport protocols to send the events

More detailed information about **OpenSIPS Event Interface** can be found in the [Event Interface Tutorial](https://www.opensips.org/Documentation/Tutorials-EventInterface "Tutorials-EventInterface").

* * *

#### Events

There are several types of events that can be exported by OpenSIPS:

*   **Core events** - internal events that trigger changes of OpenSIPS core/global behavior. A full list of exported core events can be found [here](https://www.opensips.org/Documentation/Interface-CoreEvents-3-6 "Core Events - 3.6").
*   **Modules events** - events triggered by each module, when loaded. Each module can export zero, one or more events. Details can be found in the [documentation page](https://www.opensips.org/Documentation/Modules-3-6 "Modules - 3.6") of each module.
*   **Custom events** - triggered from script using the [raise\_event()](https://www.opensips.org/Documentation/Script-CoreFunctions-3-6#raise_event "Core Functions - 3.6") command.

* * *

#### Transport Protocols

External applications can be notified about the events triggered using various transport protocols. While the interface itself is provided by OpenSIPS core, each transport protocol is implemented by a separate OpenSIPS module. Multiple transport modules can be loaded simultaneously in order to provide different ways of notifications.

Available transport protocols are :

*   [event\_datagram](http://www.opensips.org/html/docs/modules/3.6.x/event_datagram) - sends Datagrams over UDP or UNIX sockets
*   [event\_flastore](http://www.opensips.org/html/docs/modules/3.6.x/event_flatstore) - writes to plain text files
*   [event\_kafka](http://www.opensips.org/html/docs/modules/3.6.x/event_kafka) - sends events via Apache Kafka broker
*   [event\_rabbitmq](http://www.opensips.org/html/docs/modules/3.6.x/event_rabbitmq) - sends an AMQP message to a RabbitMQ server
*   [event\_route](http://www.opensips.org/html/docs/modules/3.6.x/event_route) - runs an OpenSIPS event\_route in script
*   [event\_stream](http://www.opensips.org/html/docs/modules/3.6.x/event_stream) - sends a JSON-RPC command/notification over TCP
*   [event\_virtual](http://www.opensips.org/html/docs/modules/3.6.x/event_virtual) - aggregates event backends for failover and balancing
*   [event\_xmlrpc](http://www.opensips.org/html/docs/modules/3.6.x/event_xmlrpc) - sends a XML-RPC command over TCP

An external application can subscribe to any of the exported module and can be notified using any of the loaded transport modules/protocols.

* * *

#### Events Subscription

You can subscribe for an event either at startup (using the [subscribe\_event()](https://www.opensips.org/Documentation/Script-CoreFunctions-3-6#subscribe_event "Core Functions - 3.6") command in the script) or during runtime, using the [event\_subscribe](https://www.opensips.org/Documentation/Interface-CoreMI-3-6#event_subscribe "Core MI Functions - 3.6") MI command.

* * *

#### Examples

In order to configure a RabbbitMQ server to be notified when a custom event is triggered, first you have to subscribe it to the event, using the [subscribe\_event()](https://www.opensips.org/Documentation/Script-CoreFunctions-3-6#subscribe_event "Core Functions - 3.6") command:

    startup\_route {
        subscribe\_event("E\_SCRIPT\_CUSTOM\_EVENT", "rabbitmq:127.0.0.1/opensips");
    }

Then, in order to trigger the event from the script, call the [raise\_event()](https://www.opensips.org/Documentation/Script-CoreFunctions-3-6#raise_event "Core Functions - 3.6") command when needed:

   ....
   raise\_event("E\_SCRIPT\_CUSTOM\_EVENT");     # raises an event without any parameters
   ...
