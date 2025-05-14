Title: openSIPS | Documentation / Core Variables

URL Source: https://www.opensips.org/Documentation/Script-CoreVar-3-6

Markdown Content:
##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Core Variables

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Script-CoreVar-3-5 "Core Variables - 3.5") [3.4](https://www.opensips.org/Documentation/Script-CoreVar-3-4 "Core Variables - 3.4") Older versions: [3.3](https://www.opensips.org/Documentation/Script-CoreVar-3-3 "Core Variables - 3.3") [3.2](https://www.opensips.org/Documentation/Script-CoreVar-3-2 "Core Variables - 3.2") [3.1](https://www.opensips.org/Documentation/Script-CoreVar-3-1 "Core Variables - 3.1") [3.0](https://www.opensips.org/Documentation/Script-CoreVar-3-0 "Core Variables - 3.0") [2.4](https://www.opensips.org/Documentation/Script-CoreVar-2-4 "Core Variables - 2.4") [2.3](https://www.opensips.org/Documentation/Script-CoreVar-2-3 "Core Variables - 2.3") [2.2](https://www.opensips.org/Documentation/Script-CoreVar-2-2 "Core Variables - 2.2") [2.1](https://www.opensips.org/Documentation/Script-CoreVar-2-1 "Core Variables - 2.1") [1.11](https://www.opensips.org/Documentation/Script-CoreVar-1-11 "Core Variables - 1.11") [1.10](https://www.opensips.org/Documentation/Script-CoreVar-1-10 "Core Variables - ver 1.10") [1.9](https://www.opensips.org/Documentation/Script-CoreVar-1-9 "Core Variables - ver 1.9") [1.8](https://www.opensips.org/Documentation/Script-CoreVar-1-8 "Core Variables - ver 1.8") [1.7](https://www.opensips.org/Documentation/Script-CoreVar-1-7 "Core Variables - ver 1.7") [1.6](https://www.opensips.org/Documentation/Script-CoreVar-1-6 "Core Variables - ver 1.6") [1.5](https://www.opensips.org/Documentation/Script-CoreVar-1-5 "Core Variables - ver 1.5") [1.4](https://www.opensips.org/Documentation/Script-CoreVar-1-4 "Core Variables - ver 1.4")

**Core Variables v3.6**

* * *

**Table of Contents** (hide)

1.  1. [Script variables](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc1)
2.  2. [AVP variables](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc2)
3.  3. [Scripting Variables](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc3)
    1.  3.1 [URI in SIP Request's P-Asserted-Identity header - $ai](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc4)
    2.  3.2 [Authentication Digest URI - $adu](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc5)
    3.  3.3 [Authentication realm - $ar](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc6)
    4.  3.4 [Auth username user - $au](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc7)
    5.  3.5 [Auth username domain - $ad](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc8)
    6.  3.6 [Auth nonce - $an](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc9)
    7.  3.7 [Auth response - $auth.resp](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc10)
    8.  3.8 [Auth nonce - $auth.nonce](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc11)
    9.  3.9 [Auth opaque - $auth.opaque](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc12)
    10.  3.10 [Auth algorithm - $auth.alg](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc13)
    11.  3.11 [Auth QOP - $auth.qop](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc14)
    12.  3.12 [Auth nonce count (nc) - $auth.nc](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc15)
    13.  3.13 [Auth whole username - $aU](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc16)
    14.  3.14 [Acc username - $Au](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc17)
    15.  3.15 [Argument options - $argv](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc18)
    16.  3.16 [Branch flags list - $bf](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc19)
    17.  3.17 [Branch - $branch](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc20)
    18.  3.18 [Branch fields - $branch.fields](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc21)
    19.  3.19 [Branch flag - $branch.flag](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc22)
    20.  3.20 [Authorize Challenge Algorithm - $challenge.algorithm](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc23)
    21.  3.21 [Authorize Challenge Realm - $challenge.realm](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc24)
    22.  3.22 [Authorize Challenge Nonce - $challenge.nonce](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc25)
    23.  3.23 [Authorize Challenge Opaque - $challenge.opaque](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc26)
    24.  3.24 [Authorize Challenge QOP - $challenge.qop](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc27)
    25.  3.25 [Authorize Challenge IK - $challenge.ik](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc28)
    26.  3.26 [Authorize Challenge CK - $challenge.ck](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc29)
    27.  3.27 [Call-Id - $ci](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc30)
    28.  3.28 [Content-Length - $cl](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc31)
    29.  3.29 [CSeq number - $cs](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc32)
    30.  3.30 [Contact instance - $ct](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc33)
    31.  3.31 [Fields of a contact instance - $ct.fields](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc34)
    32.  3.32 [Content-Type - $cT](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc35)
    33.  3.33 [Domain of destination URI - $dd](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc36)
    34.  3.34 [Diversion header URI - $di](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc37)
    35.  3.35 [Diversion "privacy" parameter - $dip](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc38)
    36.  3.36 [Diversion "reason" parameter - $dir](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc39)
    37.  3.37 [Port of destination URI - $dp](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc40)
    38.  3.38 [Transport protocol of destination URI - $dP](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc41)
    39.  3.39 [Destination set - $ds](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc42)
    40.  3.40 [Destination URI - $du](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc43)
    41.  3.41 [Error class - $err.class](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc44)
    42.  3.42 [Error level - $err.level](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc45)
    43.  3.43 [Error info - $err.info](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc46)
    44.  3.44 [Error reply code - $err.rcode](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc47)
    45.  3.45 [Error reply reason - $err.rreason](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc48)
    46.  3.46 [From URI domain - $fd](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc49)
    47.  3.47 [From display name - $fn](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc50)
    48.  3.48 [From tag - $ft](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc51)
    49.  3.49 [From URI - $fu](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc52)
    50.  3.50 [From URI username - $fU](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc53)
    51.  3.51 [OpenSIPS Log level - $log\_level](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc54)
    52.  3.52 [SIP message buffer](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc55)
    53.  3.53 [Message Flags - $mf](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc56)
    54.  3.54 [SIP message ID - $mi](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc57)
    55.  3.55 [SIP message length - $ml](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc58)
    56.  3.56 [Message flag - $msg.flag](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc59)
    57.  3.57 [Message is request - $msg.is\_request](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc60)
    58.  3.58 [Message type - $msg.type](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc61)
    59.  3.59 [Domain in SIP Request's original URI - $od](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc62)
    60.  3.60 [Port of SIP request's original URI - $op](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc63)
    61.  3.61 [Transport protocol of SIP request original URI - $oP](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc64)
    62.  3.62 [SIP Request's original URI - $ou](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc65)
    63.  3.63 [Username in SIP Request's original URI - $oU](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc66)
    64.  3.64 [Route parameter - $param](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc67)
    65.  3.65 [Domain in SIP Request's P-Preferred-Identity header URI - $pd](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc68)
    66.  3.66 [Display Name in SIP Request's P-Preferred-Identity header - $pn](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc69)
    67.  3.67 [Process id - $pp](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc70)
    68.  3.68 [User in SIP Request's P-Preferred-Identity header URI - $pU](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc71)
    69.  3.69 [URI in SIP Request's P-Preferred-Identity header - $pu](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc72)
    70.  3.70 [Domain in SIP Request's URI - $rd](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc73)
    71.  3.71 [Body of request/reply - $rb](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc74)
    72.  3.72 [Returned code - $rc](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc75)
    73.  3.73 [Remote-Party-ID header URI - $re](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc76)
    74.  3.74 [Return value - $return](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc77)
    75.  3.75 [SIP request's method - $rm](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc78)
    76.  3.76 [SIP request's port - $rp](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc79)
    77.  3.77 [Transport protocol of SIP request URI - $rP](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc80)
    78.  3.78 [SIP reply's reason - $rr](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc81)
    79.  3.79 [SIP reply's status - $rs](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc82)
    80.  3.80 [Refer-to URI - $rt](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc83)
    81.  3.81 [SIP Request's URI - $ru](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc84)
    82.  3.82 [Username in SIP Request's URI - $rU](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc85)
    83.  3.83 [Q value of the SIP Request's URI - $ru\_q](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc86)
    84.  3.84 [IP source address - $si](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc87)
    85.  3.85 [Socket inbound - $socket\_in](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc88)
    86.  3.86 [Socket outbound - $socket\_out](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc89)
    87.  3.87 [Source port - $sp](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc90)
    88.  3.88 [To URI Domain - $td](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc91)
    89.  3.89 [To display name - $tn](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc92)
    90.  3.90 [To tag - $tt](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc93)
    91.  3.91 [To URI - $tu](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc94)
    92.  3.92 [To URI Username - $tU](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc95)
    93.  3.93 [Formatted date and time - $time](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc96)
    94.  3.94 [Branch index - $T\_branch\_idx](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc97)
    95.  3.95 [String formatted time - $Tf](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc98)
    96.  3.96 [Current unix time stamp in seconds - $Ts](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc99)
    97.  3.97 [Current microseconds of the current second - $Tsm](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc100)
    98.  3.98 [Startup unix time stamp - $TS](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc101)
    99.  3.99 [User agent header - $ua](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc102)
    100.  3.100 [SIP Headers - $hdr](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc103)
    101.  3.101 [Route Name (Full) - $route](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc104)
    102.  3.102 [Route Type - $route.type](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc105)
    103.  3.103 [Route Name - $route.name](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc106)
    104.  3.104 [Current script line and file - $cfg\_line](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc107)
    105.  3.105 [Log level for xlog() - $xlog\_level](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc108)
4.  4. [Escape Sequences](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc109)
    1.  4.1 [Foreground and background colors](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc110)
    2.  4.2 [Examples](https://www.opensips.org/Documentation/Script-CoreVar-3-6#toc111)

**OpenSIPS** provides multiple type of variables to be used in the routing script. The difference between the types of variables comes from (1) the visibility of the variable (when it is visible), (2) what the variable is attached to (where the variable resides), (3) read-write status of the variable (some types of the variables are read-only and (4) how multiple values (for the same variable are handled).

The **OpenSIPS** variables can be easily identified in the script as all their names (or notations) start with the **$** sign.

Syntax:  
The complete syntax for a pseudo variable is:

$(_<context\>_**name**_(subname)\[index\]{transformation}_)

The fields written in green are optional. The fields meaning is:

*   **name**(compulsory) - the pseudo-variable name(type).  
    Ex: pvar, avp, ru, DLG\_status, etc.
*   **subname** - the identifier of a certain pv from the given type.  
    Ex: hdr(From), avp(name).
*   **index** - a pv can store more than one value - it can refer to a list of values. You can access a certain value from the list if you specify its index. You can also specify indexes with negative values, -1 means the last inserted, -2 the value before the previous inserted one.
*   **transformation** - a series of processing actions can be applied on pseudo-variable. You can find the whole list of possible transformations [here](https://www.opensips.org/Documentation/Script-Tran "Script-Tran"). The transformations can be cascaded, using the output of one transformation as the input of another.
*   **context** - the context in which the pseudo0variable will be evaluated. Now there are 2 pv contexts: reply and request. The reply context can be used in the failure route to request for the pseudo-variable to be evaluated in the context of the reply message. The request context can be used if in a reply route is desired for the pv to be evaluated in the context of the corresponding request.

Usage examples:

*   Only **name**: $ru
*   **Name** and _'subname_: $hdr(Contact)
*   **Name** and **index**: $(ct\[0\])
*   **Name**, **subname** and **index**: $(avp(i:10)\[2\])
*   **Context**
    *   $(<request\>ru) from a reply route will get the Request-URI from the request
    *   $(<reply\>hdr(Contact)) context can be used from failure route to access information from the reply

Types of variables:

*   [**script variables**](https://www.opensips.org/Documentation/Script-CoreVar-3-6#varscript) - as the name says, these variables are strictly bound to the script routes. The variables are visible only in the routing blocks - they are not message or transaction related, but they are process related (script variables will be inherited by script routes executed by the same **OpenSIPS** process).  
    Script variables are read write and they can have integer or string values. A script variable can only hold a single value. A new assignment (or write operation) will overwrite the existing value.
*   [**AVP - Attribute Value Pair**](https://www.opensips.org/Documentation/Script-CoreVar-3-6#varavps) - the AVPs are dynamic variables (as name) that can be created - the AVPS are linked to a singular message or transaction (if stateful processing is used). A message or a transaction will initially (when received or created) have an empty list of AVPS attached to it. During the routing script, the script directly or functions called from script may create new AVPS that will automatically attached to the message/transaction. The AVPS will be visible in all routes where any message (reply or request) of the transaction will be processed - branch\_route , failure\_route, onreply\_route (for this last route you need to enable the TM parameter _onreply\_avp\_mode_).  
    AVPs are read write and an existing AVP can be even deleted (removed). An AVP may contain multiple values - a new assignment (or write operation) will add a new value to the AVP; the values are kept in "last added first to be used" order (stack).  
    A special index **append** is defined to allow you to add a new value at the end of the list (at the bottom of the stack) - $(avp(name)\[append\]) = "last value";
*   [**pseudo variables**](https://www.opensips.org/Documentation/Script-CoreVar-3-6#varpv) - pseudo-variables (or PV) provide access to information from the processed SIP message (headers, RURI, transport level info, a.s.o) or from **OpenSIPS** inners (time values, process PID, return code of a function). Depending of what info they provide, the PVs are either bound to the message, either to nothing (global). Most of the PVs are read-only and only several allow write operations. A PV may return several values or only one, depending of the referred info (if can have multiple values or not).  
    Standard PV is read-only and returns a single value (if not otherwise documented).
*   [**escape sequences**](https://www.opensips.org/Documentation/Script-CoreVar-3-6#varesc) - escape sequences used to format the strings; they are actually not variables, but rather formatters.

### 1. Script variables [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#varscript)

**Naming**: \*\*$var(name)\*\*

**Hints**:

1.  if you want to start using a script variable in a route, better initialize it with same value (or reset it), otherwise you may inherit a value from a previous route that was executed by the same process.
2.  script variables are faster than AVPs, as they directly reference a memory location.
3.  the value of script variables persists over a **OpenSIPS** process.
4.  a script variable can only hold one value.

Example of usage:

$var(a) = 2;  # sets the value of variable 'a' to integer '2'
$var(a) = "2";  # sets the value of variable 'a' to string '2'
$var(a) = 3 + (7&(~2)); # arithmetic and bitwise operation
$var(a) = "sip:" + $au + "@" + $fd; # compose a value from authentication username and From URI domain

# using a script variable for tests
if( \[ $var(a) & 4 \] ) {
  xlog("var a has third bit set\\n");
}

Setting a variable to NULL is actually initializing the value to integer '0'. Script variables don't have NULL value.

### 2. AVP variables [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#varavps)

**Naming**: \*\*$avp(name)\*\* or \*\*$(avp(name)\[N\])\*\*

When using the index "N" you can force the AVP to return a certain value (the N-th value). If no index is given, the first value will be returned.

**Hints**:

1.  to enable AVPs in onreply\_route, use "modparam("tm", "onreply\_avp\_mode", 1)"
2.  if multiple values are used for a single AVP, the values are index in revert order than added
3.  AVPs are part of the transaction context, so they will be visible everywhere where the transaction is present.
4.  the value of an AVP can be deleted

Example of usage:

1.  Transaction persistence example

\# enable avps in onreply route
modparam("tm", "onreply\_avp\_mode", 1)
...
route{
...
$avp(tmp) = $Ts ; # store the current time (at request processing)
...
t\_onreply("1");
t\_relay();
...
}

onreply\_route\[1\] {
	if (t\_check\_status("200")) {
		# calculate the setup time
		$var(setup\_time) = $Ts - $avp(tmp);
	}
}

1.  Multiple values example

$avp(17) = "one";
# we have a single value
$avp(17) = "two";
# we have two values ("two","one")
$avp(17) = "three";
# we have three values ("three","two","one")

xlog("accessing values with no index: $avp(17)\\n");
# this will print the first value, which is the last added value -\> "three"

xlog("accessing values with no index: $(avp(17)\[2\])\\n");
# this will print the index 2 value (third one), -\> "one"

# remove the last value of the avp; if there is only one value, the AVP itself will be destroyed
$avp(17) = NULL;

# delete all values and destroy the AVP
avp\_delete("$avp(17)/g");

# delete the value located at a certain index 
$(avp(17)\[1\]) = NULL;

#overwrite the value at a certain index
$(avp(17)\[0\]) = "zero";

The **AVPOPS** module provides a lot of useful functions to operate AVPs (like checking values, pushing values into different other locations, deleting AVPs, etc).

### 3. Scripting Variables [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#varpv)

**Naming**: $name

**Hints**:

1.  the PV tokens can be given as parameters to different script functions and they will be replaced with a value before the execution of the function.
2.  most of PVs are made available by **OpenSIPS** core, but there are also module exporting PV (to make available info specific to that module) - check the modules documentation.

Predefined (provided by core) PVs are listed in alphabetical order.

#### 3.1  URI in SIP Request's P-Asserted-Identity header - $ai [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ai)

**$ai** - reference to URI in request's P-Asserted-Identity header (see RFC 3325)

#### 3.2  Authentication Digest URI - $adu [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#adu)

**$adu** - URI from Authorization or Proxy-Authorization header. This URI is used when calculating the HTTP Digest Response.

#### 3.3  Authentication realm - $ar [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ar)

**$ar** - realm from Authorization or Proxy-Authorization header

#### 3.4  Auth username user - $au [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#au)

**$au** - user part of username from Authorization or Proxy-Authorization header

#### 3.5  Auth username domain - $ad [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ad)

**$ad** - domain part of username from Authorization or Proxy-Authorization header

#### 3.6  Auth nonce - $an [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#an)

**$an** - the nonce from Authorization or Proxy-Authorization header

#### 3.7  Auth response - $auth.resp [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#auth.resp)

**$auth.resp** - the authentication response from Authorization or Proxy-Authorization header

#### 3.8  Auth nonce - $auth.nonce [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#auth.nonce)

**$auth.nonce** - the nonce string from Authorization or Proxy-Authorization header

#### 3.9  Auth opaque - $auth.opaque [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#auth.opaque)

**$auth.opaque** - the opaque string from Authorization or Proxy-Authorization header

#### 3.10  Auth algorithm - $auth.alg [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#auth.alg)

**$auth.alg** - the algorithm string from Authorization or Proxy-Authorization header

#### 3.11  Auth QOP - $auth.qop [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#auth.qop)

**$auth.qop** - the value of qop parameter from Authorization or Proxy-Authorization header

#### 3.12  Auth nonce count (nc) - $auth.nc [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#auth.nc)

**$auth.nc** - the value of nonce count parameter from Authorization or Proxy-Authorization header

#### 3.13  Auth whole username - $aU [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#aU)

**$aU** - whole username from Authorization or Proxy-Authorization header

#### 3.14  Acc username - $Au [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#Au)

**$Au** - username for accounting purposes. It's a selective pseudo variable (inherited from acc module). It returns $au if exits or From username otherwise.

#### 3.15  Argument options - $argv [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#argv)

**$argv** - provides access to command line arguments specified with '-o' option. Examples:

   # for option '-o foo=0'
   xlog("foo is $argv(foo) \\n");

#### 3.16  Branch flags list - $bf [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#bf)

**$bf** - displays a list with the branch flags set for the current SIP request

#### 3.17  Branch - $branch [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#branch)

**$branch** - this variable is used for creating new branches by writing into it the value of a SIP URI. Examples:

   # creates a new branch
   $branch = "sip:new@doamin.org";
   # print its URI
   xlog("last added branch has URI $(branch(uri)\[-1\]) \\n");

#### 3.18  Branch fields - $branch.fields [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#branch.fields)

**$branch()** - this variable provides read/write access to all fields/attributes of an already existing branch (prior created with append\_branch() ). The fields of the branch are:

*   uri - the RURI of the branch (string value)
*   duri - destination URI of the branch (outbound proxy of the branch) (string value)
*   q - q value of the branch (int value)
*   path - the PATH string for this branch (string value)
*   flags - the branch flags of this branch (int value)
*   socket - the local socket to be used for relaying this branch (string value)

The variable accepts also index **$(branch(uri)\[1\])** for accessing a specific branch (multiple branches can be defined at a moment). The index starts from 0 (first branch). If the index is negative, it is considered the n-th branch from the end ( index -1 means the last branch).  
To get all branches, use the \* index - $(branch(uri)\[\*\]).  
Examples:

   # creates the first branch
   append\_branch();
   # creates the second branch
   force\_send\_socket(udp:193.668.1.12:5060);
   $du = "sip:193.668.3.60";
   append\_branch("sip:foo@bar.com","0.5");

   # display branches
   xlog("----- branch 0: $(branch(uri)\[0\]) , $(branch(q)\[0\]), $(branch(duri)\[0\]), $(branch(path)\[0\]), $(branch(flags)\[0\]), $(branch(socket)\[0\]) \\n");
   xlog("----- branch 1: $(branch(uri)\[1\]) , $(branch(q)\[1\]), $(branch(duri)\[1\]), $(branch(path)\[1\]), $(branch(flags)\[1\]), $(branch(socket)\[1\]) \\n");

   # do some changes over the branches
   $branch(uri) = "sip:user@domain.ro";   # set URI for the first branch
   $(branch(q)\[0\]) = 1000;  # set to 1.00 for the first branch
   $(branch(socket)\[1\]) = NULL;  # reset the socket of the second branch
   $branch(duri) = NULL;  # reset the destination URI or the first branch

It is R/W variable (you can assign values to it from routing logic)

#### 3.19  Branch flag - $branch.flag [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#branch.flag)

**$branch.flag(flag\_name)\[\]** - this variable provides read/write access to the value of a single certain branch flag (identified by name). The values accepted for writing are 1 (set) and 0 (unset). The returned values are 1/"true" (set) and 0/"false" (unset). An index is accepted, in order to access the flag for a certain branch. By default the 0 (or current) branch accessed (for more on index, see the the [branch.fields](https://www.opensips.org/Documentation/Script-CoreVar-3-6#branch.fields) variable) - note that "\*" is not accepted.

  setbflag("X");
  xlog("---- flag value is $branch.flag(X) \\n");
  $branch.flag(X) = off;
  xlog("---- flag value is $branch.flag(X) \\n");

#### 3.20  Authorize Challenge Algorithm - $challenge.algorithm [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#challenge.algorithm)

**$challenge.algorithm** - the algorithm value taken from the WWW-Authorize or Proxy-Authorize header.

#### 3.21  Authorize Challenge Realm - $challenge.realm [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#challenge.realm)

**$challenge.realm** - the realm value taken from the WWW-Authorize or Proxy-Authorize header.

#### 3.22  Authorize Challenge Nonce - $challenge.nonce [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#challenge.nonce)

**$challenge.nonce** - the nonce value taken from the WWW-Authorize or Proxy-Authorize header.

#### 3.23  Authorize Challenge Opaque - $challenge.opaque [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#challenge.opaque)

**$challenge.opaque** - the opaque value taken from the WWW-Authorize or Proxy-Authorize header.

#### 3.24  Authorize Challenge QOP - $challenge.qop [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#challenge.qop)

**$challenge.qop** - the qop value taken from the WWW-Authorize or Proxy-Authorize header.

#### 3.25  Authorize Challenge IK - $challenge.ik [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#challenge.ik)

**$challenge.ik** - the ik value taken from the WWW-Authorize or Proxy-Authorize header.

#### 3.26  Authorize Challenge CK - $challenge.ck [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#challenge.ck)

**$challenge.ck** - the ck value taken from the WWW-Authorize or Proxy-Authorize header.

#### 3.27  Call-Id - $ci [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ci)

**$ci** - reference to body of call-id header

#### 3.28  Content-Length - $cl [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#cl)

**$cl** - reference to body of content-length header

#### 3.29  CSeq number - $cs [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#cs)

**$cs** - reference to cseq number from cseq header

#### 3.30  Contact instance - $ct [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ct)

**$ct** - reference to contact instance/body from the contact header. A contact instance is display\_name + URI + contact\_params. As a Contact header may contain multiple Contact instances and a message may contain multiple Contact headers, an index was added to the $ct variable:

*   $ct -first contact instance from message
*   $(ct\[n\]) - the n-th contact instance form the beginning of message, starting with index 0
*   $(ct\[-n\]) - the n-th contact instance form the end of the message, starting with index -1 (the last contact instance)

#### 3.31  Fields of a contact instance - $ct.fields [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ct.fields)

**$ct.fields()** - reference to the fields of a contact instance/body (see above). Supported fields are:

*   name - display name
*   uri - contact uri
*   q - q param (value only)
*   expires - expires param (value only)
*   methods - methods param (value only)
*   received - received param (value only)
*   params - all params (including names)

Examples:

*   $ct.fields(uri) - the URI of the first contact instance
*   $(ct.fields(name)\[1\]) - the display name of the second contact instance

#### 3.32  Content-Type - $cT [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#cT)

**$cT** - reference to body of Content-Type header and also the content-type headers inside a multi-part body

*   $cT - the main Content-Type of the message; the one inside the headers
*   $(cT\[n\]) - the **n**\-th Content-Type inside a multi-part body from the beginning of message, starting with index 0
*   $(cT\[-n\]) - the **n**\-th Content-Type inside a multi-part body from the end of the message, starting with index -1 (the last contact instance)
*   $(cT\[\*\]) - all the Content-Type headers including the main one and the ones from the multi-part body

#### 3.33  Domain of destination URI - $dd [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#dd)

**$dd** - reference to domain of destination uri

It is R/W variable (you can assign values to it from routing logic)

#### 3.34  Diversion header URI - $di [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#di)

**$di** - reference to Diversion header URI

#### 3.35  Diversion "privacy" parameter - $dip [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#dip)

**$dip** - reference to Diversion header "privacy" parameter value

#### 3.36  Diversion "reason" parameter - $dir [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#dir)

**$dir** - reference to Diversion header "reason" parameter value

#### 3.37  Port of destination URI - $dp [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#dp)

**$dp** - reference to port of destination uri

It is R/W variable (you can assign values to it from routing logic)

#### 3.38  Transport protocol of destination URI - $dP [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#dP)

**$dP** - reference to transport protocol of destination uri

#### 3.39  Destination set - $ds [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ds)

**$ds** - reference to destination set

#### 3.40  Destination URI - $du [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#du)

**$du** - reference to destination uri (outbound proxy to be used for sending the request) If loose\_route() returns TRUE a destination uri is set according to the first Route header.

It is R/W variable (you can assign values to it from routing logic)

#### 3.41  Error class - $err.class [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#err.class)

**$err.class** - the class of error (now is '1' for parsing errors)

#### 3.42  Error level - $err.level [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#err.level)

**$err.level** - severity level for the error

#### 3.43  Error info - $err.info [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#err.info)

**$err.info** - text describing the error

#### 3.44  Error reply code - $err.rcode [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#err.rcode)

**$err.rcode** - recommended reply code

#### 3.45  Error reply reason - $err.rreason [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#err.rreason)

**$err.rreason** - recommended reply reason phrase

#### 3.46  From URI domain - $fd [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#fd)

**$fd** - reference to domain in URI of 'From' header

#### 3.47  From display name - $fn [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#fn)

**$fn** - reference to display name of 'From' header

#### 3.48  From tag - $ft [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ft)

**$ft** - reference to tag parameter of 'From' header

#### 3.49  From URI - $fu [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#fu)

**$fu** - reference to URI of 'From' header

#### 3.50  From URI username - $fU [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#fU)

**$fU** - reference to username in URI of 'From' header

#### 3.51  OpenSIPS Log level - $log\_level [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#log_level)

**$log\_level** - changes the log level for the current process ; the log level can be set to a new value (see [possible values](https://www.opensips.org/Documentation/Script-CoreParameters-3-6#log_level "Core Parameters - 3.6") or it can be reset back to the global log level. This function is very helpful if you are tracing and debugging only a specific piece of code.

Example of usage:

    log\_level= -1 # errors only
    .....
    {
      ......
      $log\_level = 4; # set the debug level of the current process to DBG
      uac\_replace\_from(....);
      $log\_level = NULL; # reset the log level of the current process to its default level
      .......
    }

#### 3.52 SIP message buffer

**$mb** - reference to SIP message buffer

#### 3.53  Message Flags - $mf [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#mf)

**$mf** - displays a list with the message/transaction flags set for the current SIP request

#### 3.54  SIP message ID - $mi [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#mi)

**$mi** - reference to SIP message id

#### 3.55  SIP message length - $ml [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ml)

**$ml** - reference to SIP message length

#### 3.56  Message flag - $msg.flag [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#msg.flag)

**$msg.flag(flag\_name)** - this variable provides read/write access to the value of a single certain message flag (identified by name). The values accepted for writing are 1 (set) and 0 (unset). The returned values are 1/"true" (set) and 0/"false" (unset).

  setflag("X");
  xlog("---- flag value is $msg.flag(X) \\n");
  $msg.flag(X) = off;
  xlog("---- flag value is $msg.flag(X) \\n");

#### 3.57  Message is request - $msg.is\_request [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#msg.is_request)

**$msg.is\_request** - this variable tells if the current SIP message is a request or not. The returned values are 1/"true" (request) and 0/"false" (reply).

  xlog("---- this message is a request:  $msg.is\_request \\n");
  if ( $msg.is\_request )
    xlog("---- yes, it is a request\\n");

#### 3.58  Message type - $msg.type [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#msg.type)

**$msg.type** - this variable returns the type of the current message. The returned values are "request" (request) or "reply" (reply).

  xlog("---- this message is a SIP $msg.type \\n");

#### 3.59  Domain in SIP Request's original URI - $od [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#od)

**$od** - reference to domain in request's original R-URI

#### 3.60  Port of SIP request's original URI - $op [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#op)

**$op** - reference to port of original R-URI

#### 3.61  Transport protocol of SIP request original URI - $oP [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#oP)

**$oP** - reference to transport protocol of original R-URI

#### 3.62  SIP Request's original URI - $ou [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ou)

**$ou** - reference to request's original URI

#### 3.63  Username in SIP Request's original URI - $oU [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#oU)

**$oU** - reference to username in request's original URI

#### 3.64  Route parameter - $param [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#param)

**$param(idx)** - retrieves the parameters of the route. The index can be an integer, or a pseudo-variable (index starts at 1).  
Example:

   route {
      ...
      $var(debug) = "DBUG:"
      route(PRINT\_VAR, $var(debug), "param value");
      ...
   }

   route\[PRINT\_VAR\] {
      $var(index) = 2;
      xlog("$param(1): The parameter value is <$param($var(index))\>\\n");
   }

#### 3.65  Domain in SIP Request's P-Preferred-Identity header URI - $pd [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#pd)

**$pd** - reference to domain in request's P-Preferred-Identity header URI (see RFC 3325)

#### 3.66  Display Name in SIP Request's P-Preferred-Identity header - $pn [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#pn)

**$pn** - reference to Display Name in request's P-Preferred-Identity header (see RFC 3325)

#### 3.67  Process id - $pp [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#pp)

**$pp** - reference to process id (pid)

#### 3.68  User in SIP Request's P-Preferred-Identity header URI - $pU [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#pU)

**$pU** - reference to user in request's P-Preferred-Identity header URI (see RFC 3325)

#### 3.69  URI in SIP Request's P-Preferred-Identity header - $pu [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#pu)

**$pu** - reference to URI in request's P-Preferred-Identity header (see RFC 3325)

#### 3.70  Domain in SIP Request's URI - $rd [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#rd)

**$rd** - reference to domain in request's URI

It is R/W variable (you can assign values to it routing script)

#### 3.71  Body of request/reply - $rb [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#rb)

**$rb** - reference to the body or a body part of the SIP message

*   $rb - the whole body of the message (with all the parts)
*   $(rb\[\*\]) - same as $rb
*   $(rb\[n\]) - the n-th body belonging to a multi-part body from the beginning of message, starting with index 0
*   $(rb\[-n\]) - the n-th body belonging to a multi-part body from the end of the message, starting with index -1 (the last contact instance)
*   $rb(application/sdp) - get the first SDP body part
*   $(rb(application/isup)\[-1\]) - get the last ISUP body part

#### 3.72  Returned code - $rc [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#rc)

**$rc** - reference to returned code by last invoked function

**$retcode** - same as \*\*$rc\*\*

#### 3.73  Remote-Party-ID header URI - $re [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#re)

**$re** - reference to Remote-Party-ID header URI

#### 3.74  Return value - $return [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#return)

**$return** - Returns the value of the previously executed route.

The variable receives an index, starting with 0, indicating the return value that needs to be read.

#### 3.75  SIP request's method - $rm [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#rm)

**$rm** - reference to request's method

#### 3.76  SIP request's port - $rp [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#rp)

**$rp** - reference to port of R-URI

It is R/W variable (you can assign values to it routing script)

#### 3.77  Transport protocol of SIP request URI - $rP [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#rP)

**$rP** - reference to transport protocol of R-URI

#### 3.78  SIP reply's reason - $rr [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#rr)

**$rr** - reference to reply's reason

#### 3.79  SIP reply's status - $rs [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#rs)

**$rs** - reference to reply's status

#### 3.80  Refer-to URI - $rt [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#rt)

**$rt** - reference to URI of refer-to header

#### 3.81  SIP Request's URI - $ru [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ru)

**$ru** - reference to request's URI

It is R/W variable (you can assign values to it routing script)

#### 3.82  Username in SIP Request's URI - $rU [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#rU)

**$rU** - reference to username in request's URI

It is R/W variable (you can assign values to it routing script)

#### 3.83  Q value of the SIP Request's URI - $ru\_q [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ru_q)

**$ru\_q** - reference to q value of the R-URI

It is R/W variable (you can assign values to it routing script)

#### 3.84  IP source address - $si [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#si)

**$si** - reference to IP source address of the message

#### 3.85  Socket inbound - $socket\_in [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#socket_in)

**$socket\_in** - read-only variable to get the description (proto:ip:port format) of the inbound socket (used for receiving the message).  
The variable also offers detailed read-only access to various attributes/sub-fields of the socket, as **$socket\_in()**. The sub-fields of the socket are:

*   ip - the IP part of the socket
*   port - the port part of the socket
*   proto - the name of the protocol of the socket (as "UDP", "TPC", etc)
*   advertised\_ip - the advertised IP part of the socket (it may be NULL if no advertising is done on this particlar socket)
*   advertised\_port - the advertised part part of the socket (it may be NULL if no advertising is done on this particlar socket)
*   tag - the socket internal tag/alias
*   anycast - if the socket uses an anycast IP or not (returns 0 if not, 1 if yes)
*   af - the address family of the socket's IP. It's value is "INET" if IPv4 or "INET6" if IPv6.

For more details on the meaning of these sub-fields, please also read about the [socket definition](https://www.opensips.org/Documentation/Script-CoreParameters-3-6#toc66 "Core Parameters - 3.6").

#### 3.86  Socket outbound - $socket\_out [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#socket_out)

**$socket\_out** - read-write variable for reading or changing the outbound socket of the message. Originally (before being written/changed) it will return the same socket description as [$socket\_in](https://www.opensips.org/Documentation/Script-CoreVar-3-6#socket_in) (the inbound socket will be used as outbound socket also). In addition, it also supports the `forced` sub-field, which returns a socket description only if a socket had been explicitly forced; thus, as opposed to the regular [$socket\_out](https://www.opensips.org/Documentation/Script-CoreVar-3-6#socket_ou), if no socket had explicitly been forced, the variable returns NULL.

The variable also offers detailed read-only access to various attributes/sub-fields of the socket, as $socket\_out()'''. It provides the same sub-fields as the [$socket\_in](https://www.opensips.org/Documentation/Script-CoreVar-3-6#socket_in) variable.

   $socket\_out = "udp:11.11.11.11:5060";
   xlog("The outbound port is $socket\_out(port)\\n");

#### 3.87  Source port - $sp [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#sp)

**$sp** - reference to the source port of the message

#### 3.88  To URI Domain - $td [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#td)

**$td** - reference to domain in URI of 'To' header

#### 3.89  To display name - $tn [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#tn)

**$tn** - reference to display name of 'To' header

#### 3.90  To tag - $tt [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#tt)

**$tt** - reference to tag parameter of 'To' header

#### 3.91  To URI - $tu [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#tu)

**$tu** - reference to URI of 'To' header

#### 3.92  To URI Username - $tU [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#tU)

**$tU** - reference to username in URI of 'To' header

#### 3.93  Formatted date and time - $time [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#time)

**$time(format)** - returns the string formatted time according to UNIX date (see: **man date**).

#### 3.94  Branch index - $T\_branch\_idx [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#T_branch_idx)

**$T\_branch\_idx** - the index (starting with 1 for the first branch) of the branch for which is executed the branch\_route\[\]. If used outside of branch\_route\[\] block, the value is '0'. This is exported by TM module.

#### 3.95  String formatted time - $Tf [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#Tf)

**$Tf** - reference string formatted time

#### 3.96  Current unix time stamp in seconds - $Ts [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#Ts)

**$Ts** - reference to current unix time stamp in seconds

#### 3.97  Current microseconds of the current second - $Tsm [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#Tsm)

**$Tsm** - reference to current microseconds of the current second

#### 3.98  Startup unix time stamp - $TS [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#TS)

**$TS** - reference to startup unix time stamp

#### 3.99  User agent header - $ua [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#ua)

**$ua** - reference to user agent header field

#### 3.100  SIP Headers - $hdr [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#hdr)

**$(hdr(name)\[N\])** - represents the body of the N-th header identified by 'name'. If \[N\] is omitted then the body of the first header is printed. The first header is got when N=0, for the second N=1, a.s.o. To print the last header of that type, use -1, no other negative values are supported now. No white spaces are allowed inside the specifier (before }, before or after {, \[, \] symbols). When N='\*', all headers of that type are printed.

The module should identify most of compact header names (the ones recognized by **OpenSIPS** which should be all at this moment), if not, the compact form has to be specified explicitly. It is recommended to use dedicated specifiers for headers (e.g., %ua for user agent header), if they are available -- they are faster.

**$(hdr\_name\[N\])** - returns the name of the N-th header. The first header name is obtained for N=0, the second for N=1, a.s.o. To print the last header name use -1, the second last -2 a.s.o. No white spaces are allowed inside the specifier (before }, before or after {, \[, \] symbols). When N='\*', all header names are printed.

**$(hdrcnt(name))** -- returns number of headers of type given by 'name'. Uses same rules for specifying header names as **$hdr(name)** above. Many headers (e.g., Via, Path, Record-Route) may appear more than once in the message. This variable returns the number of headers of a given type.

Note that some headers (e.g., Path) may be joined together with commas and appear as a single header line. This variable counts the number of header lines, not header values.

For message fragment below, **$hdrcnt(Path)** will have value 2 and **$(hdr(Path)\[0\])** will have value **<a.com\>**:

    Path: <a.com\>
    Path: <b.com\>

For message fragment below, **$hdrcnt(Path)** will have value 1 and **$(hdr(Path)\[0\])** will have value **<a.com\>,<b.com\>**:

    Path: <a.com\>,<b.com\>

Note that both examples above are semantically equivalent but the variables take on different values.

#### 3.101  Route Name (Full) - $route [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#route)

**$route** - Access route names of the current route call stack. Usage examples (assuming a route call stack of "route \> route\[A\] \> route\[B\]"):

*   **$route** and **$(route\[0\])** both return **"route\[B\]"** (current route)
*   **$(route\[1\])** returns **"route\[A\]"** (parent route)
*   **$(route\[2\])** returns **"route"** (previous-parent route)
*   **$(route\[-1\])** returns **"route"** (topmost route)
*   **$(route\[-2\])** returns **"route\[A\]"** (next-topmost route)
*   **$(route\[-3\])** returns **"route\[B\]"** (next-next-topmost route)
*   **$(route\[3\])** and **$(route\[-4\])** both return **NULL** (index out of bounds)
*   **$(route\[\*\])** returns **"route \> route\[A\] \> route\[B\]"** (entire call stack)

#### 3.102  Route Type - $route.type [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#route.type)

**$route.type** - Access the type of the current route. May be indexed, using positive or negative indexes.

*   **$route.type** and **$(route.type\[0\])** both return current route type
*   **$(route.type\[1\])** returns parent route type
*   **$(route.type\[-1\])** returns topmost route type
*   **$(route.type\[-2\])** returns next-topmost route type

#### 3.103  Route Name - $route.name [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#route.name)

**$route.name** - Access the name of the current route. May be indexed, using positive or negative indexes.

*   **$route.name** and **$(route.name\[0\])** both return current route name
*   **$(route.name\[1\])** returns parent route name
*   **$(route.name\[-1\])** returns topmost route name
*   **$(route.name\[-2\])** returns next-topmost route name

#### 3.104  Current script line and file - $cfg\_line [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#cfg_line)

**$cfg\_line** - Holds the current line from the script of the action being executed, useful for logging purposes  
**$cfg\_file** - Holds the current name of the cfg file being executed, useful when using multiple scripts via the include statement

#### 3.105  Log level for xlog() - $xlog\_level [🔗](https://www.opensips.org/Documentation/Script-CoreVar-3-6#xlog_level)

**$xlog\_level** - allows to set /reset the xlog() logging level on per-process bases. Shortly said, you can read the verbosity level for the xlog() calls or you can temporary change the level per process bases.

Example:

xlog("current verbosity is $xlog\_level \\n");
$xlog\_level = L\_DBG; # force local xlogging limit to DBG
...
(set of xlogs)
...
$xlog\_level = NULL;  # reset to initial value

### 4. Escape Sequences

These sequences are exported, and mainly used, by xlog module to print messages in many colors (foreground and background) using escape sequences.

#### 4.1 Foreground and background colors

$C(xy) - reference to an escape sequence. ¿x¿ represents the foreground color and ¿y¿ represents the background color.

Colors could be:

*   x : default color of the terminal
*   s : Black
*   r : Red
*   g : Green
*   y : Yellow
*   b : Blue
*   p : Purple
*   c : Cyan
*   w : White

#### 4.2 Examples

A few examples of usage.

...
route {
...
    $avp(uuid)="caller\_id";
    $avp(tmp)= $avp(uuid) + ": " + $fu;
    xlog("$C(bg)$avp(tmp)$C(xx) \[$avp(tmp)\] $C(br)$cs$C(xx)=\[$hdr(cseq)\]\\n");
...
}
...
