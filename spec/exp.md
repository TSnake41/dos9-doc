# Conventional and delayed expansion #

Variable expansion is a [parsing](parse) step during which variables get 
replaced in the command line.

This step in fact consist of two different step. The first, the **conventional 
expansion** and the **delayed expansion**. The first takes places as the file 
is read by Dos9. The second one takes place just before the command execution.

## Conventional expansion ##

Conventional expansion takes places at every new line read. It can not be 
discarded.

During this step [Dos9](../dos9) searches string delimited by some **%**. If 
Dos9 finds any of those, it will consider it to be [variable](var) names and 
replace it by their content.

Once **Dos9** encounters such a string, it proceeds the following way :

* if the string refers to a valid variable name, then **Dos9** will expand the 
  string into the variable content.

  As example :

        SET var=hello world !
        ECHO %var%

  will display :

        hello world !

* If both **%** are next to one another, Dos9 replace it by a single **%**

  As example:

        ECHO copy : 10%%

  will display :

        copy 10%

* If we are in neither of the previous conditions are met, then the string is 
  just deleted from the line.

  As example :

        SET foo=
        ECHO %foo% hello world !
        

  will display:

        hello world !

Some options can also be specified during the expansion by inserting a column 
**:** between the **%** signs just after the variable name. The following 
options can be used :

* Truncation of the content of the variable using the option

        %variable:~nb1,nb2%

  * **nb1** : the position of character of **variable** that should be the 
    beginning of the part to part that should be used for expansion. The first 
    character of **variable** is at position 0. If **nb1** is a negative 
    number, then the position are counted from the end of the string

  * **nb2** : the number of character of **variable** after **nb1** that 
    should be used for expansion. If **nb2** is a negative number, then the 
    position are counted from the end of the string

  Note that if the version of Dos9 that is running supports utf-8, then the 
  variable truncation happens only counting entire characters. If not, this is 
  not warranted.

  As example:

        SET foo=Hello world
        ECHO %foo:~2,3%
        ECHO %foo:~2,-3%

  Will print :

        llo
        llo wo

* Replacement of a string of **variable** :

        %variable:string1=string2%

  * **string1** : string to be replaced in **variable**

  * **string2** : string remplacing **string1** in **variable**

  As example:

        SET foo=Ceci est un test
        ECHO %foo:est=pingouin%

  will print :

        Ceci pingouin un tpingouin

* Replacing a **variable** by a default string if **variable** is undefined :

        nom_variable:string

  * **string** : Defaut string.

  For example :

        SET var=
        ECHO %var:rien%

  will print : 

        rien

## Delayed expansion ##

Delayed expansion takes place just before line execution. This step can be 
discarded via the [SETLOCAL](../setlocal) command using the 
**ENABLEDELAYEDEXPANSION** or **DISABLEDELAYEDEXPANSION** options.

Delayed expansion works exactly as conventional expansion excepting that it 
uses **!** instead of **%**.

It enables some very frequent batch programming issue to be solved :

* Correctly handle variables within a [FOR](../for) loop or a [IF](../if) 
  command, since variables get expanded again after every new loop, as opposed 
  to conventionnal expansion which does not.

  As an example, the following code that use only conventional expansion 
  exhibits a strange behaviour :

        SET var=1
        ECHO 1: %var%
        IF %var% equ 1 (
         SET var=2
         echo 2: %var%
        )

  The output is quite surprising as it seems that **%var%** does not get 
  modified. However, in fact, it is but only when the line was read from the 
  file. 

  To get the expected result, using delayed expansion is necessary, that is 
  modifying a bit the code:

        SETLOCAL EnableDelayedExpansion
        SET var=1
        ECHO 1: %var%
        IF %var% equ 1 (
         SET var=2
         echo 2: !var!
        )

* Work around some parsing problems that occur when a variable containing 
  spaces gets expanded :

  As an example, the following code will fail as spaces in **%var%** will 
  raise an error:

        SET var=some variable with spaces
        IF %var% equ test (
        :: some code
        )

  The best way to work around this is to use delayed expansion. A couples of 
  other workaround and the reason this one is the base are discussed in the 
  [IF command](../if) page.

        SETLOCAL EnableDelayedExpansion
        SET var=some variable with spaces
        IF !var! equ test (
        :: some code
        )

## Special var expansion ##

[Special variables](xvar) just before delayed expansion. This topic is 
discussed on the associated page.

## Compatibility ##

Compatible with **cmd.exe**.

Available since **0.7**

## See also ##

[Environment variables](var), [Special variables](xvar), [SETLOCAL 
command](../setlocal), [Specification index](index) 

