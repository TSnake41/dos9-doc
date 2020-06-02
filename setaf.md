# SET (/A) Command (floating point) #

The **SET /A** commande enables the value of an arithmetical expression to be 
stored into a variable.

This manual pages is only about the use of the **/A** of the **SET** command 
and the use of floating point numbers. To learn more about the general use of 
the command, please see the [SET manual page](set).

## Synopsis ##

    SET [/a | /a[:]f] variable=expression

Computes the value of the arithmetical expression **expression** and stores it 
into **variable**. The behaviour of the command depends on the 
**EnableFloats** setting of the [SETLOCAL](setlocal) command.

The **=** sign can be replaced by one of the following operator:

* **+=** : Adds the result to **variable**.

* **-=** : Subtract the result to **variable**.

* **\*=** : Multiply **variable** by the result.

* **/=** : Divide **variable** by the result.

## Operators ##

The arithmetical expression has to be made of combination of the following 
operators and operands.

Binary operators available with floating point arithmetic are:

* **+** : Addition.

* **-** : Subtraction.

* **\*** : Multiplication.

* **/** : Division.

* **^** : Exponentiation.

* **%** : Modulo.

* **=** : Assignment.

Operators have the following precedence \(from greatest to lowest\):

* **unary operators**

* **^**

* **=**

* **\***, **/**, **%**

* **+**, **-**

To avoid precedence issue, use the parenthesis **\(** and **\)**.

Only one unary operator is available with floating point arithmetic:

* **-** : Minus sign.

Unary operators have highest precedence.

## Mathematical functions ##

In addition to operators, **expression** may contain mathematical function. To 
use such a function use the name of it followed by its arguments enclosed in 
parenthesis :

    function(expression)

Available functions are:

* **exp** : Exponential.

* **log** : Neperian logarithm.

* **log10** : Decimal logarithm.

* **sqrt** : Square root.

* Trigonometry :

  * **sin** : Sine.

  * **cos** : Cosine.

  * **tan** : Tangent.

  * **cot** : Cotangent.

  * **sec** : Secant.

  * **csc** : Cosecant.

* Reverse Trigonometry :

  * **asin** : Reverse sine.

  * **acos** : Reverse cosine.

  * **atan** : Reverse tangent.

  * **acot** : Reverse cotangent.

  * **acec** : Reverse secant.

  * **acsc** : Reverse cosecant.

* Hyperbolic trigonometry :

  * **sinh** : Hyperbolic sine.

  * **cosh** : Hyperbolic cosine.

  * **tanh** : Hyperbolic tangent.

  * **coth** : Hyperbolic cotangent.

  * **sech** : Hyperbolic secant.

  * **csch** : Hyperbolic cosecant.

* Reverse hyperbolic trigonometry :

  * **asinh** : Reverse hyperbolic sine.

  * **acosh** : Reverse hyperbolic cosine.

  * **atanh** : Reverse hyperbolic tangent.

  * **acoth** : Reverse hyperbolic cotangent.

  * **acech** : Reverse hyperbolic secant.

  * **acsch** : Reverse hyperbolic cosecant.

* **abs** : Absolute value.

* **step** : Step function \(Heaviside's function\). Returns **0** if **x < 
  0**, **1** else.

* **delta** : Dirac's function. Returns plus infinity if **x = 0** and **0** 
  else.

* **nandelta** : Dirac's function returning NAN instead of infinity.

## Constants ##

Finally, the following constants are defined

* **e**

* **log2e** : log2\(e\)

* **log10e** : log10\(e\)

* **ln2** : ln\(2\)

* **ln10** : ln\(10\)

* **pi**

* **pi\_2** : pi/2

* **pi\_4** : pi/4

* **1\_pi** : 1/pi

* **2\_pi** : 2/pi

* **2\_sqrtpi** : 2/sqrt\(pi\)

* **sqrt2** : sqrt\(2\)

* **sqrt1\_2** : sqrt\(1/2\), or 1/sqrt\(2\) or sqrt\(2\)/2.

## Special numbers ##

Special numbers are values that are not numbers but are considered as so. The 
values have been defined by IEEE standard, but Dos9 only support two of them:

* **inf** \(INFINITY\) : Infinite value.

* **nan** \(NotANumber\) : not a number.

## Precisness ##

As opposed to integers, wich are usually bound between **-2 147 483 648** and 
**+2 147 483 647**, floating point numbers offer a much greater range, 
between4 **2,2250738585072014e-308** à **1,7976931348623157e+308**. However, 
this gain on range causes a loss of precision because of approached computing.

## Bugs ##

It is not unusual to encounter preciseness bug as floating point number have a 
finite precision of about 15 decimal places. As a result some expression may 
be subject to approximation errors when dealing with numbers several orders of 
magnitude away from one another. Here is an example:

    (2*10^60+1)-2*10^60)

Computing this expression using floating points arithmetics will lead to a 
precision error as the result would be 0 even though it is clearly 1. This 
happen because **10^60** is several orders of magnitude greater that 1. 
Changing slightly the expression can fix this issue : 

    2*10^60-2*10^60+1

Another problem may be comparing two results of floating point computing, as 
approximations may lead to a slightly different values even though they are 
equal from a mathematical point of view. To fix this kind of bugs, use the 
**FEQ** comparison from the [IF command](if).

## Notes ##

This command uses a modified version of the **GNU libmatheval** library.

## Compatibility ##

Available since **0.7.1.0**, before the support of expressions was incomplete, 
supporting neither the **%** operating system nor functions.

Not compatible with **cmd.exe** that does not support floating point 
arithmetics.

## See also ##

[SET Command](set), [SET \(/a\) Command \(integers\)](setai) 

