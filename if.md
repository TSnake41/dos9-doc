# IF command #

The **IF** command allows [conditional processing](spec/cond) of commands.

This command is very important for creating advanced batch scripts as it 
allows script to make conditionnal execution.

You might also prefer multilines **IF** to **IF**-[GOTO](goto) combination, 
which are a little bit disordered.

## Synopsis - First syntax ##

The very first one just compares two strings, and execute the specified 
commands if they're both equal. It supports also some basic modifiers. The 
syntax is :

     IF [/i] [NOT] string1==string2 (
     :: code to be ran
     ...
     )

Check whether **string1** and **string2** are the same strings and run the 
code to be run if it is true. The behaviour can be modified by the following 
switches and modifiers :

* **/i** : Comparison is case-insensitive. \(ie. ``Dos9'' will be equal to 
  ``DOS9''\).

* **NOT** : Negation. The code is ran if **string1** and **string2** are 
  different.

## Synopsis - Second syntax ##

The second syntax is used to compare either strings and numbers. It allows 
scripts to perform more advanced test such as testing if one number is greater 
than another one. This syntax should also be prefered since it is more robust, 
and if well used, this syntax is much more resistant to [expansion](spec/exp) 
bugs. As explained later.

     IF [/i] string1 cmp string2 (
     :: code to be ran
     ...
     )

Test comparison specified by **cmp** to strings **string1** and **string2** 
and run the code to be executed if the specified comparison is true.

Where **cmp** can be one of the following:

* **EQU** : \(EQUal\). The condition is true if the value associated to 
  **string1** and **string2** are identical. Values can be specified in 
  various numeral bases, decimal, octal or hexadecimal as long as the right 
  prefix is specified \(**0** for octal and **0x** for hexadecimal\). If any 
  of **string1** and **string2** do not represent any valid number \(eg. 
  **\[-\]\[prefix\]\[value\]**\), then **EQU** compares the strings behaving 
  exactly as **==**.

* **NEQ** : \(Not EQual\). Exact opposite of preceeding condition.

* **LEQ** : \(Less or EQual\). The value associated to **string1** is lesser 
  or equal to that of **string2**.

* **LSS** : \(LeSS\). The value associated to **string1** is strictly lesser 
  than that of **string2**.

* **GTR** : \(GreaTeR\). The value associated to **string1** is strictly 
  greater than that of **string2**.

* **GEQ** : \(Greater or EQual\). The value associated to **string1** is 
  greater or equal to that of **string2**.

**LSS**, **GTR**, **LEQ** and **GEQ** conditions require **string1** and 
**string2** to represent integers otherwise the result is unspecified.

Analogous conditions can be obtained for floating point numbers by prefixing 
condition with an **F**, leading to **FEQU**, **FGTR**, **FGEQ**, **FLSS** and 
**FLEQ**. The ability to deal with octal or hexadecimal floating point number 
is not warranted and may depend on platform or versions. To remain compatible, 
you have to use only the standard format 
\[sign\]\[number\]\[.number\]\[e|E\]\[exponent\].

## Synopsis - Third syntax ##

The last syntax allows to perform test on a object. Obviously, the specified 
command are ran if the test performed returned true.

     IF [NOT] [DEFINED | EXIST | ERRORLEVEL] object (
     :: code to be ran
     ...
     )

Checks whether the condition stated about **object** is true, and then 
executes the code to be executed if the condition is true. The conditions can 
be :

* **DEFINED** : The condition is true if the variable named by **object** is 
  defined.

* **EXIST** : The condition is true if a file named by **object** exists. The 
  string **object** can contain [regulars expressions](spec/regexp).

* **ERRORLEVEL** : **Deprecated** The condition is true if the environment 
  variable [%ERRORLEVEL%](errorlevel) is greater or equal to **object**, were 
  **object** is a number . Its use is deprecated, you should use the following 
  syntax instead :

         IF %ERRORLEVEL%==value

If you specify operator **NOT**, then the code to be executed is ran if the 
condition is false.

## Synopsis - Expressions (Fourth syntax) ##

**Dos9** offer a fourth syntax for the **IF** command. This syntax allows 
using logical connectors to build expressions.

    IF [/i] [ expression ] (
     :: code to run
    ...
    )

Run the code if the conditions specified by **expression** are met.

* **/i** : Discard case-sensitiveness.

* **\[ expression \]** : A list of conditions to be met for the code to be 
  executed. The use of brackets and space around elements is mandatory.

  An expression should be built made of comparisons connected together with 
  some logical operators.

  * Two types of tests are available :

            [NOT] cmp1 comparison cmp2
            [NOT] [Defined|Errorlevel|Exist] objet

    Both these forms are the same as those described above.

  * There is two operators available:

    * **or** : Logical or.

    * **and** : Logical and.

    The **and** operator own precedence over **or** operators.

  Finally, one can affect precedence using brackets **\[\]**.

## Synopsis - ELSE subcommand ##

After any kind of previously described **IF**, an **ELSE** keyword may be 
inserted so that code specified after the **ELSE** will be ran if the **IF** 
comparison fails.

     IF /i %var1%==%var2% (
    :: code to be executed if %var1% is equal to %var2%
    ) ELSE (
    :: code to be executed if %var1% differs form %var2%
    )

Both **ELSE** keyword preceeding and following codes must be enclosed in 
brackets, so that it defines two different [code blocks](spec/block). 
Otherwise, the interpretor should interpret it like a single line.

Both of these codes will work as **expected**:

    IF /i %var1%==%var2% (
     ECHO %var1% is equal to %var2%
    ) ELSE (
     ECHO %var1% differs from %var2%
    )
    
    IF /i %var1%==%var2% (ECHO %var1% is equal to %var2%) ELSE (ECHO %var1% differs from %var2%)
    
    :: both will output:
    ::  - ``ECHO %var1% is equal to %var2%''
    ::    when %var1% is equal to %var2%
    :: - ``ECHO %var1% differs from %var2%''
    ::    when %var1% differs for %var2%
    

Whereas the following code will fail :

    IF /i %var1%==%var2% ECHO %var1% is equal to %var2% ELSE ECHO %var1% differs from %var2%
    :: will output
    :: ``ECHO %var1% is equal to %var2% ELSE ECHO %var1% differs from %var2%''
    :: only when %var1% is equal to %var2%
    

## Dealing with spaces ##

Almost anyone have already seen the following message output from the prompt :

    Error : ``some'' was unexpected.

This error, has two origins. On the one hand, it could be sometimes just 
caused by a syntax error \(ie. prompt is failing to run command because it 
syntax is incorect\). This account for a great part of the causes of this 
error. On the other hand, the hand that we're interested in, it could be 
simply caused by a space character that wasn't expected. It happens really 
easy when using [var expansion](spec/exp) with variable that contain spaces or 
tabs. Let's take an example :

    IF %my_var%==test (
     ECHO The test is true
    )
    

As long as **my\_var** does not contains any space, or whatever possibly 
interpreted \(such as & and |\), this example works pretty well. But, if 
**my\_var** do contains such characters, it goes wrong. This effect is caused 
because **my\_var** is expanded before even the line interpretation, thus, any 
characters from **my\_var** will be interpreted. There's several trick to fix 
that bug.

* **my\_var** can be enclosed in double quotes, avoiding blank characters 
  problem. However, the characters like & and | contained in **my\_var** will 
  still be interpreted, and **my\_var** could not contain double-quotes 
  anymore.

* **my\_var** can be enclosed in single quotes, avoiding blank characters 
  problem. This causes the same issues as previous, replacing "double quotes" 
  by "single quotes".

* The last, and best solution is to expand **my\_var** using [delayed 
  expansion](spec/exp) rather than [conventional expansion](spec/exp). Indeed, 
  using that trick, **my\_var** will only be expanded after the line parsing, 
  and thus no character can cause issue.

Therefore, if you really need avoiding these errors \(for scripts that modify 
windows registry\), for exemple, you should use the most robust solution, ie:

    SETLOCAL EnableDelayedExpansion
    
    IF !my_var!==test (
     ECHO The test is true
    )
    

## The == bug ##

The fact that the second syntax is much more resistant to 
[expansion](spec/exp) bugs as been stated previously. Indeed, if a script 
complies to all hints to avoid bugs that have been given previously, it's 
still not guaranted to resist to all bugs. Indeed, the first syntax is subject 
to the ``== bug''. The following code is subject to this bug

    SETLOCAL EnableDelayedExpansion
    
    IF !my_var!==test (
     ECHO The test is true
    )
    

As stated in the previous part, this is perfectly unvunerable to bugs due to 
spaces, whatever... Nevertheless, a bug is encountered if **my\_var** contains 
``==''. In this case, the behaviour of comparison is modified as it uses first 
``=='' encountered. In most cases, this is issue is not even a problem, 
because script rarely make a comparison with ``=='' in both members. But it 
can cause the comparison to be inconsitent in some cases.

To conclude, if such a scenario is likely to happen when executing script, 
prefer the following syntax:

    SETLOCAL EnableDelayedExpansion
    
    IF !my_var! EQU test (
     ECHO The test is true
    )
    

## Compatibility ##

Mostly compatible with **cmd.exe**. Indeed, the use of **IF ERRORLEVEL** is 
not guaranted to be compatible with **cmd.exe**, as the behaviour of 
**cmd.exe** is weird \(it tests if **ERRORLEVEL** is greater than the 
specified number\) and causes numbers of mistakes.

Supported since version **0.4**.

**FEQ** comparison is supported since version **0.7.0.1**

## See also ##

[FOR command](for), [GOTO command](goto), [CALL command](call), [Command 
list](commands) 

