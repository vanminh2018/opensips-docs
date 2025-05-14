Title: openSIPS | Documentation / DB schema

URL Source: https://www.opensips.org/Documentation/Install-DBSchema-3-6

Markdown Content:
Login | Register



 
About Downloads Documentation Community Development Training

Documentation

Manuals
Advanced Tutorials
Tips & FAQ
Version Migration
OpenSIPS Webinars
Troubleshooting
OpenSIPS Tools
Devel Tutorial
	
Documentation -> Manuals -> Manual devel -> DB schema

Pages for other versions: devel 3.5 3.4 Older versions: 3.3 3.2 3.1 3.0 2.4 2.3 2.2 2.1 1.11 1.10 1.9 1.8 1.7 1.6 1.5 1.4




DB Schema v3.6
Prev	Next





OpenSIPS database tables
OpenSIPS Development Team
https://opensips.org/


Copyright © 2007-2020 OpenSIPS development Team

Table of Contents
1. Accounting
2. alias db
3. Subscriber
4. JWT authentication
5. B2BUA
6. SCA support
7. CacheDB_SQL
8. Call Center
9. carrierroute
10. Accounting
11. Clusterer support
12. Call-processing language
13. Dialog support
14. Matching and translation rules
15. Dispatcher
16. Domain
17. Domainpolicy
18. Dynamic Routing
19. Emergency
20. Fraud Detection
21. FreeSWITCH ESL Integration
22. Group checking
23. Instant Message Conference
24. JANUS
25. Load Balancer
26. Message Storage
27. Permissions
28. Presence
29. Quality Routing
30. Rate Cacher
31. Registrant support
32. RLS
33. RTPengine
34. RTPProxy
35. SMPP
36. SOCKETS_MGM support
37. Speed dial
38. SQL Operations
39. Version
40. TCP_MGM support
41. TLS_MGM support
42. Tracer
43. Trie
44. User and global blacklists
45. User location
List of Tables
1-1. Table "acc"
1-2. Table "acc" indexes
1-3. Table "missed_calls"
1-4. Table "missed_calls" indexes
2-1. Table "dbaliases"
2-2. Table "dbaliases" indexes
3-1. Table "subscriber"
3-2. Table "subscriber" indexes
3-3. Table "uri"
3-4. Table "uri" indexes
4-1. Table "jwt_profiles"
4-2. Table "jwt_profiles" indexes
4-3. Table "jwt_secrets"
5-1. Table "b2b_entities"
5-2. Table "b2b_entities" indexes
5-3. Table "b2b_logic"
5-4. Table "b2b_logic" indexes
6-1. Table "b2b_sca"
6-2. Table "b2b_sca" indexes
7-1. Table "cachedb"
7-2. Table "cachedb" indexes
8-1. Table "cc_flows"
8-2. Table "cc_flows" indexes
8-3. Table "cc_agents"
8-4. Table "cc_agents" indexes
8-5. Table "cc_cdrs"
8-6. Table "cc_calls"
8-7. Table "cc_calls" indexes
9-1. Table "carrierroute"
9-2. Table "carrierfailureroute"
9-3. Table "route_tree"
10-1. Table "closeddial"
10-2. Table "closeddial" indexes
11-1. Table "clusterer"
11-2. Table "clusterer" indexes
12-1. Table "cpl"
12-2. Table "cpl" indexes
13-1. Table "dialog"
14-1. Table "dialplan"
15-1. Table "dispatcher"
16-1. Table "domain"
16-2. Table "domain" indexes
17-1. Table "domainpolicy"
17-2. Table "domainpolicy" indexes
18-1. Table "dr_gateways"
18-2. Table "dr_gateways" indexes
18-3. Table "dr_rules"
18-4. Table "dr_carriers"
18-5. Table "dr_carriers" indexes
18-6. Table "dr_groups"
18-7. Table "dr_partitions"
19-1. Table "emergency_routing"
19-2. Table "emergency_report"
19-3. Table "emergency_service_provider"
20-1. Table "fraud_detection"
21-1. Table "freeswitch"
22-1. Table "grp"
22-2. Table "grp" indexes
22-3. Table "re_grp"
22-4. Table "re_grp" indexes
23-1. Table "imc_rooms"
23-2. Table "imc_rooms" indexes
23-3. Table "imc_members"
23-4. Table "imc_members" indexes
24-1. Table "janus"
25-1. Table "load_balancer"
25-2. Table "load_balancer" indexes
26-1. Table "silo"
26-2. Table "silo" indexes
27-1. Table "address"
28-1. Table "presentity"
28-2. Table "presentity" indexes
28-3. Table "active_watchers"
28-4. Table "active_watchers" indexes
28-5. Table "watchers"
28-6. Table "watchers" indexes
28-7. Table "xcap"
28-8. Table "xcap" indexes
28-9. Table "pua"
28-10. Table "pua" indexes
29-1. Table "qr_profiles"
30-1. Table "rc_clients"
30-2. Table "rc_clients" indexes
30-3. Table "rc_vendors"
30-4. Table "rc_vendors" indexes
30-5. Table "rc_ratesheets"
30-6. Table "rc_ratesheets" indexes
30-7. Table "rc_demo_ratesheet"
30-8. Table "rc_demo_ratesheet" indexes
31-1. Table "registrant"
31-2. Table "registrant" indexes
32-1. Table "rls_presentity"
32-2. Table "rls_presentity" indexes
32-3. Table "rls_watchers"
32-4. Table "rls_watchers" indexes
33-1. Table "rtpengine"
34-1. Table "rtpproxy_sockets"
35-1. Table "smpp"
35-2. Table "smpp" indexes
36-1. Table "sockets"
37-1. Table "speed_dial"
37-2. Table "speed_dial" indexes
38-1. Table "usr_preferences"
38-2. Table "usr_preferences" indexes
39-1. Table "version"
39-2. Table "version" indexes
40-1. Table "tcp_mgm"
41-1. Table "tls_mgm"
41-2. Table "tls_mgm" indexes
42-1. Table "sip_trace"
42-2. Table "sip_trace" indexes
43-1. Table "trie_table"
43-2. Table "dr_partitions"
44-1. Table "userblacklist"
44-2. Table "userblacklist" indexes
44-3. Table "globalblacklist"
44-4. Table "globalblacklist" indexes
45-1. Table "location"
Chapter 1. Accounting

    

acc

This table is used by the ACC module to report on transactions - accounted calls. More information is available at: https://opensips.org/docs/modules/devel/acc.html
		

missed_calls

This table is used by the ACC module for keeping track of missed calls. This table is similar to the 'acc' table. More information is available at: https://opensips.org/docs/modules/devel/acc.html


  

    

Table 1-1. Table "acc"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              method
            	              string
            	              16
            	''	no	 	 	              

A method is the primary function that a request is meant to invoke on a server.


            
              from_tag
            	              string
            	              64
            	''	no	 	 	              

The tag parameter serves as a general mechanism to identify a dialog, which is the combination of the Call-ID along with two tags, one from participant in the dialog.


            
              to_tag
            	              string
            	              64
            	''	no	 	 	              

The tag parameter serves as a general mechanism to identify a dialog, which is the combination of the Call-ID along with two tags, one from participant in the dialog.


            
              callid
            	              string
            	              64
            	''	no	 	 	              

Call-ID header field uniquely identifies a particular invitation or all registrations of a particular client. 


            
              sip_code
            	              string
            	              3
            	''	no	 	 	              

SIP reply code


            
              sip_reason
            	              string
            	              32
            	''	no	 	 	              

SIP reply reason


            
              time
            	              datetime
            	              not specified
            	default	no	 	 	              

Date and time when this record was written.


            
              duration
            	              unsigned int
            	              11
            	0	no	 	 	              

Call duration (from 200OK INVITE to BYE request) in seconds - this field is populated only if CDR support is enabled in ACC module (see cdr_flag parameter)


            
              ms_duration
            	              unsigned int
            	              11
            	0	no	 	 	              

Call duration (from 200OK INVITE to BYE request) in milliseconds - this field is populated only if CDR support is enabled in ACC module (see cdr_flag parameter)


            
              setuptime
            	              unsigned int
            	              11
            	0	no	 	 	              

Call initialization duration - (from INVITE request to 200 OK INVITE) - this filed is populated only if CDR support is enabled in ACC module (see cdr_flag parameter)


            
              created
            	              datetime
            	              not specified
            	NULL	yes	 	 	              

The call creation date and time.


            

    

Table 1-2. Table "acc" indexes

name	type	links	description
              callid_idx
            	default	callid	              

 


            

    

Table 1-3. Table "missed_calls"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              method
            	              string
            	              16
            	''	no	 	 	              

A method is the primary function that a request is meant to invoke on a server.


            
              from_tag
            	              string
            	              64
            	''	no	 	 	              

The tag parameter serves as a general mechanism to identify a dialog, which is the combination of the Call-ID along with two tags, one from participant in the dialog.


            
              to_tag
            	              string
            	              64
            	''	no	 	 	              

The tag parameter serves as a general mechanism to identify a dialog, which is the combination of the Call-ID along with two tags, one from participant in the dialog.


            
              callid
            	              string
            	              64
            	''	no	 	 	              

Call-ID header field uniquely identifies a particular invitation or all registrations of a particular client. 


            
              sip_code
            	              string
            	              3
            	''	no	 	 	              

SIP reply code


            
              sip_reason
            	              string
            	              32
            	''	no	 	 	              

SIP reply reason


            
              time
            	              datetime
            	              not specified
            	default	no	 	 	              

Date and time when this record was written.


            
              setuptime
            	              unsigned int
            	              11
            	0	no	 	 	              

Call initialization duration - (from INVITE request to reply) - this filed is populated only if CDR support is enabled in ACC module (see cdr_flag parameter)


            
              created
            	              datetime
            	              not specified
            	NULL	yes	 	 	              

The call creation date and time.


            

    

Table 1-4. Table "missed_calls" indexes

name	type	links	description
              callid_idx
            	default	callid	              

 


            

  

Chapter 2. alias db

    

dbaliases

This table us used by the alias_db module as an alternative for user aliases via userloc. More information about the alias_db module can be found at: https://opensips.org/docs/modules/devel/alias_db.html
        


  

    

Table 2-1. Table "dbaliases"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              alias_username
            	              string
            	              64
            	''	no	 	 	              

Alias username / phone number


            
              alias_domain
            	              string
            	              64
            	''	no	 	 	              

Alias domain name


            
              username
            	              string
            	              64
            	''	no	 	 	              

Username / phone number


            
              domain
            	              string
            	              64
            	''	no	 	 	              

Domain name


            

    

Table 2-2. Table "dbaliases" indexes

name	type	links	description
              alias_idx
            	unique	alias_username, alias_domain	              

 


            
              target_idx
            	default	username, domain	              

 


            

  

Chapter 3. Subscriber

    

subscriber

This table is used to provide authentication information. More information about the auth_db module can be found at: https://opensips.org/docs/modules/devel/auth_db.html
        

uri

This table is used by uri_db module to implement various SIP URI checks.
                 More information about the uri_db module can be found at: https://opensips.org/docs/modules/devel/uri_db.html 
        


  

    

Table 3-1. Table "subscriber"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              username
            	              string
            	              64
            	''	no	 	 	              

Username / phone number


            
              domain
            	              string
            	              64
            	''	no	 	 	              

Domain name


            
              password
            	              string
            	              25
            	''	no	 	 	              

Password


            
              ha1
            	              string
            	              64
            	''	no	 	 	              

md5(username:realm:password)


            
              ha1_sha256
            	              string
            	              64
            	''	no	 	 	              

sha256(username:realm:password)


            
              ha1_sha512t256
            	              string
            	              64
            	''	no	 	 	              

sha512t256(username:realm:password)


            

    

Table 3-2. Table "subscriber" indexes

name	type	links	description
              account_idx
            	unique	username, domain	              

 


            
              username_idx
            	default	username	              

 


            

    

Table 3-3. Table "uri"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

 


            
              username
            	              string
            	              64
            	''	no	 	 	              

Username / phone number


            
              domain
            	              string
            	              64
            	''	no	 	 	              

Domain name


            
              uri_user
            	              string
            	              64
            	''	no	 	 	              

Username / phone number


            
              last_modified
            	              datetime
            	              not specified
            	'1900-01-01 00:00:01'	no	 	 	              

Date and time when this record was last modified.


            

    

Table 3-4. Table "uri" indexes

name	type	links	description
              account_idx
            	unique	username, domain, uri_user	              

 


            

  

Chapter 4. JWT authentication

    

jwt_profiles

This table is used by the AUTH_JWT module to read the actual JWT profiles info
		More information can be found at: https://opensips.org/docs/modules/devel/auth_jwt.html.
		

jwt_secrets

This table is used by the AUTH_JWT module to read the actual JWT secrets which are used for authentication
		More information can be found at: https://opensips.org/docs/modules/devel/auth_jwt.html.
		


  

    

Table 4-1. Table "jwt_profiles"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Table key, not used by module


            
              tag
            	              string
            	              128
            	default	no	 	 	              

Unique ID of the JWT profile


            
              sip_username
            	              string
            	              128
            	default	no	 	 	              

The SIP username associated with the JWT profile
		


            

    

Table 4-2. Table "jwt_profiles" indexes

name	type	links	description
              jwt_tag_idx
            	unique	tag	              

 


            

    

Table 4-3. Table "jwt_secrets"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Table key, not used by module


            
              corresponding_tag
            	              string
            	              128
            	default	no	 	 	              

JWT profile tag which this secret belongs to


            
              secret
            	              text
            	              not specified
            	default	no	 	 	              

The KEY used for signing the JWT
		


            
              start_ts
            	              int
            	              not specified
            	default	no	 	 	              

UNIX TS for the START period on which the JWT secret is valid
		


            
              end_ts
            	              int
            	              not specified
            	default	no	 	 	              

UNIX TS for the END period on which the JWT secret is valid
		


            

  

Chapter 5. B2BUA

    

b2b_entities

Table for the b2b_entities module. More information can be found at: https://opensips.org/docs/modules/devel/b2b_entities.html
        

b2b_logic

Table for the b2b_logic module. More information can be found at: https://opensips.org/docs/modules/devel/b2b_logic.html
        


  

    

Table 5-1. Table "b2b_entities"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              type
            	              int
            	              2
            	default	no	 	 	              

Entity type: 0-server, 1-client


            
              state
            	              int
            	              2
            	default	no	 	 	              

Dialog state


            
              ruri
            	              string
            	              255
            	default	yes	 	 	              

RURI(stored only for server entities to correctly match CANCEL)


            
              from_uri
            	              string
            	              255
            	default	no	 	 	              

From URI


            
              to_uri
            	              string
            	              255
            	default	no	 	 	              

To URI


            
              from_dname
            	              string
            	              64
            	default	yes	 	 	              

From display name


            
              to_dname
            	              string
            	              64
            	default	yes	 	 	              

To display name


            
              tag0
            	              string
            	              64
            	default	no	 	 	              

TO tag


            
              tag1
            	              string
            	              64
            	default	yes	 	 	              

From tag


            
              callid
            	              string
            	              128
            	default	no	 	 	              

Call ID


            
              cseq0
            	              int
            	              11
            	default	no	 	 	              

Cseq0


            
              cseq1
            	              int
            	              11
            	default	yes	 	 	              

Cseq1


            
              contact0
            	              string
            	              255
            	default	no	 	 	              

Contact0


            
              contact1
            	              string
            	              255
            	default	yes	 	 	              

Contact1


            
              route0
            	              text
            	              not specified
            	default	yes	 	 	              

Record route 0


            
              route1
            	              text
            	              not specified
            	default	yes	 	 	              

Record route 1


            
              sockinfo_srv
            	              string
            	              64
            	default	yes	 	 	              

Socket Info


            
              param
            	              string
            	              255
            	default	no	 	 	              

Logic parameter


            
              mod_name
            	              string
            	              32
            	default	no	 	 	              

OpenSIPS module that this entity belongs to


            
              storage
            	              binary
            	              4096
            	NULL	yes	 	 	              

Generic binary data storage


            
              lm
            	              int
            	              11
            	default	no	 	 	              

Last method


            
              lrc
            	              int
            	              11
            	default	yes	 	 	              

Last reply code


            
              lic
            	              int
            	              11
            	default	yes	 	 	              

Last invite cseq


            
              leg_cseq
            	              int
            	              11
            	default	yes	 	 	              

Leg cseq


            
              leg_route
            	              text
            	              not specified
            	default	yes	 	 	              

Leg route


            
              leg_tag
            	              string
            	              64
            	default	yes	 	 	              

Leg tag


            
              leg_contact
            	              string
            	              255
            	default	yes	 	 	              

Leg contact


            
              leg_sockinfo
            	              string
            	              255
            	default	yes	 	 	              

Leg sockinfo


            

    

Table 5-2. Table "b2b_entities" indexes

name	type	links	description
              b2b_entities_idx
            	unique	type, tag0, tag1, callid	              

 


            
              b2b_entities_param
            	default	param	              

 


            

    

Table 5-3. Table "b2b_logic"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              si_key
            	              string
            	              64
            	default	no	 	 	              

Scenario instantiation key


            
              scenario
            	              string
            	              64
            	default	yes	 	 	              

Scenario id


            
              sstate
            	              int
            	              2
            	default	no	 	 	              

Scenario State


            
              lifetime
            	              int
            	              10
            	0	no	 	 	              

Lifetime


            
              e1_type
            	              int
            	              2
            	default	no	 	 	              

E1 type


            
              e1_sid
            	              string
            	              64
            	default	yes	 	 	              

E1 Scenario ID


            
              e1_from
            	              string
            	              255
            	default	no	 	 	              

E1 From URI


            
              e1_to
            	              string
            	              255
            	default	no	 	 	              

E1 To URI


            
              e1_key
            	              string
            	              64
            	default	no	 	 	              

E1 Key


            
              e1_sdp
            	              text
            	              not specified
            	default	yes	 	 	              

E1 SDP


            
              e2_type
            	              int
            	              2
            	default	no	 	 	              

E2 type


            
              e2_sid
            	              string
            	              64
            	default	yes	 	 	              

E2 Scenario ID


            
              e2_from
            	              string
            	              255
            	default	no	 	 	              

E2 From URI


            
              e2_to
            	              string
            	              255
            	default	no	 	 	              

E2 To URI


            
              e2_key
            	              string
            	              64
            	default	no	 	 	              

E2 Key


            
              e2_sdp
            	              text
            	              not specified
            	default	yes	 	 	              

E2 SDP


            
              e3_type
            	              int
            	              2
            	default	yes	 	 	              

E3 type


            
              e3_sid
            	              string
            	              64
            	default	yes	 	 	              

E3 Scenario ID


            
              e3_from
            	              string
            	              255
            	default	yes	 	 	              

E3 From URI


            
              e3_to
            	              string
            	              255
            	default	yes	 	 	              

E3 To URI


            
              e3_key
            	              string
            	              64
            	default	yes	 	 	              

E3 Key


            

    

Table 5-4. Table "b2b_logic" indexes

name	type	links	description
              b2b_logic_idx
            	unique	si_key	              

 


            

  

Chapter 6. SCA support

    

b2b_sca

Persistent sca information for the b2b_sca module. More 
		information can be found at: https://opensips.org/docs/modules/devel/b2b_sca.html
		


  

    

Table 6-1. Table "b2b_sca"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              shared_line
            	              string
            	              64
            	default	no	 	 	              

The shared line.


            
              watchers
            	              string
            	              255
            	default	no	 	 	              

The URI list of watchers


            
              app1_shared_entity
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The entity to keep.


            
              app1_call_state
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The state of the appearance index.


            
              app1_call_info_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the Call-Info header


            
              app1_call_info_appearance_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the appearance in Call-Info header


            
              app1_b2bl_key
            	              string
            	              64
            	NULL	yes	 	 	              

The b2b_logic key.


            
              app2_shared_entity
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The entity to keep.


            
              app2_call_state
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The state of the appearance index.


            
              app2_call_info_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the Call-Info header


            
              app2_call_info_appearance_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the appearance in Call-Info header


            
              app2_b2bl_key
            	              string
            	              64
            	NULL	yes	 	 	              

The b2b_logic key.


            
              app3_shared_entity
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The entity to keep.


            
              app3_call_state
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The state of the appearance index.


            
              app3_call_info_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the Call-Info header


            
              app3_call_info_appearance_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the appearance in Call-Info header


            
              app3_b2bl_key
            	              string
            	              64
            	NULL	yes	 	 	              

The b2b_logic key.


            
              app4_shared_entity
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The entity to keep.


            
              app4_call_state
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The state of the appearance index.


            
              app4_call_info_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the Call-Info header


            
              app4_call_info_appearance_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the appearance in Call-Info header


            
              app4_b2bl_key
            	              string
            	              64
            	NULL	yes	 	 	              

The b2b_logic key.


            
              app5_shared_entity
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The entity to keep.


            
              app5_call_state
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The state of the appearance index.


            
              app5_call_info_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the Call-Info header


            
              app5_call_info_appearance_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the appearance in Call-Info header


            
              app5_b2bl_key
            	              string
            	              64
            	NULL	yes	 	 	              

The b2b_logic key.


            
              app6_shared_entity
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The entity to keep.


            
              app6_call_state
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The state of the appearance index.


            
              app6_call_info_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the Call-Info header


            
              app6_call_info_appearance_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the appearance in Call-Info header


            
              app6_b2bl_key
            	              string
            	              64
            	NULL	yes	 	 	              

The b2b_logic key.


            
              app7_shared_entity
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The entity to keep.


            
              app7_call_state
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The state of the appearance index.


            
              app7_call_info_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the Call-Info header


            
              app7_call_info_appearance_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the appearance in Call-Info header


            
              app7_b2bl_key
            	              string
            	              64
            	NULL	yes	 	 	              

The b2b_logic key.


            
              app8_shared_entity
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The entity to keep.


            
              app8_call_state
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The state of the appearance index.


            
              app8_call_info_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the Call-Info header


            
              app8_call_info_appearance_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the appearance in Call-Info header


            
              app8_b2bl_key
            	              string
            	              64
            	NULL	yes	 	 	              

The b2b_logic key.


            
              app9_shared_entity
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The entity to keep.


            
              app9_call_state
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The state of the appearance index.


            
              app9_call_info_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the Call-Info header


            
              app9_call_info_appearance_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the appearance in Call-Info header


            
              app9_b2bl_key
            	              string
            	              64
            	NULL	yes	 	 	              

The b2b_logic key.


            
              app10_shared_entity
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The entity to keep.


            
              app10_call_state
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

The state of the appearance index.


            
              app10_call_info_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the Call-Info header


            
              app10_call_info_appearance_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The URI of the appearance in Call-Info header


            
              app10_b2bl_key
            	              string
            	              64
            	NULL	yes	 	 	              

The b2b_logic key.


            

    

Table 6-2. Table "b2b_sca" indexes

name	type	links	description
              sca_idx
            	unique	shared_line	              

 


            

  

Chapter 7. CacheDB_SQL

    

cachedb

DB implementation of the CacheDB interface: https://opensips.org/docs/modules/devel/cachedb_sql.html
		


  

    

Table 7-1. Table "cachedb"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Table primary key, not used by module
		


            
              keyname
            	              string
            	              255
            	default	no	 	 	              

The Key


            
              value
            	              text
            	              512
            	default	no	 	 	              

The value


            
              counter
            	              int
            	              10
            	0	no	 	 	              

The value of the counter


            
              expires
            	              unsigned int
            	              10
            	0	no	 	 	              

The unix timestamp when the key will expires


            

    

Table 7-2. Table "cachedb" indexes

name	type	links	description
              cachedbsql_keyname_idx
            	unique	keyname	              

 


            

  

Chapter 8. Call Center

    

cc_flows

This table is used by the Call Center module to store
		the definition of the call queues / flows.
		More information can be found at: https://opensips.org/docs/modules/devel/call_center.html.
		

cc_agents

This table is used by the Call Center module to store
		the definition of the agents serving the flows/queues.
		More information can be found at: https://opensips.org/docs/modules/devel/call_center.html.
		

cc_cdrs

This table is used by the Call Center module to store
		the Call Data Records (CDRs) for all the handled calls.
		More information can be found at: https://opensips.org/docs/modules/devel/call_center.html.
		

cc_calls

This table is used by the Call Center module to store ongoing 
		calls for restart persitancy. It consists only of runtime data and 
		should not be manually provisioned.
		More information can be found at: https://opensips.org/docs/modules/devel/call_center.html.
		


  

    

Table 8-1. Table "cc_flows"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Flow unique ID in DB
		


            
              flowid
            	              string
            	              64
            	default	no	 	 	              

The unique ID of the flow in the
		Call Center module - to be used to identify the
		flow/queue in the module and from outside the module;
		It is an alphanumerical string.
		


            
              priority
            	              unsigned int
            	              11
            	256	no	 	 	              

The priority of the flow (in relation to
		the other flows); 0 is maximum priority and calls for
		this flow will be processed first all the time.
		


            
              skill
            	              string
            	              64
            	default	no	 	 	              

The skill required from an agent in order
		to receive calls from this flow/queue.
		


            
              prependcid
            	              string
            	              32
            	NULL	yes	 	 	              

Aphanumerical prefix to be added to the
		caller displayname when sending calls from this flow
		to agents (so agent - serving muliple flows - can see
		what was the flow the call was received on.
		


            
              max_wrapup_time
            	              unsigned int
            	              11
            	0	no	 	 	              

The maximum warpup time (in seconds) allowed
		for the call terminated via this flow. This value will 
		limit the default or per-agent wrapup time. A 0 value means
		no limit/max defined.
		


            
              dissuading_hangup
            	              unsigned int
            	              11
            	0	no	 	 	              

If set to true (non zero value), the calls diverted
		to dissuading destination will be closed after the dissuading 
		terminates (useful when using a playback for dissuading).
		


            
              dissuading_onhold_th
            	              unsigned int
            	              11
            	0	no	 	 	              

For how long (in seconds) a call will wait in the
		queue before getting a dissuading redirect.
		


            
              dissuading_ewt_th
            	              unsigned int
            	              11
            	0	no	 	 	              

The Estimated Waiting Time (in seconds) threshold that
		will redirect a new incoming call (not queued yet) to the
		dissuading destination.
		


            
              dissuading_qsize_th
            	              unsigned int
            	              11
            	0	no	 	 	              

The Size of the Queue (as already waiting calls in this
		flow) that will redirect a new incoming call (not queued yet) to the
		dissuading destination.
		


            
              message_welcome
            	              string
            	              128
            	NULL	yes	 	 	              

SIP URI point to a media server; this is
		used for playing the welcome message for this
		flow.


            
              message_queue
            	              string
            	              128
            	default	no	 	 	              

SIP URI point to a media server; this is
		used for playing the onhold message for this
		flow. IMPORTANT - this message must cycle and media
		server must never hung up on it.


            
              message_dissuading
            	              string
            	              128
            	NULL	yes	 	 	              

SIP URI point to a media server; this is
		used for playing the dissuading message for this
		flow.


            
              message_flow_id
            	              string
            	              128
            	NULL	yes	 	 	              

SIP URI point to a media server; this is
		used for playing the name of the flow id to the agent
		before delivering a call to him.


            

    

Table 8-2. Table "cc_flows" indexes

name	type	links	description
              unique_flowid
            	unique	flowid	              

 


            

    

Table 8-3. Table "cc_agents"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Agent unique ID in DB
		


            
              agentid
            	              string
            	              128
            	default	no	 	 	              

The unique ID of the agent in the
		Call Center module - to be used to identify the
		agent in the module and from outside the module;
		It is an alphanumerical string.
		


            
              location
            	              string
            	              128
            	default	yes	 	 	              

SIP URI point to the agent location;
		All calls for this agents will be sent to this
		SIP address.


            
              logstate
            	              unsigned int
            	              10
            	0	no	 	 	              

The call login state of the agent;
		0 - not logged in; 1 - logged in ; Agent will
		start receiving calls only if logged in.
		


            
              msrp_location
            	              string
            	              128
            	default	yes	 	 	              

MSRP SIP URI point to the agent location;
		All chat sessions for this agents will be sent to this
		SIP address.


            
              msrp_max_sessions
            	              unsigned int
            	              10
            	4	no	 	 	              

How many MSRP/chat sessions the agent
		can handle in the same time.
		


            
              skills
            	              string
            	              255
            	default	no	 	 	              

Comma separated list of skills offered
		by the agent; these skills must match the skills used
		in the queues/flows definition; In order to receive
		calls from a flow, the agent must have the skill required
		by that flow.
		


            
              wrapup_end_time
            	              int
            	              11
            	0	no	 	 	              

The timestamp when the last wrapup ends/ended for the
		agent. If different than 0, the agent will only receive calls after
		this timestamp.
		


            
              wrapup_time
            	              int
            	              11
            	0	no	 	 	              

The duration in seconds needed by the agent to wrap
		up the call he just completed. If set to 0, the global wraptup time
		will be used for this agent.
		


            

    

Table 8-4. Table "cc_agents" indexes

name	type	links	description
              unique_agentid
            	unique	agentid	              

 


            

    

Table 8-5. Table "cc_cdrs"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

CDR unique ID in DB
		


            
              caller
            	              string
            	              64
            	default	no	 	 	              

The SIP URI identifing the caller.
		


            
              received_timestamp
            	              datetime
            	              not specified
            	default	no	 	 	              

When the call was received.
		


            
              wait_time
            	              unsigned int
            	              11
            	0	no	 	 	              

Time (in seconds) spent by the call
		in queue (onhold).
		


            
              pickup_time
            	              unsigned int
            	              11
            	0	no	 	 	              

Time (in seconds) spent by the call
		in ringing to the agent.
		


            
              talk_time
            	              unsigned int
            	              11
            	0	no	 	 	              

The duration (in seconds) of the call.
		


            
              flow_id
            	              string
            	              128
            	default	no	 	 	              

The ID of the flow the call was
		received on.
		


            
              agent_id
            	              string
            	              128
            	NULL	yes	 	 	              

The ID of the agent who picked
		this call (if any).
		


            
              call_type
            	              int
            	              11
            	-1	no	 	 	              

Type of call: -2 - call rejected by agent;
		 -1 - call dropped because of internal error;
		  0 - call handled by agent;
		  1 - call dropped while in queue;
		


            
              rejected
            	              unsigned int
            	              11
            	0	no	 	 	              

How many times the call was rejected by agents
		(agent not answering his phone).
		


            
              fstats
            	              unsigned int
            	              11
            	0	no	 	 	              

Bitmask of the following binary flags: 
		0 - it is inbound call;
		1 - call was distributed to agents;
		2 - call was answered;
		3 - call was abandoned.
		


            
              cid
            	              unsigned int
            	              11
            	0	yes	 	 	              

Sequence number of the call.
		


            
              media
            	              int
            	              11
            	0	no	 	 	              

Media type of the call:
		  1 - RTP/audio;
		  2 - MSRP/chat;
		


            

    

Table 8-6. Table "cc_calls"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID of the call.
		


            
              state
            	              int
            	              11
            	default	no	 	 	              

The state of the call.
		


            
              media
            	              int
            	              11
            	default	no	 	 	              

Indicates the media type of the call,
		(0) RTP/audio or (1) MSRP/chat.
		


            
              ig_cback
            	              int
            	              11
            	default	no	 	 	              

Indicates if the call should be ignored.
		


            
              no_rej
            	              int
            	              11
            	default	no	 	 	              

Indicates whether the call can be rejected or not.
		


            
              setup_time
            	              int
            	              11
            	default	no	 	 	              

Stores the call setup time.
		


            
              eta
            	              int
            	              11
            	default	no	 	 	              

The estimated wait time for a call until
			it is answered by an agent.
		


            
              last_start
            	              int
            	              11
            	default	no	 	 	              

Stores the timestamp when the last call has started.
		


            
              recv_time
            	              int
            	              11
            	default	no	 	 	              

Stores the timestamp when the call was received by the
			call center.
		


            
              caller_dn
            	              string
            	              128
            	default	no	 	 	              

Caller Display Name.
		


            
              caller_un
            	              string
            	              128
            	default	no	 	 	              

Caller User Name.
		


            
              b2buaid
            	              string
            	              128
            	''	no	 	 	              

The B2B id internally used by the B2B module to identify
			the call.
		


            
              flow
            	              string
            	              128
            	default	no	 	 	              

The flow/queue this call belongs to.
		


            
              agent
            	              string
            	              128
            	default	no	 	 	              

The agent that handles the call.
		


            
              script_param
            	              string
            	              128
            	default	no	 	 	              

Parameter passed to the callcenter B2B logic scriptt.
		


            

    

Table 8-7. Table "cc_calls" indexes

name	type	links	description
              unique_id
            	unique	b2buaid	              

 


            
              b2buaid_idx
            	default	b2buaid	              

 


            

  

Chapter 9. carrierroute

    

carrierroute

This table is used by the carrierroute module to provides routing, balancing and blacklisting capabilities. More information is available at: https://opensips.org/docs/modules/devel/carrierroute.html
			  

carrierfailureroute

This table is used by the carrierroute module to provide failure routing capabilities. More information is available at: https://opensips.org/docs/modules/devel/carrierroute.html
			  

route_tree

This table is used by the carrierroute module to provides routing, balancing and blacklisting capabilities. More information is available at: https://opensips.org/docs/modules/devel/carrierroute.html
			  


  

    

Table 9-1. Table "carrierroute"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              carrier
            	              unsigned int
            	              10
            	0	no	 	 	              

This column contains the carrier id.


            
              domain
            	              string
            	              64
            	''	no	 	 	              

This column contains the route domain. Additional domains could be used for example as fallback.


            
              scan_prefix
            	              string
            	              64
            	''	no	 	 	              

This column contains the scan prefix, which define the matching portion of a phone number.


            
              flags
            	              unsigned int
            	              11
            	0	no	 	 	              

This column contains the flags used for rule matching.


            
              mask
            	              unsigned int
            	              11
            	0	no	 	 	              

This column contains the mask that is applied to the message flags before rule matching.


            
              prob
            	              float
            	              not specified
            	0	no	 	 	              

Name of column containing the probability. The probability value is used to distribute the traffic between several gateways.


            
              strip
            	              unsigned int
            	              11
            	0	no	 	 	              

Name of the column containing the number of digits to be stripped of the userpart of an URI before prepending rewrite_prefix.


            
              rewrite_host
            	              string
            	              255
            	''	no	 	 	              

Name of column containing rewrite prefixes. Here you can define a rewrite prefix for the localpart of the SIP URI.


            
              rewrite_prefix
            	              string
            	              64
            	''	no	 	 	              

Rewrite prefix for the localpart of the SIP URI.


            
              rewrite_suffix
            	              string
            	              64
            	''	no	 	 	              

Rewrite suffix for the localpart of the SIP URI.


            
              description
            	              string
            	              255
            	NULL	yes	 	 	              

A comment for the route entry, useful for larger routing tables.


            

    

Table 9-2. Table "carrierfailureroute"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              carrier
            	              unsigned int
            	              10
            	0	no	 	 	              

This column contains the carrier id.


            
              domain
            	              string
            	              64
            	''	no	 	 	              

This column contains the route domain. Additional domains could be used for example as fallback.


            
              scan_prefix
            	              string
            	              64
            	''	no	 	 	              

This column contains the scan prefix, which define the matching portion of a phone number.


            
              host_name
            	              string
            	              255
            	''	no	 	 	              

This column contains the routing destination used for rule matching.


            
              reply_code
            	              string
            	              3
            	''	no	 	 	              

This column contains the reply code used for rule matching.


            
              flags
            	              unsigned int
            	              11
            	0	no	 	 	              

This column contains the flags used for rule matching.


            
              mask
            	              unsigned int
            	              11
            	0	no	 	 	              

This column contains the mask that is applied to the message flags before rule matching.


            
              next_domain
            	              string
            	              64
            	''	no	 	 	              

This column contains the route domain that should be used for the next routing attempt.


            
              description
            	              string
            	              255
            	NULL	yes	 	 	              

A comment for the route entry, useful for larger routing tables.


            

    

Table 9-3. Table "route_tree"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              carrier
            	              string
            	              64
            	NULL	yes	 	 	              

This column contains the carrier name.


            

  

Chapter 10. Accounting

    

closeddial

This table is used by the closeddial module to provide closed dial functionality for groups of usernames; This is a functionality similar to a Centrex. More information about the closeddial module can be found at: https://opensips.org/docs/modules/devel/closeddial.html
        


  

    

Table 10-1. Table "closeddial"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              username
            	              string
            	              64
            	''	no	 	 	              

Username / phone number


            
              domain
            	              string
            	              64
            	''	no	 	 	              

Domain name


            
              cd_username
            	              string
            	              64
            	''	no	 	 	              

Closed dial username


            
              cd_domain
            	              string
            	              64
            	''	no	 	 	              

Closed dial domain


            
              group_id
            	              string
            	              64
            	''	no	 	 	              

Attribute use to group usernames


            
              new_uri
            	              string
            	              255
            	''	no	 	 	              

New URI


            

    

Table 10-2. Table "closeddial" indexes

name	type	links	description
              cd_idx1
            	unique	username, domain, cd_domain, cd_username, group_id	              

 


            
              cd_idx2
            	default	group_id	              

 


            
              cd_idx3
            	default	cd_username	              

 


            
              cd_idx4
            	default	username	              

 


            

  

Chapter 11. Clusterer support

    

clusterer

This table is used for defining clusters of OpenSIPS instances.
        


  

    

Table 11-1. Table "clusterer"

name	type	size	default	null	key	extra attributes	description
              id
            	              int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              cluster_id
            	              int
            	              10
            	default	no	 	 	              

unique identifier for a cluster


            
              node_id
            	              int
            	              10
            	default	no	 	 	              

unique identifier for a node


            
              url
            	              string
            	              64
            	default	no	 	 	              

network location of the machine, like protocol:ip:port


            
              state
            	              int
            	              1
            	1	no	 	 	              

state of the  machine 1 - Enabled, 0 - Disabled


            
              no_ping_retries
            	              int
            	              10
            	3	no	 	 	              

maximum number of ping retries before the link with a node is considered down


            
              priority
            	              int
            	              10
            	50	no	 	 	              

priority to be chosen as next hop in case of same length(number of hops) paths


            
              sip_addr
            	              string
            	              64
            	default	yes	 	 	              

SIP address, currently not used by the module


            
              flags
            	              string
            	              64
            	default	yes	 	 	              

Node flags: "seed" - node automatically considered to be synchronized


            
              description
            	              string
            	              64
            	default	yes	 	 	              

opaque text not used by the module


            

    

Table 11-2. Table "clusterer" indexes

name	type	links	description
              clusterer_idx
            	unique	cluster_id, node_id	              

 


            

  

Chapter 12. Call-processing language

    

cpl

Table for the call processing language "cpl" module. More information is available at: https://opensips.org/docs/modules/devel/cpl_c.html


  

    

Table 12-1. Table "cpl"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              username
            	              string
            	              64
            	default	no	 	 	              

 


            
              domain
            	              string
            	              64
            	''	no	 	 	              

 


            
              cpl_xml
            	              text
            	              not specified
            	default	yes	 	 	              

 


            
              cpl_bin
            	              text
            	              not specified
            	default	yes	 	 	              

 


            

    

Table 12-2. Table "cpl" indexes

name	type	links	description
              account_idx
            	unique	username, domain	              

 


            

  

Chapter 13. Dialog support

    

dialog

Persistent dialog information for the dialog module. More
		information can be found at: https://opensips.org/docs/modules/devel/dialog.html
		


  

    

Table 13-1. Table "dialog"

name	type	size	default	null	key	extra attributes	description
              dlg_id
            	              unsigned long
            	              10
            	default	no	primary	 	              

h_entry | h_id


            
              callid
            	              string
            	              255
            	default	no	 	 	              

Call-ID of the dialog


            
              from_uri
            	              string
            	              255
            	default	no	 	 	              

The URI of the FROM header (as per INVITE)


            
              from_tag
            	              string
            	              64
            	default	no	 	 	              

The tag parameter serves as a general mechanism to
		identify a dialog, which is the combination of the Call-ID along
		with two tags, one from participant in the dialog.


            
              to_uri
            	              string
            	              255
            	default	no	 	 	              

The URI of the TO header (as per INVITE)


            
              to_tag
            	              string
            	              64
            	default	no	 	 	              

The tag parameter serves as a general mechanism to
		identify a dialog, which is the combination of the Call-ID along
		with two tags, one from participant in the dialog.


            
              mangled_from_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The mangled from URI, in case uac_replace_from
		was called for this dialog.


            
              mangled_to_uri
            	              string
            	              255
            	NULL	yes	 	 	              

The mangled to URI, in case uac_replace_to
		was called for this dialog


            
              caller_cseq
            	              string
            	              11
            	default	no	 	 	              

Last Cseq number on the caller side.


            
              callee_cseq
            	              string
            	              11
            	default	no	 	 	              

Last Cseq number on the callee side.


            
              caller_ping_cseq
            	              unsigned int
            	              11
            	default	no	 	 	              

Last Cseq number of pings generated on caller side.


            
              callee_ping_cseq
            	              unsigned int
            	              11
            	default	no	 	 	              

Last Cseq number of pings generated on callee side.


            
              caller_route_set
            	              text
            	              512
            	default	yes	 	 	              

Route set on the caller side.


            
              callee_route_set
            	              text
            	              512
            	default	yes	 	 	              

Route set on on the caller side.


            
              caller_contact
            	              string
            	              255
            	default	yes	 	 	              

Caller's contact uri.


            
              callee_contact
            	              string
            	              255
            	default	yes	 	 	              

Callee's contact uri.


            
              caller_sock
            	              string
            	              64
            	default	no	 	 	              

Local socket used to communicate with caller


            
              callee_sock
            	              string
            	              64
            	default	no	 	 	              

Local socket used to communicate with callee


            
              state
            	              unsigned int
            	              10
            	default	no	 	 	              

The state of the dialog.


            
              start_time
            	              unsigned int
            	              10
            	default	no	 	 	              

The timestamp (unix time) when the dialog was confirmed.
		


            
              timeout
            	              unsigned int
            	              10
            	default	no	 	 	              

The timestamp (unix time) when the dialog will expire.
		


            
              vars
            	              binary
            	              4096
            	NULL	yes	 	 	              

Variables attached to this dialog.


            
              profiles
            	              text
            	              512
            	NULL	yes	 	 	              

Profiles this dialog belongs to.


            
              script_flags
            	              string
            	              255
            	NULL	yes	 	 	              

Script flags for the dialog.


            
              module_flags
            	              unsigned int
            	              10
            	0	no	 	 	              

Module flags for the dialog.


            
              flags
            	              unsigned int
            	              10
            	0	no	 	 	              

Internal flags used by the module.


            
              rt_on_answer
            	              string
            	              64
            	NULL	yes	 	 	              

The name of the script route to be executed
		upon call answering


            
              rt_on_timeout
            	              string
            	              64
            	NULL	yes	 	 	              

The name of the script route to be executed
		upon call timeout (as duration)


            
              rt_on_hangup
            	              string
            	              64
            	NULL	yes	 	 	              

The name of the script route to be executed
		upon call hangup


            

  

Chapter 14. Matching and translation rules

    

dialplan

This table is used by the dialplan module for the translation rules. More information is available at: https://opensips.org/docs/modules/devel/dialplan.html
        


  

    

Table 14-1. Table "dialplan"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              dpid
            	              int
            	              11
            	default	no	 	 	              

Dialplan ID.


            
              pr
            	              int
            	              11
            	0	no	 	 	              

Priority of rule.


            
              match_op
            	              int
            	              11
            	default	no	 	 	              

Matching operator for rule (0-equal, 1-regexp).


            
              match_exp
            	              string
            	              64
            	default	no	 	 	              

Matching expression (regexp or string).


            
              match_flags
            	              int
            	              11
            	0	no	 	 	              

Matching flags (0-case sensitive, 1-case insensitive).


            
              subst_exp
            	              string
            	              64
            	NULL	yes	 	 	              

Substitution expression.


            
              repl_exp
            	              string
            	              32
            	NULL	yes	 	 	              

Replacement expression (sed like).


            
              timerec
            	              string
            	              255
            	NULL	yes	 	 	              

Time recurrence used to match this rule.


            
              disabled
            	              int
            	              11
            	0	no	 	 	              

Specifies if the command can be used, or is disabled.


            
              attrs
            	              string
            	              255
            	NULL	yes	 	 	              

General attributes string to be returned in case of rule matching.


            

  

Chapter 15. Dispatcher

    

dispatcher

This table is used by the dispatcher module. It contains the sets of destinations used for load balancing and dispatching. More information about the dispatcher module can be found at: https://opensips.org/docs/modules/devel/dispatcher.html
        


  

    

Table 15-1. Table "dispatcher"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              setid
            	              int
            	              not specified
            	0	no	 	 	              

Destination set id


            
              destination
            	              string
            	              192
            	''	no	 	 	              

Destination SIP address


            
              socket
            	              string
            	              128
            	NULL	yes	 	 	              

Local Socket to be used when sending requests (traffic and probes)
        to the destination - must be an listener configured in opensips.
        


            
              state
            	              int
            	              not specified
            	0	no	 	 	              

The state of the destination (0 enabled, 1 disabled , 2 probing)


            
              probe_mode
            	              unsigned int
            	              11
            	0	no	 	 	              

0-Probe only when in probing state; 1-Probe even in enable/active state;


            
              weight
            	              string
            	              64
            	1	no	 	 	              

The weight of the destination (integer or socket definition) 


            
              priority
            	              int
            	              not specified
            	0	no	 	 	              

The priority of each destination (only useful with algorithm 8)


            
              attrs
            	              string
            	              128
            	NULL	yes	 	 	              

Attribute string - custom, opaque string that
        will be pushed into script when this destination will 
        be selected


            
              description
            	              string
            	              64
            	NULL	yes	 	 	              

Description for this destination


            

  

Chapter 16. Domain

    

domain

This table is used by the domain module to determine if a host part of a URI is "local" or not. More information about the domain module can be found at: https://opensips.org/docs/modules/devel/domain.html
        


  

    

Table 16-1. Table "domain"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              domain
            	              string
            	              64
            	''	no	 	 	              

Domain name


            
              attrs
            	              string
            	              255
            	NULL	yes	 	 	              

Domain Attributes


            
              last_modified
            	              datetime
            	              not specified
            	'1900-01-01 00:00:01'	no	 	 	              

Date and time when this record was last modified.


            

    

Table 16-2. Table "domain" indexes

name	type	links	description
              domain_idx
            	unique	domain	              

 


            

  

Chapter 17. Domainpolicy

    

domainpolicy

Table for the domainpolicy module. More information at https://opensips.org/docs/modules/devel/domainpolicy.html.
        


  

    

Table 17-1. Table "domainpolicy"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              rule
            	              string
            	              255
            	default	no	 	 	              

Domain policy rule name which is equal to the URI as published in the domain policy NAPTRs.


            
              type
            	              string
            	              255
            	default	no	 	 	              

 Domain policy rule type. In the case of federation names, this is "fed". For standard referrals according to draft-lendl-speermint-technical-policy-00, this is "std". For direct domain lookups, this is "dom". Default value is "type".


            
              att
            	              string
            	              255
            	default	yes	 	 	              

It contains the AVP's name. If the rule stored in this row triggers, than dp_can_connect() will add an AVP with that name.


            
              val
            	              string
            	              128
            	default	yes	 	 	              

It contains the values for AVPs created by dp_can_connect(). Default value is "val"


            
              description
            	              string
            	              255
            	default	no	 	 	              

Comment about the rule


            

    

Table 17-2. Table "domainpolicy" indexes

name	type	links	description
              rav_idx
            	unique	rule, att, val	              

 


            
              rule_idx
            	default	rule	              

 


            

  

Chapter 18. Dynamic Routing

    

dr_gateways

This table is used by the Dynamic Routing module to store
		information about the destinations/gateways where to route calls.
		More information can be found at: https://opensips.org/docs/modules/devel/drouting.html.
		

dr_rules

This table is used by the Dynamic Routing module to store
		information about the routing rules.
		More information can be found at: https://opensips.org/docs/modules/devel/drouting.html.
		

dr_carriers

This table is used by the Dynamic Routing module to define
		carriers (a carrier is defined by a list of gateways and an ordering
		rule).
		More information can be found at: https://opensips.org/docs/modules/devel/drouting.html.
		

dr_groups

This table is used by the Dynamic Routing module to store
		information about the routing groups (users mapped over groups).
		More information can be found at: https://opensips.org/docs/modules/devel/drouting.html.
		

dr_partitions

This table is used by the Dynamic Routing module to store
		information about the partitions used in routing (url to database, 
		table names and AVP names for each partition).
		More information can be found at: https://opensips.org/docs/modules/devel/drouting.html.
		


  

    

Table 18-1. Table "dr_gateways"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Table primary key, not used by module
		


            
              gwid
            	              string
            	              64
            	default	no	 	 	              

GW unique ID - used to link the GW from 
			the routing rules
		


            
              type
            	              unsigned int
            	              11
            	0	no	 	 	              

Type/class of the GW (user defined)


            
              address
            	              string
            	              128
            	default	no	 	 	              

GW/destination address as name/IP[:port]


            
              strip
            	              unsigned int
            	              11
            	0	no	 	 	              

Number of digits to be striped out for the beginning 
			of the username when using this GW/destination


            
              pri_prefix
            	              string
            	              16
            	NULL	yes	 	 	              

String to prefix the username of RURI when using 
			this GW/destination


            
              attrs
            	              string
            	              255
            	NULL	yes	 	 	              

Generic string describing GW attributes - this string is
			to be interpreted from the script


            
              probe_mode
            	              unsigned int
            	              11
            	0	no	 	 	              

0- No probing; 1-Probe on disable only ; 2-Always probe;  


            
              state
            	              unsigned int
            	              11
            	0	no	 	 	              

State of the gateway: 0 - enabled; 1 - permanent disabled;
                2 - temporary disabled (probing)


            
              socket
            	              string
            	              128
            	NULL	yes	 	 	              

Local Socket to be used when sending requests (traffic and probes)
		to the destination - must be an listener configured in opensips.
		


            
              description
            	              string
            	              128
            	NULL	yes	 	 	              

Text description of the GW/destination


            

    

Table 18-2. Table "dr_gateways" indexes

name	type	links	description
              dr_gw_idx
            	unique	gwid	              

 


            

    

Table 18-3. Table "dr_rules"

name	type	size	default	null	key	extra attributes	description
              ruleid
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Rule unique ID
		


            
              groupid
            	              string
            	              255
            	default	no	 	 	              

The ID(s) of the routing group(s) this rule is to be
		used for - comma separeted list of numerical Ids
		


            
              prefix
            	              string
            	              64
            	default	no	 	 	              

Numerical prefix to match this rule


            
              timerec
            	              string
            	              255
            	NULL	yes	 	 	              

Time recurrence used for matching this rule.


            
              priority
            	              int
            	              11
            	0	no	 	 	              

Priority of this rule (among rules with same prefix
		and timerec).


            
              routeid
            	              string
            	              255
            	NULL	yes	 	 	              

Route block (from cfg script) to be called when rule
		matches.


            
              gwlist
            	              string
            	              255
            	default	yes	 	 	              

A comma-separated list of GW unique IDs (e.g. GW-5)
			and/or hash-prefixed ("#") Carrier unique IDs (e.g. #CR-2).


            
              sort_alg
            	              string
            	              1
            	'N'	no	 	 	              

The sorting algorithm to be employed for the rule's
			destinations when do_routing() is called.  Possible values:
			'N' (default; no sorting, preserve given order),
			'W' (weight based sorting),
			'Q' (quality-based sorting, provided by the qrouting module)
		


            
              sort_profile
            	              unsigned int
            	              10
            	NULL	yes	 	 	              

Whenever the 'Q' (quality-based routing) sorting algorithm
			is provided, this column must hold a profile id belonging to the
			"qr_profiles" table.
		


            
              attrs
            	              string
            	              255
            	NULL	yes	 	 	              

Generic string describing RULE attributes - this string is
			to be interpreted from the script


            
              description
            	              string
            	              128
            	NULL	yes	 	 	              

Text description of the rule


            

    

Table 18-4. Table "dr_carriers"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Table key, not used by module


            
              carrierid
            	              string
            	              64
            	default	no	 	 	              

Unique ID of the carrier


            
              gwlist
            	              string
            	              255
            	default	no	 	 	              

A comma-separated list of GW unique IDs (e.g. GW-5).
		


            
              flags
            	              unsigned int
            	              11
            	0	no	 	 	              

Flags of the carriers (for different purposes: 
					use only first gw from cr (set the first bit of the flag); 
					disable gateway (set the second bit of the flag);
		


            
              sort_alg
            	              string
            	              1
            	'N'	no	 	 	              

The sorting algorithm to be employed for the carrier's
			destinations when do_routing() is called.  Possible values:
			'N' (default; no sorting, preserve given order),
			'W' (weight based sorting),
			'Q' (quality-based sorting, provided by the qrouting module)
		


            
              state
            	              unsigned int
            	              11
            	0	no	 	 	              

The state of the carrier (on / off).
		


            
              attrs
            	              string
            	              255
            	NULL	yes	 	 	              

Attributes string for the carrier
		


            
              description
            	              string
            	              128
            	NULL	yes	 	 	              

Text description of the GW list


            

    

Table 18-5. Table "dr_carriers" indexes

name	type	links	description
              dr_carrier_idx
            	unique	carrierid	              

 


            

    

Table 18-6. Table "dr_groups"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              username
            	              string
            	              64
            	default	no	 	 	              

Username part of user


            
              domain
            	              string
            	              128
            	NULL	yes	 	 	              

Domain part of user


            
              groupid
            	              unsigned int
            	              11
            	0	no	 	 	              

The ID of the routing group the user belongs to.
		


            
              description
            	              string
            	              128
            	NULL	yes	 	 	              

Text description of the group/user


            

    

Table 18-7. Table "dr_partitions"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Partition unique ID
		


            
              partition_name
            	              string
            	              255
            	default	no	 	 	              

The name of the partition.
		


            
              db_url
            	              string
            	              255
            	default	no	 	 	              

The url to the database containing the tables: dr_rules, dr_groups,
		dr_carriers and dr_gateways


            
              drd_table
            	              string
            	              255
            	default	yes	 	 	              

The name of the dr_gateways table in the given database (for the given partition).


            
              drr_table
            	              string
            	              255
            	default	yes	 	 	              

The name of the dr_rules table in the given database (for the given partition).


            
              drg_table
            	              string
            	              255
            	default	yes	 	 	              

The name of the dr_groups table in the given database (for the given partition).


            
              drc_table
            	              string
            	              255
            	default	yes	 	 	              

The name of the dr_carriers table in the given database (for the given partition).


            
              ruri_avp
            	              string
            	              255
            	default	yes	 	 	              

The name of ruri_avp AVP.


            
              gw_id_avp
            	              string
            	              255
            	default	yes	 	 	              

The name of gw_id_avp AVP


            
              gw_priprefix_avp
            	              string
            	              255
            	default	yes	 	 	              

The name of gw_priprefix_avp AVP.


            
              gw_sock_avp
            	              string
            	              255
            	default	yes	 	 	              

The name of gw_sock_avp AVP.


            
              rule_id_avp
            	              string
            	              255
            	default	yes	 	 	              

The name of rule_id_avp AVP.


            
              rule_prefix_avp
            	              string
            	              255
            	default	yes	 	 	              

The name of rule_prefix_avp AVP.


            
              carrier_id_avp
            	              string
            	              255
            	default	yes	 	 	              

The name of carrier_id_avp AVP.


            

  

Chapter 19. Emergency

    

emergency_routing

This table is used by the Emergency module to translate ERT informations in ESGWRI.
		More information can be found at: https://opensips.org/docs/modules/devel/emergency.html.
		

emergency_report

This table is used by the Emergency module to save information associated 
		  with a emergency call, for trouble shooting purposes.
		  More information can be found at: https://opensips.org/docs/modules/devel/emergency.html.
		

emergency_service_provider

This table is used by the Emergency module to store information of the organizations involved 
		in the routing of the emergency call, this information is necessary to send the request to the VPC, 
		according to the NENA standard. 
		This table isn't necessary if opensips role not send request to VPC, such as the opensips acting as call server in the scenarios II and III.
		More information can be found at: https://opensips.org/docs/modules/devel/emergency.html.
		


  

    

Table 19-1. Table "emergency_routing"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              selectiveRoutingID
            	              string
            	              11
            	default	no	 	 	              

The Common Language Location Indicator(CLLI) code associated
		  with the Selective Router to which the emergency call is to be directed
		


            
              routingESN
            	              unsigned int
            	              5
            	0	no	 	 	              

 The Emergency Services Number associated with a particular ESZ 
		  that respresents a unique combination of Police, Fire and EMS emergency responders.
		


            
              npa
            	              unsigned int
            	              3
            	0	no	 	 	              

 The primary Numbering Plan Area (NPA) associated with
		the outgoing route to the Selective Router that is appropriate for
		caller's location.
		


            
              esgwri
            	              string
            	              50
            	default	no	 	 	              

 Routing information used to direct the call to the ESGW.
		


            

    

Table 19-2. Table "emergency_report"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              callid
            	              string
            	              25
            	default	no	 	 	              

 header that uniquely identifies the call.
		


            
              selectiveRoutingID
            	              string
            	              11
            	default	no	 	 	              

The Common Language Location Indicator(CLLI) code associated
		  with the Selective Router to which the emergency call is to be directed
		


            
              routingESN
            	              unsigned int
            	              5
            	0	no	 	 	              

 The Emergency Services Number associated with a particular ESZ 
		  that respresents a unique combination of Police, Fire and EMS emergency responders.
		


            
              npa
            	              unsigned int
            	              3
            	0	no	 	 	              

 The primary Numbering Plan Area (NPA) associated with 
		the outgoing route to the Selective Router that is appropriate for 
		caller's location.
		


            
              esgwri
            	              string
            	              50
            	default	no	 	 	              

 Routing information used to direct the call to the ESGW.
		


            
              lro
            	              string
            	              20
            	default	no	 	 	              

last routing option destination for the call.
		


            
              VPC_organizationName
            	              string
            	              50
            	default	no	 	 	              

 company name or other label of the VPC that provided the routing information.
		


            
              VPC_hostname
            	              string
            	              50
            	default	no	 	 	              

 identifies the fully qualified domain name or IP address
		  of the VPC that provided routing information.
		


            
              VPC_timestamp
            	              string
            	              30
            	default	no	 	 	              

Date Time Stamp indicating UTC date and time that the message was sent from VPC.
		


            
              result
            	              string
            	              4
            	default	no	 	 	              

 Code indicating the reason for success or failure to determine an ERT/ESGWRI and ESQK.
		


            
              disposition
            	              string
            	              10
            	default	no	 	 	              

 Describe how routing of call was done(e.g.,by ESGWRI or bye LRO)
		


            

    

Table 19-3. Table "emergency_service_provider"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              organizationName
            	              string
            	              50
            	default	no	 	 	              

provider company name's. This parameter is optional 
		field in the NENA v2 interface (call server - VPC)
		


            
              hostId
            	              string
            	              30
            	default	no	 	 	              

 provider hostname's. This parameter isÂ  mandatory if 
		attribution is 0(source) or 2(VSP), otherwise it is optional.
		


            
              nenaId
            	              string
            	              50
            	default	no	 	 	              

 the NENA administered company identifier (NENA Company ID) of provider. 
			This parameter is optional field in the NENA v2 interface (call server - VPC). 
		


            
              contact
            	              string
            	              20
            	default	no	 	 	              

  telephone number by which the provider operator can be reachedÂ 24 hours a day, 7 days a week. 
			This parameter isÂ  mandatory if attribution is 0(source) or 2(VSP), otherwise it is optional.
		


            
              certUri
            	              string
            	              50
            	default	no	 	 	              

 provides a means of directly obtaining the VESA(ValidÂ Emergency Services Authority) issued certificate for the provider. 
		         This parameter is optional field in the NENAÂ v2 interface (call server - VPC).
		


            
              nodeIP
            	              string
            	              20
            	default	no	 	 	              

 IP address of the node that is being registered. This parameter isÂ  mandatory.
		


            
              attribution
            	              unsigned int
            	              2
            	default	no	 	 	              

 It is a field of type int designating the function of the organization involvedÂ in the composition of architecture NENA being registered in this table. This parameter isÂ  mandatory.Â 
		  The values that this field can take are:
		  0 - the organization is a Source. Source is node directly requesting emergency call routing from the VPC.
		  1 - the organization is a VPC. VPC is the routing information provider to emengency call
		  2- the organization is a VSP. VSP is the caller's voice service provider 
		


            

  

Chapter 20. Fraud Detection

    

fraud_detection

This table is used by the Fraud Detection module to store
		information about fraud-profiles.
		More information can be found at: https://opensips.org/docs/modules/devel/fraud_detection.html.
		


  

    

Table 20-1. Table "fraud_detection"

name	type	size	default	null	key	extra attributes	description
              ruleid
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Rule unique ID
		


            
              profileid
            	              unsigned int
            	              not specified
            	default	no	 	 	              

The ID of the profile the current rule is part of
		


            
              prefix
            	              string
            	              64
            	default	no	 	 	              

Numerical prefix to match this rule


            
              start_hour
            	              string
            	              5
            	'00:00'	no	 	 	              

Start of the interval in which the rule should be matched.
		


            
              end_hour
            	              string
            	              5
            	'23:59'	no	 	 	              

End of the interval in which the rule should be matched.
		


            
              daysoftheweek
            	              string
            	              64
            	'Mon-Sun'	no	 	 	              

List/interval of days in which the rule is available.
		


            
              cpm_warning
            	              unsigned int
            	              5
            	0	no	 	 	              

Warning threshold for calls per minute.


            
              cpm_critical
            	              unsigned int
            	              5
            	0	no	 	 	              

Crtical threshold for calls per minute.


            
              call_duration_warning
            	              unsigned int
            	              5
            	0	no	 	 	              

Warning threshold for calls per minute.


            
              call_duration_critical
            	              unsigned int
            	              5
            	0	no	 	 	              

Crtical threshold for call duration.


            
              total_calls_warning
            	              unsigned int
            	              5
            	0	no	 	 	              

Warning threshold for total calls.


            
              total_calls_critical
            	              unsigned int
            	              5
            	0	no	 	 	              

Crtical threshold for total calls.


            
              concurrent_calls_warning
            	              unsigned int
            	              5
            	0	no	 	 	              

Warning threshold for concurrent calls.


            
              concurrent_calls_critical
            	              unsigned int
            	              5
            	0	no	 	 	              

Crtical threshold for concurrent calls.


            
              sequential_calls_warning
            	              unsigned int
            	              5
            	0	no	 	 	              

Warning threshold for sequential calls.


            
              sequential_calls_critical
            	              unsigned int
            	              5
            	0	no	 	 	              

Crtical threshold for sequential calls.


            

  

Chapter 21. FreeSWITCH ESL Integration

    

freeswitch

Generic FreeSWITCH integration, allowing full control over
		the ESL commands and event notifications. More information can be found
		at: https://opensips.org/docs/modules/devel/freeswitch_scripting.html
		


  

    

Table 21-1. Table "freeswitch"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              username
            	              string
            	              64
            	default	yes	 	 	              

FreeSWITCH ESL authentication username


            
              password
            	              string
            	              64
            	default	no	 	 	              

FreeSWITCH ESL authentication password (plain text)


            
              ip
            	              string
            	              20
            	default	no	 	 	              

FreeSWITCH ESL IP address


            
              port
            	              int
            	              11
            	8021	no	 	 	              

FreeSWITCH ESL port


            
              events_csv
            	              string
            	              255
            	default	yes	 	 	              

Comma-separated, case-sensitive values holding the exact FreeSWITCH ESL events which OpenSIPS will attempt to subscribe to


            

  

Chapter 22. Group checking

    

grp

This table us used by the group module as a means of group membership checking. Used primarily for Access Control Lists (ACL's). More information about the group module can be found at: https://opensips.org/docs/modules/devel/group.html
        

re_grp

 This table is used by the group module to check membership based on regular expressions. More information about the group module can be found at: https://opensips.org/docs/modules/devel/group.html
        


  

    

Table 22-1. Table "grp"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              username
            	              string
            	              64
            	''	no	 	 	              

Username / phone number


            
              domain
            	              string
            	              64
            	''	no	 	 	              

Domain name


            
              grp
            	              string
            	              64
            	''	no	 	 	              

Group name


            
              last_modified
            	              datetime
            	              not specified
            	'1900-01-01 00:00:01'	no	 	 	              

Date and time when this record was last modified.


            

    

Table 22-2. Table "grp" indexes

name	type	links	description
              account_group_idx
            	unique	username, domain, grp	              

 


            

    

Table 22-3. Table "re_grp"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              reg_exp
            	              string
            	              128
            	''	no	 	 	              

Regular expression


            
              group_id
            	              int
            	              11
            	0	no	 	 	              

Group ID


            

    

Table 22-4. Table "re_grp" indexes

name	type	links	description
              group_idx
            	default	group_id	              

 


            

  

Chapter 23. Instant Message Conference

    

imc_rooms

Room table for the IMC module. More information at https://opensips.org/docs/modules/devel/imc.html.
        

imc_members

Member table for the IMC module. More information at https://opensips.org/docs/modules/devel/imc.html.
        


  

    

Table 23-1. Table "imc_rooms"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              name
            	              string
            	              64
            	default	no	 	 	              

Name of the room


            
              domain
            	              string
            	              64
            	default	no	 	 	              

Domain of the room


            
              flag
            	              int
            	              11
            	default	no	 	 	              

Flags


            

    

Table 23-2. Table "imc_rooms" indexes

name	type	links	description
              name_domain_idx
            	unique	name, domain	              

 


            

    

Table 23-3. Table "imc_members"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              username
            	              string
            	              64
            	default	no	 	 	              

Username


            
              domain
            	              string
            	              64
            	default	no	 	 	              

Domain


            
              room
            	              string
            	              64
            	default	no	 	 	              

 


            
              flag
            	              int
            	              11
            	default	no	 	 	              

Flags


            

    

Table 23-4. Table "imc_members" indexes

name	type	links	description
              account_room_idx
            	unique	username, domain, room	              

 


            

  

Chapter 24. JANUS

    

janus

This table is used by the JANUS module to store
		definitions of socket(s) used to connect to.
		More information can be found at: https://opensips.org/docs/modules/devel/janus.html.
		


  

    

Table 24-1. Table "janus"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              janus_id
            	              text
            	              not specified
            	default	no	 	 	              

JANUS identifier as referenced from the OpenSIPS script.			Example: "my_janus".
		


            
              janus_url
            	              text
            	              not specified
            	default	no	 	 	              

JANUS socket used to send commands.
			Example: "janusws://1.2.3.4:80/janus?room=abcd".
		


            

  

Chapter 25. Load Balancer

    

load_balancer

This table is used by the Load-Balancer module to store
		information about the destinations the balance the calls between.
		More information can be found at: https://opensips.org/docs/modules/devel/load_balancer.html.
		


  

    

Table 25-1. Table "load_balancer"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID of the destination
		


            
              group_id
            	              unsigned int
            	              11
            	0	no	 	 	              

The group the destination belongs to


            
              dst_uri
            	              string
            	              128
            	default	no	 	 	              

Destination address as a SIP URI


            
              resources
            	              string
            	              255
            	default	no	 	 	              

String with the definition of the resource provided
		by the destination and the capacity of each resource


            
              probe_mode
            	              unsigned int
            	              11
            	0	no	 	 	              

Probing mode (0-none, 1-if disabled, 2-all the time)


            
              attrs
            	              string
            	              255
            	NULL	yes	 	 	              

Attribute string - custom, opaque string that
		will simply be pushed into script


            
              description
            	              string
            	              128
            	NULL	yes	 	 	              

Text description of the destination


            

    

Table 25-2. Table "load_balancer" indexes

name	type	links	description
              dsturi_idx
            	default	dst_uri	              

 


            

  

Chapter 26. Message Storage

    

silo

 This table us used by the msilo module to provide offline message storage More information about the msilo module can be found at: https://opensips.org/docs/modules/devel/msilo.html
        


  

    

Table 26-1. Table "silo"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              src_addr
            	              string
            	              255
            	''	no	 	 	              

Source address - From URI


            
              dst_addr
            	              string
            	              255
            	''	no	 	 	              

Destination address - To URI


            
              username
            	              string
            	              64
            	''	no	 	 	              

SIP domain of target user


            
              domain
            	              string
            	              64
            	''	no	 	 	              

Username / phone number of target user


            
              inc_time
            	              int
            	              not specified
            	0	no	 	 	              

Incoming time


            
              exp_time
            	              int
            	              not specified
            	0	no	 	 	              

Expiration time


            
              snd_time
            	              int
            	              not specified
            	0	no	 	 	              

Reminder send time


            
              ctype
            	              string
            	              255
            	NULL	yes	 	 	              

Content type


            
              body
            	              binary
            	              not specified
            	NULL	yes	 	 	              

Body of the message


            

    

Table 26-2. Table "silo" indexes

name	type	links	description
              account_idx
            	default	username, domain	              

 


            

  

Chapter 27. Permissions

    

address

This table is used by the permissions module. More information is available at: https://opensips.org/docs/modules/devel/permissions.html
		


  

    

Table 27-1. Table "address"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              grp
            	              unsigned short
            	              5
            	0	no	 	 	              

The group ID - each address may belong to a group/set


            
              ip
            	              string
            	              50
            	default	no	 	 	              

IP address, IPv4 or IPv6 format


            
              mask
            	              char
            	              not specified
            	32	no	 	 	              

Network mask, a number from 0 to 128; It should be up to 32 if the IP is v4 and up to 128 if the IP is v6


            
              port
            	              unsigned short
            	              5
            	0	no	 	 	              

Port number, 0 value meaning 'any' (wildcard)


            
              proto
            	              string
            	              4
            	'any'	no	 	 	              

Transport protocol is either "any" or equal to transport protocol of request. Possible values that can be stored are "any", "udp", "tcp", "tls", and "sctp".


            
              pattern
            	              string
            	              64
            	NULL	yes	 	 	              

A shell wildcard pattern to be used for matching string provided by the check address functions.


            
              context_info
            	              string
            	              32
            	NULL	yes	 	 	              

Extra context information, not used by OpenSIPS, but simply exposed to the script level via scripting variables


            

  

Chapter 28. Presence

    

presentity

Table for the presence module. More information can be found at: https://opensips.org/docs/modules/devel/presence.html
        

active_watchers

Table for the presence module. More information can be found at: https://opensips.org/docs/modules/devel/presence.html
        

watchers

Table for the presence module. More information can be found at: https://opensips.org/docs/modules/devel/presence.html
        

xcap

Table for the presence module. More information can be found at: https://opensips.org/docs/modules/devel/presence.html
        

pua

Table for the presence related pua module. More information can be found at: https://opensips.org/docs/modules/devel/pua.html
        


  

    

Table 28-1. Table "presentity"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              username
            	              string
            	              64
            	default	no	 	 	              

User name


            
              domain
            	              string
            	              64
            	default	no	 	 	              

Domain


            
              event
            	              string
            	              64
            	default	no	 	 	              

Event


            
              etag
            	              string
            	              64
            	default	no	 	 	              

User name


            
              expires
            	              int
            	              11
            	default	no	 	 	              

Expires


            
              received_time
            	              int
            	              11
            	default	no	 	 	              

Reveived time


            
              body
            	              binary
            	              not specified
            	NULL	yes	 	 	              

 


            
              extra_hdrs
            	              binary
            	              not specified
            	NULL	yes	 	 	              

 


            
              sender
            	              string
            	              255
            	NULL	yes	 	 	              

Sender contact


            

    

Table 28-2. Table "presentity" indexes

name	type	links	description
              presentity_idx
            	unique	username, domain, event, etag	              

 


            

    

Table 28-3. Table "active_watchers"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              presentity_uri
            	              string
            	              255
            	default	no	 	 	              

Presence URI


            
              watcher_username
            	              string
            	              64
            	default	no	 	 	              

From User


            
              watcher_domain
            	              string
            	              64
            	default	no	 	 	              

From Domain


            
              to_user
            	              string
            	              64
            	default	no	 	 	              

To User


            
              to_domain
            	              string
            	              64
            	default	no	 	 	              

To Domain


            
              event
            	              string
            	              64
            	'presence'	no	 	 	              

Event description


            
              event_id
            	              string
            	              64
            	default	yes	 	 	              

Event ID


            
              to_tag
            	              string
            	              64
            	default	no	 	 	              

TO tag


            
              from_tag
            	              string
            	              64
            	default	no	 	 	              

From tag


            
              callid
            	              string
            	              64
            	default	no	 	 	              

Call ID


            
              local_cseq
            	              int
            	              11
            	default	no	 	 	              

Local cseq


            
              remote_cseq
            	              int
            	              11
            	default	no	 	 	              

Remote cseq


            
              contact
            	              string
            	              255
            	default	no	 	 	              

Contact


            
              record_route
            	              text
            	              not specified
            	default	yes	 	 	              

Record route


            
              expires
            	              int
            	              11
            	default	no	 	 	              

Expires


            
              status
            	              int
            	              11
            	2	no	 	 	              

Status


            
              reason
            	              string
            	              64
            	default	yes	 	 	              

Reason


            
              version
            	              int
            	              11
            	0	no	 	 	              

Version


            
              socket_info
            	              string
            	              64
            	default	no	 	 	              

Socket info


            
              local_contact
            	              string
            	              255
            	default	no	 	 	              

Local contact


            
              sharing_tag
            	              string
            	              32
            	NULL	yes	 	 	              

The name of the tag assigned to this watcher inside the sharing cluster


            

    

Table 28-4. Table "active_watchers" indexes

name	type	links	description
              active_watchers_idx
            	unique	presentity_uri, callid, to_tag, from_tag	              

 


            

    

Table 28-5. Table "watchers"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              presentity_uri
            	              string
            	              255
            	default	no	 	 	              

Presentity Uri


            
              watcher_username
            	              string
            	              64
            	default	no	 	 	              

Watcher User


            
              watcher_domain
            	              string
            	              64
            	default	no	 	 	              

Watcher Domain


            
              event
            	              string
            	              64
            	'presence'	no	 	 	              

Event description


            
              status
            	              int
            	              11
            	default	no	 	 	              

Status


            
              reason
            	              string
            	              64
            	default	yes	 	 	              

Reason


            
              inserted_time
            	              int
            	              11
            	default	no	 	 	              

 


            

    

Table 28-6. Table "watchers" indexes

name	type	links	description
              watcher_idx
            	unique	presentity_uri, watcher_username, watcher_domain, event	              

 


            

    

Table 28-7. Table "xcap"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              username
            	              string
            	              64
            	default	no	 	 	              

User name


            
              domain
            	              string
            	              64
            	default	no	 	 	              

Domain


            
              doc
            	              binary
            	              not specified
            	default	no	 	 	              

doc


            
              doc_type
            	              int
            	              11
            	default	no	 	 	              

Document type


            
              etag
            	              string
            	              64
            	default	no	 	 	              

Document Etag


            
              source
            	              int
            	              11
            	default	no	 	 	              

Entity inserting the record


            
              doc_uri
            	              string
            	              255
            	default	no	 	 	              

Document uri


            
              port
            	              int
            	              11
            	default	no	 	 	              

XCAP server port


            

    

Table 28-8. Table "xcap" indexes

name	type	links	description
              account_doc_type_idx
            	unique	username, domain, doc_type, doc_uri	              

 


            
              source_idx
            	default	source	              

 


            

    

Table 28-9. Table "pua"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              pres_uri
            	              string
            	              255
            	default	no	 	 	              

URI


            
              pres_id
            	              string
            	              255
            	default	no	 	 	              

ID


            
              event
            	              int
            	              11
            	default	no	 	 	              

Event


            
              expires
            	              int
            	              11
            	default	no	 	 	              

Expires


            
              desired_expires
            	              int
            	              11
            	default	no	 	 	              

Desired Expires


            
              flag
            	              int
            	              11
            	default	no	 	 	              

Flags


            
              etag
            	              string
            	              64
            	default	yes	 	 	              

Etag


            
              tuple_id
            	              string
            	              64
            	default	yes	 	 	              

Tuple ID


            
              watcher_uri
            	              string
            	              255
            	default	yes	 	 	              

Watcher URI


            
              to_uri
            	              string
            	              255
            	default	yes	 	 	              

URI


            
              call_id
            	              string
            	              64
            	default	yes	 	 	              

Call ID


            
              to_tag
            	              string
            	              64
            	default	yes	 	 	              

To tag


            
              from_tag
            	              string
            	              64
            	default	yes	 	 	              

From tag


            
              cseq
            	              int
            	              11
            	default	yes	 	 	              

 


            
              record_route
            	              text
            	              not specified
            	default	yes	 	 	              

Record route


            
              contact
            	              string
            	              255
            	default	yes	 	 	              

Contact


            
              remote_contact
            	              string
            	              255
            	default	yes	 	 	              

Remote contact


            
              version
            	              int
            	              11
            	default	yes	 	 	              

 


            
              extra_headers
            	              text
            	              not specified
            	default	yes	 	 	              

Extra Headers


            
              sharing_tag
            	              string
            	              32
            	NULL	yes	 	 	              

The name of the tag assigned to this presentity inside the sharing cluster


            

    

Table 28-10. Table "pua" indexes

name	type	links	description
              del1_idx
            	default	pres_uri, event	              

 


            
              del2_idx
            	default	expires	              

 


            
              update_idx
            	default	pres_uri, pres_id, flag, event	              

 


            

  

Chapter 29. Quality Routing

    

qr_profiles

This table is used by the Quality Routing module to store
		information about the thresholds for warnings and disabling destinations. A profile is
		associated with a drouting rule.
		More information can be found at: https://opensips.org/docs/modules/devel/qrouting.html.
		


  

    

Table 29-1. Table "qr_profiles"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Table primary key
		


            
              profile_name
            	              string
            	              64
            	default	no	 	 	              

 The name of the profile


            
              warn_threshold_asr
            	              double
            	              not specified
            	-1	no	 	 	              

The warning threshold for answer seizure ratio


            
              warn_threshold_ccr
            	              double
            	              not specified
            	-1	no	 	 	              

The warning threshold for call completion ratio


            
              warn_threshold_pdd
            	              double
            	              not specified
            	-1	no	 	 	              

The warning threshold for post dial delay


            
              warn_threshold_ast
            	              double
            	              not specified
            	-1	no	 	 	              

The warning threshold for average setup time


            
              warn_threshold_acd
            	              double
            	              not specified
            	-1	no	 	 	              

The warning threshold for average call duration


            
              crit_threshold_asr
            	              double
            	              not specified
            	-1	no	 	 	              

The critical threshold for answer seizure ratio


            
              crit_threshold_ccr
            	              double
            	              not specified
            	-1	no	 	 	              

The critical threshold for call completion ratio


            
              crit_threshold_pdd
            	              double
            	              not specified
            	-1	no	 	 	              

The critical threshold for post dial delay


            
              crit_threshold_ast
            	              double
            	              not specified
            	-1	no	 	 	              

The critical threshold for average setup time


            
              crit_threshold_acd
            	              double
            	              not specified
            	-1	no	 	 	              

The critical threshold for average call duration


            
              warn_penalty_asr
            	              double
            	              not specified
            	0.5	no	 	 	              

Traffic volume reduction when ASR falls below warn limit


            
              warn_penalty_ccr
            	              double
            	              not specified
            	0.5	no	 	 	              

Traffic volume reduction when CCR falls below warn limit


            
              warn_penalty_pdd
            	              double
            	              not specified
            	0.5	no	 	 	              

Traffic volume reduction when PDD falls below warn limit


            
              warn_penalty_ast
            	              double
            	              not specified
            	0.5	no	 	 	              

Traffic  volume reduction when AST falls below warn limit


            
              warn_penalty_acd
            	              double
            	              not specified
            	0.5	no	 	 	              

Traffic volume reduction when ACD falls below warn limit


            
              crit_penalty_asr
            	              double
            	              not specified
            	0.05	no	 	 	              

Traffic volume reduction when ASR falls below crit limit


            
              crit_penalty_ccr
            	              double
            	              not specified
            	0.05	no	 	 	              

Traffic volume reduction when CCR falls below crit limit


            
              crit_penalty_pdd
            	              double
            	              not specified
            	0.05	no	 	 	              

Traffic volume reduction when PDD falls below crit limit


            
              crit_penalty_ast
            	              double
            	              not specified
            	0.05	no	 	 	              

Traffic  volume reduction when AST falls below crit limit


            
              crit_penalty_acd
            	              double
            	              not specified
            	0.05	no	 	 	              

Traffic volume reduction when ACD falls below crit limit


            

  

Chapter 30. Rate Cacher

    

rc_clients

This table is used by the Rate Cacher module to keep track of the
		clients - the inbound side of the traffic.
		More information can be found at: https://opensips.org/docs/modules/devel/rate_cacher.html.
		

rc_vendors

This table is used by the Rate Cacher module to keep track of the
		vendors - the outbound side of the traffic.
		More information can be found at: https://opensips.org/docs/modules/devel/rate_cacher.html.
		

rc_ratesheets

This table is used by the Rate Cacher module to keep track of the
		ratesheets.
		More information can be found at: https://opensips.org/docs/modules/devel/rate_cacher.html.
		

rc_demo_ratesheet

This table is a demo table to be used by the Rate Cacher module to keep track of the
		prices for the traffic.
		More information can be found at: https://opensips.org/docs/modules/devel/rate_cacher.html.
		


  

    

Table 30-1. Table "rc_clients"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Table primary key, not used by module
		


            
              client_id
            	              string
            	              64
            	default	no	 	 	              

Client unique ID
		


            
              wholesale_rate
            	              unsigned int
            	              11
            	0	no	 	 	              

Wholesale Rate used for this clients


            
              retail_rate
            	              unsigned int
            	              11
            	0	no	 	 	              

Retail Rate used for this client


            

    

Table 30-2. Table "rc_clients" indexes

name	type	links	description
              client_id_idx
            	unique	client_id	              

 


            

    

Table 30-3. Table "rc_vendors"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Table primary key, not used by module
		


            
              vendor_id
            	              string
            	              64
            	default	no	 	 	              

Vendor unique ID 
		


            
              vendor_rate
            	              unsigned int
            	              11
            	0	no	 	 	              

Rate used for this vendor


            

    

Table 30-4. Table "rc_vendors" indexes

name	type	links	description
              vendor_id_idx
            	unique	vendor_id	              

 


            

    

Table 30-5. Table "rc_ratesheets"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Table primary key, used by the module to get the currency and table name
		


            
              ratesheet_table
            	              string
            	              64
            	default	no	 	 	              

Table name for the ratesheet with the above ID 
		


            
              currency
            	              string
            	              64
            	default	no	 	 	              

Currency for the current ratesheet 
		


            

    

Table 30-6. Table "rc_ratesheets" indexes

name	type	links	description
              table_idx
            	unique	ratesheet_table	              

 


            

    

Table 30-7. Table "rc_demo_ratesheet"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Table primary key, not used by module
		


            
              prefix
            	              string
            	              64
            	default	no	 	 	              

Prefix of the currenty entry in the ratesheet 
		


            
              destination
            	              string
            	              128
            	default	no	 	 	              

Plain-Text description of current entry in the ratesheet


            
              price
            	              float
            	              not specified
            	0	no	 	 	              

Price for the current entry


            
              minimum
            	              unsigned int
            	              11
            	0	no	 	 	              

Minimum seconds to bill for this entry


            
              increment
            	              unsigned int
            	              11
            	1	no	 	 	              

Increment to bill for this entry


            

    

Table 30-8. Table "rc_demo_ratesheet" indexes

name	type	links	description
              prefix_idx
            	unique	prefix	              

 


            

  

Chapter 31. Registrant support

    

registrant

Registrant information for the uac_registrant module. More 
		information can be found at: https://opensips.org/docs/modules/devel/uac_registrant.html
		


  

    

Table 31-1. Table "registrant"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              registrar
            	              string
            	              255
            	''	no	 	 	              

URI pointing to the remote registrar.


            
              proxy
            	              string
            	              255
            	NULL	yes	 	 	              

URI pointing to the outbond proxy.


            
              aor
            	              string
            	              255
            	''	no	 	 	              

URI defining the address of record.


            
              third_party_registrant
            	              string
            	              255
            	NULL	yes	 	 	              

URI defining the third party registrant.


            
              username
            	              string
            	              64
            	NULL	yes	 	 	              

Username for authentication.


            
              password
            	              string
            	              64
            	NULL	yes	 	 	              

Password for authentication. If the password
		starts with 0x and is an MD5 hash, then
		it is considered to be the HA1 representation of the hash.
		Otherwise, it is considered to be plain text.


            
              binding_URI
            	              string
            	              255
            	''	no	 	 	              

Contact URI in REGISTER.


            
              binding_params
            	              string
            	              64
            	NULL	yes	 	 	              

Contact params in REGISTER.


            
              expiry
            	              unsigned int
            	              1
            	NULL	yes	 	 	              

Expiration time.


            
              forced_socket
            	              string
            	              64
            	NULL	yes	 	 	              

socket for sending the REGISTER.


            
              cluster_shtag
            	              string
            	              64
            	NULL	yes	 	 	              

A cluster sharing tag (as [tag_name/custer_id]) used to control this registration in clustering scenarios


            
              state
            	              int
            	              not specified
            	0	no	 	 	              

The state of the registrant (0 enabled, 1 disabled)


            

    

Table 31-2. Table "registrant" indexes

name	type	links	description
              registrant_idx
            	unique	aor, binding_URI, registrar	              

 


            

  

Chapter 32. RLS

    

rls_presentity

Table for the RLS module.
        

rls_watchers

Table for RLS module used for storing resource lists subscribe
                 information.
        


  

    

Table 32-1. Table "rls_presentity"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              rlsubs_did
            	              string
            	              255
            	default	no	 	 	              

Resource list subscribe dialog id


            
              resource_uri
            	              string
            	              255
            	default	no	 	 	              

List Uri


            
              content_type
            	              string
            	              255
            	default	no	 	 	              

Content type


            
              presence_state
            	              binary
            	              not specified
            	default	no	 	 	              

 


            
              expires
            	              int
            	              11
            	default	no	 	 	              

Expires


            
              updated
            	              int
            	              11
            	default	no	 	 	              

Update flag


            
              auth_state
            	              int
            	              11
            	default	no	 	 	              

Watcher authorization state


            
              reason
            	              string
            	              64
            	default	no	 	 	              

reason for watcher authorization state


            

    

Table 32-2. Table "rls_presentity" indexes

name	type	links	description
              rls_presentity_idx
            	unique	rlsubs_did, resource_uri	              

 


            
              updated_idx
            	default	updated	              

 


            

    

Table 32-3. Table "rls_watchers"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              presentity_uri
            	              string
            	              255
            	default	no	 	 	              

Presence URI


            
              to_user
            	              string
            	              64
            	default	no	 	 	              

To user


            
              to_domain
            	              string
            	              64
            	default	no	 	 	              

To domain


            
              watcher_username
            	              string
            	              64
            	default	no	 	 	              

From user


            
              watcher_domain
            	              string
            	              64
            	default	no	 	 	              

From domain


            
              event
            	              string
            	              64
            	'presence'	no	 	 	              

Event description


            
              event_id
            	              string
            	              64
            	default	yes	 	 	              

Event ID


            
              to_tag
            	              string
            	              64
            	default	no	 	 	              

To tag


            
              from_tag
            	              string
            	              64
            	default	no	 	 	              

From tag


            
              callid
            	              string
            	              64
            	default	no	 	 	              

Call ID


            
              local_cseq
            	              int
            	              11
            	default	no	 	 	              

Local cseq


            
              remote_cseq
            	              int
            	              11
            	default	no	 	 	              

Remote cseq


            
              contact
            	              string
            	              64
            	default	no	 	 	              

Contact


            
              record_route
            	              text
            	              not specified
            	default	yes	 	 	              

Record route


            
              expires
            	              int
            	              11
            	default	no	 	 	              

Expires


            
              status
            	              int
            	              11
            	2	no	 	 	              

Status


            
              reason
            	              string
            	              64
            	default	no	 	 	              

Reason


            
              version
            	              int
            	              11
            	0	no	 	 	              

Version


            
              socket_info
            	              string
            	              64
            	default	no	 	 	              

Socket info


            
              local_contact
            	              string
            	              255
            	default	no	 	 	              

Local contact


            

    

Table 32-4. Table "rls_watchers" indexes

name	type	links	description
              rls_watcher_idx
            	unique	presentity_uri, callid, to_tag, from_tag	              

 


            

  

Chapter 33. RTPengine

    

rtpengine

This table is used by the RTPEngine module to store
		definitions of socket(s) used to connect to (a set) RTPEngine.
		More information can be found at: https://opensips.org/docs/modules/devel/rtpengine.html.
		


  

    

Table 33-1. Table "rtpengine"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              socket
            	              text
            	              not specified
            	default	no	 	 	              

RTPEngine socket used to send commands.
			Example: "udp:localhost:60000".
		


            
              set_id
            	              unsigned int
            	              10
            	default	no	 	 	              

The ID of the RTPEngine set.


            

  

Chapter 34. RTPProxy

    

rtpproxy_sockets

This table is used by the NAT Helper module to store
		definitions of socket(s) used to connect to (a set) RTPProxy.	
		More information can be found at: https://opensips.org/docs/modules/devel/nathelper.html.
		


  

    

Table 34-1. Table "rtpproxy_sockets"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              rtpproxy_sock
            	              text
            	              not specified
            	default	no	 	 	              

A list of sockets use to connect to a set of RTPProxy.
			Example: "udp:localhost:12221 udp:localhost:12222".
		


            
              set_id
            	              unsigned int
            	              10
            	default	no	 	 	              

The ID of the RTPProxy set.


            

  

Chapter 35. SMPP

    

smpp

			This table is used to provision Short Message Service Center (SMSC)
			information to connect to over the SMPP (Short Message Peer-to-Peer).
			More information can be found at: https://opensips.org/docs/modules/devel/proto_smpp.html.
		


  

    

Table 35-1. Table "smpp"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              name
            	              string
            	              255
            	default	no	 	 	              

An arbitrary name of the SMSC, used to uniquely identify the binding.
		


            
              ip
            	              string
            	              50
            	default	no	 	 	              

The IP address used to connect to the SMSC.


            
              port
            	              unsigned int
            	              5
            	default	no	 	 	              

The port used to connect to the SMSC.


            
              system_id
            	              string
            	              16
            	default	no	 	 	              

The System ID (also called user name) for the gateway
		to use when connecting to the SMPP server.


            
              password
            	              string
            	              9
            	default	no	 	 	              

The password for the gateway to use when connecting to
		the SMPP server.


            
              system_type
            	              string
            	              13
            	''	no	 	 	              

Configures the System Type parameter of the
		the SMPP server.


            
              src_ton
            	              unsigned int
            	              not specified
            	0	no	 	 	              

Specifies the Source TON (Type of Number).


            
              src_npi
            	              unsigned int
            	              not specified
            	0	no	 	 	              

Specifies the Source NPI (Numbering Plan Indicator).


            
              dst_ton
            	              unsigned int
            	              not specified
            	0	no	 	 	              

Specifies the Destination TON (Type of Number).


            
              dst_npi
            	              unsigned int
            	              not specified
            	0	no	 	 	              

Specifies the Destination NPI (Numbering Plan Indicator).


            
              session_type
            	              unsigned int
            	              not specified
            	1	no	 	 	              

Specifies the type of binding: 1 - transciever,
			2 - transmitter, 3 - receiver, 4 - outbind.


            

    

Table 35-2. Table "smpp" indexes

name	type	links	description
              unique_name
            	unique	name	              

 


            

  

Chapter 36. SOCKETS_MGM support

    

sockets

This table is used to store dynamic sockets used by opensips.
		More information can be found at: https://opensips.org/docs/modules/devel/sockets_mgm.html.
		


  

    

Table 36-1. Table "sockets"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              socket
            	              string
            	              128
            	default	no	 	 	              

The definition of the dynamic socket.
			Example: "udp:127.0.0.1:5090".
		


            
              advertised
            	              string
            	              128
            	NULL	yes	 	 	              

The advertised address and port.
			If missing, the sockets itself is advertised in messages.
		


            
              tag
            	              string
            	              128
            	NULL	yes	 	 	              

Optional tag to be used to match this socket.
		


            
              flags
            	              string
            	              128
            	NULL	yes	 	 	              

Optional, comma separated flags assigned to the
		socket. Possible values are anycast, reuse_port, frag.
		


            
              tos
            	              string
            	              32
            	NULL	yes	 	 	              

ToS values to be used for the socket. This can be
		specified as an integer, or one of the following values: IPTOS_LOWDELAY,
		IPTOS_THROUGHPUT, IPTOS_RELIABILITY, IPTOS_MINCOST, IPTOS_LOWCOST.
		


            

  

Chapter 37. Speed dial

    

speed_dial

This table is used by the speeddial module to provide on-server speed dial facilities. More information about the speeddial module can be found at: https://opensips.org/docs/modules/devel/speeddial.html
        


  

    

Table 37-1. Table "speed_dial"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              username
            	              string
            	              64
            	''	no	 	 	              

Username / phone number


            
              domain
            	              string
            	              64
            	''	no	 	 	              

Domain name


            
              sd_username
            	              string
            	              64
            	''	no	 	 	              

Speed dial username


            
              sd_domain
            	              string
            	              64
            	''	no	 	 	              

Speed dial domain


            
              new_uri
            	              string
            	              255
            	''	no	 	 	              

New URI


            
              fname
            	              string
            	              64
            	''	no	 	 	              

First name


            
              lname
            	              string
            	              64
            	''	no	 	 	              

Last name


            
              description
            	              string
            	              64
            	''	no	 	 	              

Description


            

    

Table 37-2. Table "speed_dial" indexes

name	type	links	description
              speed_dial_idx
            	unique	username, domain, sd_domain, sd_username	              

 


            

  

Chapter 38. SQL Operations

    

usr_preferences

This table us used by the SQLops module to implement Attribute Value Pairs (AVP's). More information about the SQLops module can be found at: https://opensips.org/docs/modules/devel/sqlops.html
        


  

    

Table 38-1. Table "usr_preferences"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique ID


            
              uuid
            	              string
            	              64
            	''	no	 	 	              

Unique user ID


            
              username
            	              string
            	              64
            	0	no	 	 	              

Username / phone number


            
              domain
            	              string
            	              64
            	''	no	 	 	              

Domain name


            
              attribute
            	              string
            	              32
            	''	no	 	 	              

AVP attribute


            
              type
            	              int
            	              11
            	0	no	 	 	              

AVP type


            
              value
            	              string
            	              128
            	''	no	 	 	              

AVP value


            
              last_modified
            	              datetime
            	              not specified
            	'1900-01-01 00:00:01'	no	 	 	              

Date and time when this record was last modified.


            

    

Table 38-2. Table "usr_preferences" indexes

name	type	links	description
              ua_idx
            	default	uuid, attribute	              

 


            
              uda_idx
            	default	username, domain, attribute	              

 


            
              value_idx
            	default	value	              

 


            

  

Chapter 39. Version

    

version

 


  

    

Table 39-1. Table "version"

name	type	size	default	null	key	extra attributes	description
              table_name
            	              string
            	              32
            	default	no	 	 	              

 


            
              table_version
            	              unsigned int
            	              not specified
            	0	no	 	 	              

 


            

    

Table 39-2. Table "version" indexes

name	type	links	description
              t_name_idx
            	unique	table_name	              

 


            

  

Chapter 40. TCP_MGM support

    

tcp_mgm

This table is used for defining TCP connection profiles.
        


  

    

Table 40-1. Table "tcp_mgm"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique DB ID


            
              proto
            	              string
            	              8
            	'any'	no	 	 	              

Restrict this profile to a specific OpenSIPS supported protocol.


            
              remote_addr
            	              string
            	              43
            	NULL	yes	 	 	              

Remote network address in "ip[/prefix_length]" format, or the special values NULL or "any", which will both match any remote IPv4 or IPv6 address.


            
              remote_port
            	              unsigned int
            	              not specified
            	0	no	 	 	              

Remote network port.  A value of 0 will match any remote port.


            
              local_addr
            	              string
            	              43
            	NULL	yes	 	 	              

Local network address in "ip[/prefix_length]" format, or the special values NULL or "any", which will both match any of the OpenSIPS network listeners.


            
              local_port
            	              unsigned int
            	              not specified
            	0	no	 	 	              

Local network port.  A value of 0 will match any OpenSIPS listening port.


            
              priority
            	              int
            	              not specified
            	0	no	 	 	              

By default, higher network prefix lengths will match first.  The priority field can be used to override this behavior, with lower priority rules being attempted first.


            
              attrs
            	              string
            	              255
            	NULL	yes	 	 	              

A URI params string with various TCP-connection related flags or properties pertaining to specific OpenSIPS modules or areas of code.


            
              connect_timeout
            	              unsigned int
            	              not specified
            	100	no	 	 	              

Time in milliseconds before an ongoing blocking TCP connect attempt is aborted.  Default: 100 ms.


            
              con_lifetime
            	              unsigned int
            	              not specified
            	120	no	 	 	              

Time in seconds with no READ or WRITE events on a TCP connection before it is destroyed.  Default: 120 s.


            
              msg_read_timeout
            	              unsigned int
            	              not specified
            	4	no	 	 	              

The maximum number of seconds that a complete SIP message is expected to arrive via TCP.  Default: 4 s.


            
              send_threshold
            	              unsigned int
            	              not specified
            	0	no	 	 	              

The maximum number of microseconds that sending a TCP request can take.  Send latencies above this threshold will trigger a logging warning.  A value of 0 disables the check.  Default: 0 us.


            
              no_new_conn
            	              unsigned int
            	              not specified
            	0	no	 	 	              

Set this to 1 in order to instruct OpenSIPS to never open connections to the "remote" side.  This may be useful when there is a NAT firewall in-between, so only remote->local connections are possible.  Default: 0. 


            
              alias_mode
            	              unsigned int
            	              not specified
            	0	no	 	 	              

Controls TCP connection reusage for requests in the opposite direction to the original one.  0 (never reuse), 1 (only reuse if RFC 5923 Via ";alias" is present), 2 (always reuse).  Default: 0.


            
              parallel_read
            	              unsigned int
            	              not specified
            	0	no	 	 	              

Set to 1 to re-balance a TCP connection for reading after a worker processes one packet.  Set to 2 in order to have proto modules re-balance a TCP conn for reading before processing a fully read packet, but only if they have support for this (e.g. proto_tcp).  Default: 0 (lock a connection in a TCP reader process for "tcp_con_lifetime" seconds at a time).


            
              keepalive
            	              unsigned int
            	              not specified
            	1	no	 	 	              

Set to 0 in order to disable TCP keepalives at Operating System level.  Default: 1 (enabled). 


            
              keepcount
            	              unsigned int
            	              not specified
            	9	no	 	 	              

Number of keepalives to send before closing the connection.  Default: 9. 


            
              keepidle
            	              unsigned int
            	              not specified
            	7200	no	 	 	              

Amount of time, in seconds, before OpenSIPS will start to send keepalives if the connection is idle.  Default: 7200. 


            
              keepinterval
            	              unsigned int
            	              not specified
            	75	no	 	 	              

Interval in seconds between successive (failed) keepalive probes.  Default: 75. 


            

  

Chapter 41. TLS_MGM support

    

tls_mgm

This table is used for defining domains.
        


  

    

Table 41-1. Table "tls_mgm"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Unique DB ID


            
              domain
            	              string
            	              64
            	default	no	 	 	              

TLS domain name, uniquely identifies a client or server domain


            
              match_ip_address
            	              string
            	              255
            	NULL	yes	 	 	              

network address in "ip:port" format, or the wildcard value "*", used to match connections with a tls domain


            
              match_sip_domain
            	              string
            	              255
            	NULL	yes	 	 	              

FQDN used to match connections with a tls domain


            
              type
            	              int
            	              1
            	1	no	 	 	              

type of the domain : client domain(1), server domain (2) or both (0); 0 can be used only for default domains when the same specification is desired for both client and server


            
              method
            	              string
            	              16
            	'SSLv23'	yes	 	 	              

SSL method used by a certain domain


            
              verify_cert
            	              int
            	              1
            	1	yes	 	 	              

verify certificate: 0 - no, 1 - yes


            
              require_cert
            	              int
            	              1
            	1	yes	 	 	              

require certificate: 0 - no, 1 - yes


            
              certificate
            	              binary
            	              not specified
            	default	yes	 	 	              

certificate associated with a certain domain


            
              private_key
            	              binary
            	              not specified
            	default	yes	 	 	              

private_key


            
              crl_check_all
            	              int
            	              1
            	0	yes	 	 	              

check all crl: 0 -no, 1 - yes


            
              crl_dir
            	              string
            	              255
            	NULL	yes	 	 	              

crl directory


            
              ca_list
            	              binary
            	              not specified
            	NULL	yes	 	 	              

CA list


            
              ca_dir
            	              string
            	              255
            	NULL	yes	 	 	              

ca directory


            
              cipher_list
            	              string
            	              255
            	NULL	yes	 	 	              

the list of algorithms used for authentication and encryption allowed


            
              dh_params
            	              binary
            	              not specified
            	NULL	yes	 	 	              

specifies the Diffie-Hellmann parameters


            
              ec_curve
            	              string
            	              255
            	NULL	yes	 	 	              

specifies an elliptic curve which should be used for
        ciphers which demand an elliptic curve


            

    

Table 41-2. Table "tls_mgm" indexes

name	type	links	description
              domain_type_idx
            	unique	domain, type	              

 


            

  

Chapter 42. Tracer

    

sip_trace

This table is used to store incoming/outgoing SIP messages in database. More informations can be found in the tracer module documentation at: https://opensips.org/docs/modules/devel/tracer.html.
        


  

    

Table 42-1. Table "sip_trace"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              time_stamp
            	              datetime
            	              not specified
            	'1900-01-01 00:00:01'	no	 	 	              

Recording date


            
              callid
            	              string
            	              255
            	''	no	 	 	              

call ID from SIP message


            
              trace_attrs
            	              string
            	              255
            	NULL	yes	 	 	              

SIP URI of the user being traced


            
              msg
            	              text
            	              not specified
            	default	no	 	 	              

Full SIP message


            
              method
            	              string
            	              32
            	''	no	 	 	              

SIP method name


            
              status
            	              string
            	              255
            	NULL	yes	 	 	              

SIP reply status


            
              from_proto
            	              string
            	              5
            	default	no	 	 	              

Source protocol


            
              from_ip
            	              string
            	              50
            	''	no	 	 	              

Source IP address


            
              from_port
            	              unsigned int
            	              5
            	default	no	 	 	              

Source port


            
              to_proto
            	              string
            	              5
            	default	no	 	 	              

Destination protocol


            
              to_ip
            	              string
            	              50
            	''	no	 	 	              

Destination IP address


            
              to_port
            	              unsigned int
            	              5
            	default	no	 	 	              

Destination port


            
              fromtag
            	              string
            	              64
            	''	no	 	 	              

From tag


            
              direction
            	              string
            	              4
            	''	no	 	 	              

Destination IP address


            

    

Table 42-2. Table "sip_trace" indexes

name	type	links	description
              trace_attrs_idx
            	default	trace_attrs	              

 


            
              date_idx
            	default	time_stamp	              

 


            
              fromip_idx
            	default	from_ip	              

 


            
              callid_idx
            	default	callid	              

 


            

  

Chapter 43. Trie

    

trie_table

This table is used by the Trie module in order to build the trie that it caches
		More information can be found at: https://opensips.org/docs/modules/devel/trie.html.
		

dr_partitions

This table is used by the Trie module to store
		information about the partitions used in the script (url to database and table name).
		More information can be found at: https://opensips.org/docs/modules/devel/trie.html.
		


  

    

Table 43-1. Table "trie_table"

name	type	size	default	null	key	extra attributes	description
              ruleid
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Rule unique ID
		


            
              prefix
            	              string
            	              64
            	default	no	 	 	              

prefix to be cached


            
              attrs
            	              string
            	              255
            	NULL	yes	 	 	              

Generic string describing RULE attributes - this string is
			to be interpreted from the script


            
              priority
            	              int
            	              11
            	1	no	 	 	              

1 if the rule is enabled, 0 if the rule is disabled.


            

    

Table 43-2. Table "dr_partitions"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

Partition unique ID
		


            
              partition_name
            	              string
            	              255
            	default	no	 	 	              

The name of the partition.
		


            
              db_url
            	              string
            	              255
            	default	no	 	 	              

The url to the database containing the tables: dr_rules, dr_groups,
		dr_carriers and dr_gateways


            
              trie_table
            	              string
            	              255
            	default	yes	 	 	              

The name of the trie_rules table in the given database (for the given partition).


            

  

Chapter 44. User and global blacklists

    

userblacklist

This table is used by the userblacklist module for the user specific blacklists. More information is available at: https://opensips.org/docs/modules/devel/userblacklist.html
        

globalblacklist

This table is used by the userblacklist module for the global blacklists. More information is available at: https://opensips.org/docs/modules/devel/userblacklist.html
        


  

    

Table 44-1. Table "userblacklist"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              username
            	              string
            	              64
            	''	no	 	 	              

The user that is used for the blacklist lookup.


            
              domain
            	              string
            	              64
            	''	no	 	 	              

The domain that is used for the blacklist lookup.


            
              prefix
            	              string
            	              64
            	''	no	 	 	              

The prefix that is matched for the blacklist.


            
              whitelist
            	              char
            	              1
            	0	no	 	 	              

Specify if this a blacklist (0) or a whitelist (1) entry.


            

    

Table 44-2. Table "userblacklist" indexes

name	type	links	description
              userblacklist_idx
            	default	username, domain, prefix	              

 


            

    

Table 44-3. Table "globalblacklist"

name	type	size	default	null	key	extra attributes	description
              id
            	              unsigned int
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              prefix
            	              string
            	              64
            	''	no	 	 	              

The prefix that is matched for the blacklist.


            
              whitelist
            	              char
            	              1
            	0	no	 	 	              

Specify if this a blacklist (0) or a whitelist (1) entry.


            
              description
            	              string
            	              255
            	NULL	yes	 	 	              

A comment for the entry.


            

    

Table 44-4. Table "globalblacklist" indexes

name	type	links	description
              globalblacklist_idx
            	default	prefix	              

 


            

  

Chapter 45. User location

    

location

Persistent user location information for the usrloc module. More information can be found at: https://opensips.org/docs/modules/devel/usrloc.html
        


  

    

Table 45-1. Table "location"

name	type	size	default	null	key	extra attributes	description
              contact_id
            	              unsigned long
            	              10
            	default	no	primary	autoincrement	              

unique ID


            
              username
            	              string
            	              64
            	''	no	 	 	              

Username / phone number 


            
              domain
            	              string
            	              64
            	NULL	yes	 	 	              

Domain name


            
              contact
            	              text
            	              not specified
            	default	no	 	 	              

Contact header field value provides a URI whoses meaning depends on the type of request or response it is in.


            
              received
            	              string
            	              255
            	NULL	yes	 	 	              

Received IP:PORT in the format SIP:IP:PORT


            
              path
            	              string
            	              255
            	NULL	yes	 	 	              

Path Header(s) per RFC 3327


            
              expires
            	              unsigned int
            	              10
            	default	no	 	 	              

Unix timestamp when this entry expires.


            
              q
            	              float
            	              10,2
            	1.0	no	 	 	              

Value used for preferential routing.


            
              callid
            	              string
            	              255
            	'Default-Call-ID'	no	 	 	              

Call-ID header field uniquely identifies a particular invitation or all registrations of a particular client.


            
              cseq
            	              int
            	              11
            	13	no	 	 	              

CSeq header field contains a single decimal sequence number and the request method.


            
              last_modified
            	              datetime
            	              not specified
            	'1900-01-01 00:00:01'	no	 	 	              

Date and time when this entry was last modified.


            
              flags
            	              int
            	              11
            	0	no	 	 	              

Flags


            
              cflags
            	              string
            	              255
            	NULL	yes	 	 	              

CFlags


            
              user_agent
            	              string
            	              255
            	''	no	 	 	              

User-Agent header field contains information about the UAC originating the request.


            
              socket
            	              string
            	              64
            	NULL	yes	 	 	              

Socket used to connect to OpenSIPS. For example: UDP:IP:PORT


            
              methods
            	              int
            	              11
            	NULL	yes	 	 	              

Flags that indicate the SIP Methods this contact will accept.


            
              sip_instance
            	              string
            	              255
            	NULL	yes	 	 	              

SIP Instance for this particular contact


            
              kv_store
            	              text
            	              512
            	NULL	yes	 	 	              

Generic Key-Value storage


            
              attr
            	              string
            	              255
            	NULL	yes	 	 	              

Optional information specific to each registration


            

  







Edit | History | Print | Recent Changes | Search
Page last modified on April 19, 2019, at 08:58 AM
