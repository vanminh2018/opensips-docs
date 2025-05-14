Title: openSIPS | Documentation / Script Operators

URL Source: https://www.opensips.org/Documentation/Script-Operators-3-6

Markdown Content:
##### Documentation -\> [Manuals](https://www.opensips.org/Documentation/Manuals "Manuals") -\> [Manual devel](https://www.opensips.org/Documentation/Manual-3-6 "OpenSIPS Manual - 3.6") -\> Script Operators

* * *

Pages for other versions: devel [3.5](https://www.opensips.org/Documentation/Script-Operators-3-5 "Script Operators - devel") [3.4](https://www.opensips.org/Documentation/Script-Operators-3-4 "Script Operators - devel") Older versions: [3.3](https://www.opensips.org/Documentation/Script-Operators-3-3 "Script Operators - devel") [3.2](https://www.opensips.org/Documentation/Script-Operators-3-2 "Script Operators - devel") [3.1](https://www.opensips.org/Documentation/Script-Operators-3-1 "Script Operators - devel") [3.0](https://www.opensips.org/Documentation/Script-Operators-3-0 "Script Operators - devel") [2.4](https://www.opensips.org/Documentation/Script-Operators-2-4 "Script Operators - devel") [2.3](https://www.opensips.org/Documentation/Script-Operators-2-3 "Script Operators - devel") [2.2](https://www.opensips.org/Documentation/Script-Operators-2-2 "Script Operators - 2.2") [2.1](https://www.opensips.org/Documentation/Script-Operators-2-1 "Script Operators - devel") [1.11](https://www.opensips.org/Documentation/Script-Operators-1-11 "Script Operators - 1.11") [1.10](https://www.opensips.org/Documentation/Script-Operators-1-10 "Script Operators - ver 1.10") [1.9](https://www.opensips.org/Documentation/Script-Operators-1-9 "Script Operators - ver 1.9") [1.8](https://www.opensips.org/Documentation/Script-Operators-1-8 "Script Operators - ver 1.8") [1.7](https://www.opensips.org/Documentation/Script-Operators-1-7 "Script Operators - ver 1.7") [1.6](https://www.opensips.org/Documentation/Script-Operators-1-6 "Script Operators - ver 1.6") [1.5](https://www.opensips.org/Documentation/Script-Operators-1-5 "Script Operators - ver 1.5") [1.4](https://www.opensips.org/Documentation/Script-Operators-1-4 "Script Operators - ver 1.4")

**Script Operators v3.6**

* * *

Assignments, string and arithmetic operations can be done directly in the configuration file.

#### 1. Assignment

Assignments can be done like in C, via '=' (equal) operator. Not that not all variables (from script) can be written, some are read-only. Check with [listing of variables](https://www.opensips.org/Documentation/Script-CoreVar-3-6 "Core Variables - 3.6") to see which ones can be written too.

$var(a) = 123;
$ru = "sip:user@domain";

There is a special assign operator ':=' (colon equal) that can be used with AVPs. If the right value is **null**, all AVPs with that name are deleted. If different, the new value will overwrite any existing values for the AVPs with than name (on other words, delete existing AVPs with same name, add a new one with the right side value).

$avp(val) := 123;

#### 2. String operations

For strings, '+' is available to concatenate.

$var(a) = "test";
$var(b) = "sip:" + $var(a) + "@" + $fd;

#### 3. Arithmetic and bitwise operations

For numbers, one can use:

*   \+ : plus
*   \- : minus
*   / : divide
*   \* : multiply
*   % : modulo
*   | : bitwise OR
*   & : bitwise AND
*   ^ : bitwise XOR
*   ~ : bitwise NOT
*   << : bitwise left shift
*   \>\> : bitwise right shift

Example:

$var(a) = 4 + ( 7 & ( ~2 ) );

NOTE: to ensure the priority of operands in expression evaluations do use \_\_parenthesis\_\_.

Arithmetic expressions can be used in condition expressions via test operator ' \[ ... \] '.

if( \[ $var(a) & 4 \] )
    log("var a has third bit set\\n");
