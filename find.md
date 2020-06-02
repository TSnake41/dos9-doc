# FIND command #

Search for a string or an expression in one or several files.

## Synopsis ##

    FIND [/c] [/n] [/i] [/v] [/e] string [files ...]

Search for a string or an expression, in one or several files or in the 
standard input \(**stdin**\).

* **string** : The text string or the expression to be searched in **files** 
  or in the standard input. Unlike **Windows** native implementation of 
  **FIND**, [Dos9](dos9) does not require the use of quotes to delimit 
  **string**.

* **files ...** : A list of files \(that may include [regular 
  expression](spec/regexp)\) in which the **FIND** is to search **string**. 
  Folders that match regular expressions are ignored. If **files** is empty, 
  then **FIND** uses standard input as a file input.

* **/e** : Assume that **string** is a [regular expression](spec/regexp). Note 
  that **FIND** searches lines that match the full regular expression.

* **/c** : Count the number of line matching **string** and only print this 
  number.

* **/n** : Print line numbers of matching lines.

* **/i** : Use case insensitive search.

* **/v** : Reversed search; search lines that does not contain **string** or 
  does not match the regular expression.

Obviously, the **/c** and **/n** switches can not be mixed. If **FIND** 
encounters **/c** and **/n** switches together, does will take account of the 
last specified switches.

The **FIND** command has no line length limit, unlike **Windows** 
implementation which supports a maximum length of about 1024 characters.

The **FIND** command is not designed to handle binary files. However **FIND** 
is perfectly able to search in a binary file as long as it does not contain 
any **NULL** character.

In order to specify a **string** to search that contain quotes, use the escape 
character **^** before the quotes to escape.

Although **Windows**' **FIND** is an external command, **Dos9**'s **FIND** is 
an internal command. Under **WINDOWS** you can use the native command from 
**Windows** using the [ALIAS](alias) command.

## Compatibility ##

Compatible with **cmd.exe**.

Available since version **2014.0.9b**.

## See also ##

[Command list](commands), [TYPE command](type), [MORE command](more)

