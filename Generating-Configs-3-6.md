Title: openSIPS | Documentation / Generating Config Files

URL Source: https://www.opensips.org/Documentation/Generating-Configs-3-6

Markdown Content:
##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Generating Config Files

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Generating-Configs-3-5 "Generating Config Files - 3.5") [3.4](https://www.opensips.org/Documentation/Generating-Configs-3-4 "Generating Config Files - 3.4") Older versions: [3.3](https://www.opensips.org/Documentation/Generating-Configs-3-3 "Generating Config Files - 3.3") [3.2](https://www.opensips.org/Documentation/Generating-Configs-3-2 "Generating Config Files - 3.2") [3.1](https://www.opensips.org/Documentation/Generating-Configs-3-1 "Generating Config Files - 3.1") [3.0](https://www.opensips.org/Documentation/Generating-Configs-3-0 "Generating Config Files - 3.0") [2.4](https://www.opensips.org/Documentation/Generating-Configs-2-4 "Generating Config Files - devel") [2.3](https://www.opensips.org/Documentation/Generating-Configs-2-3 "Generating Config Files - devel") [2.2](https://www.opensips.org/Documentation/Generating-Configs-2-2 "Generating Config Files - 2.2") [2.1](https://www.opensips.org/Documentation/Generating-Configs-2-1 "Generating Config Files - devel") [1.11](https://www.opensips.org/Documentation/Generating-Configs-1-11 "Generating Config Files - ver 1.11") [1.10](https://www.opensips.org/Documentation/Generating-Configs-1-10 "Generating Config Files - ver 1.10") [1.9](https://www.opensips.org/Documentation/Generating-Configs-1-9 "Generating Config Files - ver 1.9") [1.8](https://www.opensips.org/Documentation/Generating-Configs-1-8 "Generating Config Files - ver 1.8")

**Generating Config Files v3.6**

* * *

Generating OpenSIPS config files is accomplished by using the menuconfig tool. Because the graphical interface is ncurses based, please make sure to first install the ncurses development library ( typically libncurses5-dev ).

### 1.  Using the Menuconfig Tool

The menuconfig can be ran either directly from the OpenSIPS sources, or post installation, from the installation path :

*   From sources, you can run

    make menuconfig

*   After installation, you can run menuconfig directly from the installation path, by running

    \[install\_path\]/sbin/osipsconfig

Once in the menuconfig tool, navigate to the 'Generate OpenSIPS Script' option, and then choose your desired script type. Once you have chosen you script type, you will be able to go to configure the various available options for that script ( described below ). Enabling certain options per script is done by using the spacebar key. Once you have configured your desired options, you can hit the 'q' key to go to the previous menu, and hit 'Save Changes'. Then, you can generate the OpenSIPS script with your configurations. At the end, the graphical tool will give you the path for your newly generated config file ( eg : Config generated : /usr/local/etc/opensips/opensips\_residential\_2013-6-21\_12:39:48.cfg )

### 2.  Types of Configs

So far, the OpenSIPS 3.6 menuconfig automated script generator supports 3 types of scripts. Here are the types of scripts, along with the available options per script :

*   Residential Script
    *   ENABLE\_TCP : OpenSIPS will listen on TCP for SIP requests
    *   ENABLE\_TLS : OpenSIPS will listen on TCP for SIP requests
    *   USE\_ALIASES : OpenSIPS will allow the use of Aliases for SIP users
    *   USE\_AUTH : OpenSIPS will authenticate Register & Invite requests
    *   USE\_DBACC : OpenSIPS will save ACC entries in DB for all calls
    *   USE\_DBUSRLOC : OpenSIPS will persistently store User Location entries in the DB
    *   USE\_DIALOG : OpenSIPS will keep track of active dialogs
    *   USE\_MULTIDOMAIN : OpenSIPS will handle multiple domains for subscribers
    *   USE\_NAT : OpenSIPS will try to cope with NAT by fixing SIP msgs and engaging RTPProxy
    *   USE\_PRESENCE : OpenSIPS will act as a Presence server
    *   USE\_DIALPLAN : OpenSIPS will use dialplan for transformation of local numbers
    *   VM\_DIVERSION : OpenSIPS will redirect to VM calls not reaching the subscribers
    *   HAVE\_INBOUND\_PSTN : OpenSIPS will accept calls from PSTN gateways (with static IP authentication)
    *   HAVE\_OUTBOUND\_PSTN : OpenSIPS will send numerical dials to PSTN gateways (with static IP definition)
    *   USE\_DR\_PSTN : OpenSIPS will use Dynamic Routing Support ( LCR ) for PSTN interconnection
*   Trunking Script
    *   ENABLE\_TCP : OpenSIPS will listen on TCP for SIP requests
    *   ENABLE\_TLS : OpenSIPS will listen on TCP for SIP requests
    *   USE\_DBACC : OpenSIPS will save ACC entries in DB for all calls
    *   USE\_DIALPLAN : OpenSIPS will use dialplan for transformation of local numbers
    *   USE\_DIALOG : OpenSIPS will keep track of active dialogs
    *   DO\_CALL\_LIMITATION : OpenSIPS will limit the number of parallel calls per trunk
*   Load-Balancer Script
    *   ENABLE\_TCP : OpenSIPS will listen on TCP for SIP requests
    *   ENABLE\_TLS : OpenSIPS will listen on TCP for SIP requests
    *   USE\_DBACC : OpenSIPS will save ACC entries in DB for all calls
    *   USE\_DISPATCHER : OpenSIPS will use DISPATCHER instead of Load-Balancer for distributing the traffic
    *   DISABLE\_PINGING : OpenSIPS will not ping at all the destinations (otherwise it will ping when detected as failed)

### 3.  Post-Generation Script editing

After generating your OpenSIPS script with the menuconfig tool, you need to open the script with your favorite editor, and go through all the '# CUSTOMIZE ME' comments in the script. Those comments mark the places where user attention is needed, and usually refer to customizing the OpenSIPS listening address or setting the proper database URL.

Upon making the appropriate '# CUSTOMIZE ME' changes, you can save your script and take it for a test drive.
