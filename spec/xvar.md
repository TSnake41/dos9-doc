# Special variables #

Special variables are internal variables provided by [Dos9](../dos9). Special 
variables are local, thus they can not be inherited by external programs.

## Special variable use ##

Special variables can not be modified, the can only be defined by 
[Dos9](../dos9), the [CALL command](../call) or the [FOR command](../for).

There is basically two types of special variables:

* Special variables prefixed by a single **%** \(per cent\) character which 
  denotes a special variable reffering to an argument of the script.

* Special variables prefixed by two **%** characters which denote a special 
  variable set within a loop by the [FOR](../for) command.

Those two types of variables have a slightly different [expansion](exp) 
precedence. Argument variables are expanded simultaneously with conventionnal 
expansion while FOR-generated variables are expanded before the delayed 
expansion and the tokenization of the command line.

Argument variables **%0** through **%9** are set to arguments passed to the 
script using the command line. As a convention, **%0** is always the script 
name when the script starts. However, when using [CALL](../call) to execute a 
label, **%0** contain the name of that label.

The **%\*** variable contains a line containing the parameters that have been 
passed to the script, that is it is the content of **%1** trough **%9** inside 
a single variable plus all the parameters beyond the ninth if any has been 
passed. The parameters beyond the ninth one \(**%9**\) can also be retrieved 
using the **%+** variable. On UNIX-based operating systems, it is not possible 
to retrieve the exact syntax of the command line. Thus **%\*** is created 
using the parameters and some added quotation if necessary.

## Special variable expansion ##

Special variables names are made of a single letter or a digit. Any ASCII 
character except the 33 first \(ie. from 0x20\) can be used. However, for 
readability purposes it is better to use only letters.

Special variable expansion is performed between [command argument](command) 
detection and [delayed expansion](var), allowing them to affect expansion of 
variables.

Special variable names need to be preceded by two **%**, \(except for **%0** 
up to **%9**, **%\*** and **%+**\) to be developed. Some option can be enabled 
by using the **~** sign. These options are the following:

* **%%~I** : Remove quotes around **%%I**.

* **%%~fI** : Expands to fully qualified path.

* **%%~dI** : Expands to **%%I** disk letter.

* **%%~pI** : Expands to **%%I** path.

* **%%~nI** : Expands to **%%I** file name.

* **%%~xI** : Expands to **%%I** file extension.

* **%%~zI** : Expands to **%%I** file size.

* **%%~aI** : Expands to **%%I** attributes.

* **%%~tI** : Expands to **%%I** access time.

Several options may be combined simultaneously \(up to 16 different options\).

As options are letters, conflicts can happen between variables names and 
options. If it is the case **Dos9** will use the longest combination of 
options \(maximum greediness\). As an example, the following code :

    ECHO %%~aI

Can be interpreted in two different ways:

* If **%%I** is defined, then **%%~aI** will be expanded. 

* If **%%I** is not defined and **%%a** is, then **%%~a** will be expanded.

* Otherwise, no expansion takes place.

When the **%0** variable gets expanded, **Dos9** has a slightly different 
behaviour:

* if **%0** or **%~0** is specified, the variable will be replaced by the 
  content of **%0**, stripped of its quote or not.

* if one ore more options is specified then the variable will be replaced by 
  the effects of the options if they where processing the file name of the 
  currently run batch. That is, **%~f0** refers to the path of the script 
  being executed, **%~dp0** to its directory, and so on and so forth. 

## Note ##

**Special variable** names and options are case sensitive.

## See also ##

[Environment variables](var), [Variable expansion](exp), [Specification 
index](index) 

