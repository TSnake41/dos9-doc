# CD, CHDIR commands and %CD% Variable #

The **CD** command changes or shows the current directory of [Dos9](dos9) 
command prompt.

The **%CD%** variable expands to the current directory of [Dos9](dos9) command 
prompt.

## Synopsis ##

    CD  [[/d] path]
    CHDIR [[/d] path]

Changes or displays the current working working directory.

* **path** : A path to the new working directory.

* **/d** : Forces changing current drive on **Windows**. This switch has no 
  effect on **UNIX**-like platforms since their file system trees always share 
  a unique root **/**. 

If neither **path** nor **/d** is specified, then **CD** will display the path 
to the current working directory.

On **Windows** \(since version **2014.0.9b**\), the **CD** command behaves 
allmost the same way as **cmd**'s **CD** does, supporting the possibility to 
have several current working directories depending on the **current drive**. 
The **CD** command behaviour is the following :

* If **path** only consists of a drive letter \(ie. something like "A:"\), 
  then **CD** enables the drive referred to by **path** and use the current 
  working directory associated with this drive. Such a drive change be 
  abbreviated by just typing **X:** at the prompt.

* If **path** is absolute \(ie. It mentions the drive letter plus sub 
  directories\), then, the current working directory associated with the drive 
  is replaced by **path**. If **/d** is not specified, the **CD** command will 
  not modify current directory, unless **path** refers to the current drive.

* If **path** is relative, then **CD** changes the current working directory 
  to **path**. This is the only syntax of **CD** that is guaranteed to be 
  portable across platforms.

## Variables ##

    %CD%

Expands to the current working directory. This variable is read-only and can 
not be modified using [SET](set). Depending on [Dos9](dos9) version, the 
undocumented **%\_\_CD\_\_%** variable defined by **cmd** might as well be 
defined by **dos9**, however its use is strongly discouraged.

    %=X:%

Expands to the current working directory associated with drive **X:**. This 
undocumented variables are also defined by **cmd.exe**, even though they are 
undocumented. However, this family of variable is not defined on 
**UNIX**-like OSes.

## Bogus ##

On **Windows**, **CD** may actually change current directory to a path that 
does not exist if **path** is made of dots. Indeed, internal windows routines 
fail to identify such folders as non-existing, thus allowing **Dos9** to 
change directory. For example:

    CD ...

## Compatibility ##

Fully compatible with **cmd.exe**.

Available since version **0.4**

## See also ##

[Variable](spec/var), [Specifications Index](spec/index), [Command 
list](commands) 

