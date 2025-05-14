Title: openSIPS | Documentation / Script Statements

URL Source: https://www.opensips.org/Documentation/Script-Statements-3-6

Markdown Content:
##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Script Statements

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Script-Statements-3-5 "Script Statements - 3.5") [3.4](https://www.opensips.org/Documentation/Script-Statements-3-4 "Script Statements - 3.4") Older versions: [3.3](https://www.opensips.org/Documentation/Script-Statements-3-3 "Script Statements - 3.3") [3.2](https://www.opensips.org/Documentation/Script-Statements-3-2 "Script Statements - 3.2") [3.1](https://www.opensips.org/Documentation/Script-Statements-3-1 "Script Statements - 3.1") [3.0](https://www.opensips.org/Documentation/Script-Statements-3-0 "Script Statements - 3.0") [2.4](https://www.opensips.org/Documentation/Script-Statements-2-4 "Script Statements - 2.4") [2.3](https://www.opensips.org/Documentation/Script-Statements-2-3 "Script Statements - 2.3") [2.2](https://www.opensips.org/Documentation/Script-Statements-2-2 "Script Statements - 2.2") [2.1](https://www.opensips.org/Documentation/Script-Statements-2-1 "Script Statements - devel") [1.11](https://www.opensips.org/Documentation/Script-Statements-1-11 "Script Statements - 1.11") [1.10](https://www.opensips.org/Documentation/Script-Statements-1-10 "Script Statements - ver 1.10") [1.9](https://www.opensips.org/Documentation/Script-Statements-1-9 "Script Statements - ver 1.9") [1.8](https://www.opensips.org/Documentation/Script-Statements-1-8 "Script Statements - ver 1.8") [1.7](https://www.opensips.org/Documentation/Script-Statements-1-7 "Script Statements - ver 1.7") [1.6](https://www.opensips.org/Documentation/Script-Statements-1-6 "Script Statements - ver 1.6") [1.5](https://www.opensips.org/Documentation/Script-Statements-1-5 "Script Statements - ver 1.5") [1.4](https://www.opensips.org/Documentation/Script-Statements-1-4 "Script Statements - ver 1.4")

**Script Statements v3.6**

* * *

**Table of Content** (hide)

1.  1. [if](https://www.opensips.org/Documentation/Script-Statements-3-6#toc1)
2.  2. [switch](https://www.opensips.org/Documentation/Script-Statements-3-6#toc2)
3.  3. [while](https://www.opensips.org/Documentation/Script-Statements-3-6#toc3)
4.  4. [for each](https://www.opensips.org/Documentation/Script-Statements-3-6#toc4)

Statements you can use in the **OpenSIPS** config file while building the routing logic.

#### 1. if [🔗](https://www.opensips.org/Documentation/Script-Statements-3-6#if)

IF-ELSE statement

Prototype:

    if (expr) {
       actions;
    } else {
       actions;
    }

The 'expr' should be a valid logical expression.

The logical operators that can be used in the logical expressions:

*   \== - equal
*   != - not equal
*   \=~ - regular expression matching (e.g. $rU =~ '^1800\*' is "$rU begins with 1800" )
*   !~ - regular expression not-matching
*   \> - greater
*   \>\= - greater or equal
*   < - less
*   <\= - less or equal
*   && - logical AND
*   || - logical OR
*   ! - logical NOT
*   \[ ... \] - test operator - inside can be any arithmetic expression

Example of usage:

    if ( is\_method("INVITE") && $rp==5060 )
    {
        log("this sip message is an invite\\n");
    } else {
        log("this sip message is not an invite\\n");
    }

#### 2. switch [🔗](https://www.opensips.org/Documentation/Script-Statements-3-6#switch)

SWITCH statement - it can be used to test the value of a pseudo-variable.

IMPORTANT NOTE: 'break' can be used only to mark the end of a 'case' branch (as it is in shell scripts). If you are trying to use 'break' outside a 'case' block the script will return error -- you must use 'return' there.

Example of usage:

    route {
        route(my\_logic);
        switch ($retcode) {
        case -1:
            log("process INVITE requests here\\n");
            break;
        case 1:
            log("process REGISTER requests here\\n");
            break;
        case 2:
        case 3:
            log("process SUBSCRIBE and NOTIFY requests here\\n");
            break;
        default:
            log("process other requests here\\n");
       }

        # switch of R-URI username
        switch ($rU) {
        case "101":
            log("destination number is 101\\n");
            break;
        case "102":
            log("destination number is 102\\n"); # continue with 103 and 104
        case "103":
        case "104":
            log("destination number is 103 or 104\\n");
            break;
        default:
            log("unknown destination number\\n");
       }
    }

    route \[my\_logic\] {
        if (is\_method("INVITE"))
            return(-1);

        if (is\_method("REGISTER"))
            return(1);

        if (is\_method("SUBSCRIBE"))
            return(2);

        if (is\_method("NOTIFY"))
            return(3);

        return(-2);
    }

Take care while using 'return' - 'return(0)' stops the execution of the script.

#### 3. while [🔗](https://www.opensips.org/Documentation/Script-Statements-3-6#while)

while statement

Example of usage:

    $var(i) = 0;
    $var(cli) = NULL;
    while ($var(i) < 10) {
        if ($(avp(valid\_clis\[$var(i)\]) == $fU) {
            xlog("matched the From user!\\n");
            $var(cli) = $fU;
            break;
        }
        $var(i) = $var(i) + 1;
    }

[#for each](https://www.opensips.org/Documentation/Script-Statements-3-6#foreach)

#### 4. for each [🔗](https://www.opensips.org/Documentation/Script-Statements-3-6#foreach)

for each statement - easy iteration over indexed variables or pseudo-variables

Example of usage:

    $avp(arr) = 0;
    $avp(arr) = 1;
    $avp(arr) = 2;
    $avp(arr) = 3;
    $avp(arr) = 4;

    for ($var(it) in $(avp(arr)\[\*\]))
        xlog("array value: $var(it)\\n");

    # iterate through all Contact URIs from each Contact header
    for ($var(ct) in $(ct\[\*\]))
        xlog("Contact: $var(ct)\\n");

    # iterate through all Via headers of a SIP request
    for ($var(via) in $(hdr(Via)\[\*\]))
        xlog("Found \\"Via\\" header: $var(via)\\n");

    # iterate through all JSON documents returned by a MongoDB query
    cache\_raw\_query("mongodb:location", "{... find ...}", "$avp(res)");
    for ($json(contact) in $(avp(res)\[\*\])) {
        xlog("Found: $json(contact/phone) $json(contact/email)\\n");

        if ($json(contact/phone) =~ "^40") {
            xlog("found a cheap destination to dial\\n");
            break;
        }
    }
