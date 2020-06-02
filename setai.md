# SET command (/A)(integers) #

Evaluate a mathematical expression and assign the result to a variable.

This manual is about the **/A** switch from the [SET](set) command, when using 
integers. For floating point arithmetics, please check [SET 
\(/A\)\(Floats\)](setaf).

## Synopsis ##

    SET [/a | /a[:]i] variable=expression

Evaluate an expression and assign the result to a variable.

The assign operator **=** can be replaced in the synopsis by one of the 
following operators:

* Arithmetic operators :

  * **+=** : Add result to **variable**.

  * **-=** : Substract result to **variable**.

  * **\*=** : Multiply **variable** by the result.

  * **/=** : Divide **variable** by the result.

* Logical operators :

  * **&&=** : Logical and between **variable** and the result.

  * **||=** : Logical or between **variable** and the result.

* Bitwise operators :

  * **&=** : Bitwise and between **variable** and the result.

  * **|=** : Bitwise or between **variable** and the result.

  * **^=** : Bitwise xor between **variable** and the result.

  * **>>=** : Bitwise left shift of **variable** by result bits.

  * **<<=** : Bitwise right shift of **variable** by result bits.

## Operators ##

A mathematical expression is made of operators and operands. Every opperand is 
separated from other opperands by an operator.

Interger arithmetics operators are:

* Arithmetic operators :

  * **\*** : product.

  * **/** : division.

  * **%** : Modulo.

  * **+** : Addition.

  * **-** : Subtraction.

  * **=** : Assignment.

* Bitwise operators:

  * **|** : Bitwise or.

  * **^** : Bitwise xor.

  * **&** : Bitwise and.

  * **>>** : Right shift.

  * **<<** : Left shift.

* Logical operators:

  * **||** : Logical or.

  * **&&** : Logical and.

Operators have the following precedence \(from greatest to lowest\):

* **unary operators**

* **=**

* **\***, **/**, **%**

* **+**, **-**

* **>>**, **<<**

* **&&**, **&**

* **^**

* **||**, **|**

To avoid precedence issue, use the parenthesis **\(** and **\)**.

[Dos9](dos9) also include unary operators. Unary operators should be to the 
left of the opperand it affects. Unary operators provided by **Dos9** are:

* **-** : Negation.

* **~** : Bitwise not.

* **!** : Logical not.

Unary operators have the highest precedence.

## Bases ##

In [Dos9](dos9) mathematical expressions, numbers can be specified in three 
different numeric bases: decimal, octal and hexadecimal. By default, numbers 
are suposed to be decimal, unless it is prefixed by one of the following 
prefix:

* **0x** : Hexadecimal number.

* **0** : Octal number.

## Note ##

This command uses **libinteval**, a parser compiled with **YACC**.

## Compatibility ##

Fully compatible with **cmd.exe**. **&&** and **||** are Dos9 extensions.

Available since version **0.7.1.0**.

## See also ##

[SET command](set), [SET command \(/A\)\(floats\)](setaf), [SETLOCAL 
command](setlocal)

