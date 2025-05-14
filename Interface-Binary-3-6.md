Title: openSIPS | Documentation / Binary Internal Interface

URL Source: https://www.opensips.org/Documentation/Interface-Binary-3-6

Markdown Content:
##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Binary Internal Interface

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Interface-Binary-3-5 "Binary Internal Interface - 3.5") [3.4](https://www.opensips.org/Documentation/Interface-Binary-3-4 "Binary Internal Interface - 3.4") Older versions: [3.3](https://www.opensips.org/Documentation/Interface-Binary-3-3 "Binary Internal Interface - 3.3") [3.2](https://www.opensips.org/Documentation/Interface-Binary-3-2 "Binary Internal Interface - 3.2") [3.1](https://www.opensips.org/Documentation/Interface-Binary-3-1 "Binary Internal Interface - 3.1") [3.0](https://www.opensips.org/Documentation/Interface-Binary-3-0 "Binary Internal Interface - 3.0") [2.4](https://www.opensips.org/Documentation/Interface-Binary-2-4 "Binary Internal Interface - 2.4") [2.3](https://www.opensips.org/Documentation/Interface-Binary-2-3 "Binary Internal Interface - 2.3") [2.2](https://www.opensips.org/Documentation/Interface-Binary-2-2 "Binary Internal Interface - 2.2") [2.1](https://www.opensips.org/Documentation/Interface-Binary-2-1 "Binary Internal Interface - devel") [1.11](https://www.opensips.org/Documentation/Interface-Binary-1-11 "Binary Internal Interface - 1.11") [1.10](https://www.opensips.org/Documentation/Interface-Binary-1-10 "Binary Internal Interface - ver 1.10")

**Binary Internal Interface v3.6**

* * *

The **Binary Internal Interface** is an OpenSIPS core interface which offers an efficient way for communication between individual OpenSIPS instances. This is especially useful in scenarios where realtime data (such as dialogs) cannot be simply stored in a database anymore, because failover would require entire minutes to complete. This issue can be solved with the new internal binary interface by replicating all the events related to the runtime data (creation / updating / deletion) to a backup OpenSIPS instance.

* * *

#### Configuring the Binary Internal Interface listeners

In order to listen for incoming Binary Packets, a **bin:** interface must be specified. Its number of listener processes can be tuned with _[tcp\_workers](https://opensips.org/Documentation/Script-CoreParameters-3-6#tcp_workers)_ core parameter.

   listen = bin:10.0.0.150:5062
   ...
   loadmodule "proto\_bin.so"

Examples of cluster-enabled modules which use the binary interface are **dialog** and **usrloc**, as they can now replicate all run-time events (creation/updating/deletion of dialogs/contacts) to one or more OpenSIPS instances. Configuration can be done as follows:

   modparam("dialog", "dialog\_replication\_cluster", 1)
   modparam("dialog", "profile\_replication\_cluster", 2)
   ...
   modparam("usrloc", "location\_cluster", 2)

More details can be found in the [dialog](https://www.opensips.org/html/docs/modules/3.6.x/dialog#dialog-clustering) and [usrloc](https://www.opensips.org/html/docs/modules/3.6.x/usrloc#distributed-sip-user-location) documentation pages.

* * *

#### C Interface Overview (for module developers)

The interface allows the module writer to build and send compact **Binary Packets** in an intuitive way.

In order to **send packets**, the interface provides the following primitives:

*   _int bin\_init(str \*mod\_name, int packet\_type)_ - begins the construction of a new Binary Packet
*   _int bin\_push\_str(const str \*info)_ - add a string to the Binary Packet that is currently being built
*   _int bin\_push\_int(int info)_ - add an integer to the Binary Packet that is currently being built
*   _int bin\_send(union sockaddr\_union \*de_[tcp\_workers](https://opensips.org/Documentation/Script-CoreParameters-3-6#tcp_workers) _core parameter.st)_ - sends the Binary Packet to a given destination over UDP

In order to **receive packets**, a module must first register a callback function to the interface:

*   _int bin\_register\_cb(char \*mod\_name, void (\*)(int packet\_type))_

Each time this callback is triggered, the information can be retrieved in the same order it was written using:

*   _int bin\_pop\_str(str \*info)_ - retrieve a string from a received Binary Packet
*   _int bin\_pop\_int(void \*info)_ - retrieve an integer from a received Binary Packet
