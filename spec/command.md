# Commands and Argument detection #

Commands and arguments are the two smallest piece of code in batch and are 
used to describe a single operation the interpreter can execute.

## Argument detection ##

What [Dos9](../dos9) considers to be arguments is a set characters delimited 
by delimiters accepted by **Dos9** which are colons \(**;**\), semicolons 
\(**;**\), comma \(**,**\), newlines, tabs and spaces. Thus the following line 
consists of two arguments:

    COMMAND foo bar

However, as it is quite common to need to pass arguments to commands that 
contain one of the preceding delimiters, It is possible to use either 
quotation marks \(**"**\) or character escaping via **^** to override 
delimiters default behaviour :

    COMMAND "foo bar"
    COMMAND foo^ bar

Both preceding syntax are valid. Note that if using quote, characters outside 
the quotes can be appended or be preceding without any influence on the 
validity of the line, just like the following.

    COMMAND foo"ta fu"bar

Note that normal control character like **|**, **&** or **\(** and **\)** are 
ignored when surrounded by quotation marks.

## Commands ##

**Commands** are the simplest structure of batch programming. Every action is 
done using a **command**. Commands are lines \(or a part of line, if 
[conditonnal operators](condop) are used\), that denote an action to be done. 
Typically, **commands** are described using the following syntax :

    COMMAND mandatory_argument [optional_argument] [choice1 | choice2]

Where:

* **COMMAND** is the name of the command. **COMMAND** should refer to one of 
  the following possibilities, by order of precedence:

  * An **internal command** to be ran, that is, a command which is included 
    inside the [Dos9](../dos9) command interpreter.

  * A **path** or the name of an external command located inside one of the 
    directories listed in [%PATH% variable](var) if **Dos9** fails to find an 
    internal command matching **COMMAND**.

  * If both preceding options fail, **Dos9** considers that **COMMAND** refers 
    to a file that is not executable and tries to find a program to handle 
    **COMMAND** using operating systems files associations. The script used to 
    find operating system associations under UNIX-derived OSes can be 
    customized using [%DOS9\_START\_SCRIPT%](../dos9startscript) environment 
    variable.

  A list of commands shipped with **Dos9** \(internal and external\) can be 
  obtained through [command list](../commands) manual page.

* **madatory\_argument** is an argument that must be specified for the command 
  to run properly. 

* **Optional\_argument** is an argument that is not required by the command 
  and is optional. These arguments only affect the behaviours of the command. 
  Two arguments can be simultaneously optional is specified as:

        COMMAND [arg1 arg2]

  In this case, **arg1** and **arg2** have to be both specified for the 
  command to be executed. Obviously, when specifying optional parameters you 
  should not use the square brackets \(**\[** and **\]**\), theses are just a 
  way to depict optionality.

* **\[choice1|choice2\]** specify a choice that have to be made between 
  **choice1** and **choice2**. Usually, specifying one of them is not 
  mandatory as square brackets depict optionality. Some can consider this 
  syntax ambiguous and depict the necessity of making a choice not using 
  brackets, like:

        COMMANDE {choix1|choix2}

  No **Dos9** command is supposed to use this syntax as it not required for 
  well designed command to require the user to make a mandatory choice.

## See also ##

[Conditional operators](condop), [Redirections](red)

