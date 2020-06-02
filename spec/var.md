# Environment variables #

Environment variables are the most common way to deal with variables with 
[Dos9](../dos9). They are usually defined by the operating system but 
**Dos9** uses its own implementation. Any external binary executed from 
**Dos9** inherits its environment.

## Use ##

Environment variables can be defined, deleted or modified using the [SET 
command](../set).

Environment variables can be included in command using [Variable 
expansion](exp).

## Default defined variables ##

Some environment variables are automatically defined by **Dos9**.

Eight of them are native variables :

* [%DOS9\_OS%](../dos9var) : OS type.

* [%DOS9\_PATH%](../dos9var) : Dos9 binary path.

* [%DOS9\_VERSION%](../dos9var) : Dos9 version.

* [%ERRORLEVEL%](../errorlevel) : Return value of last executed program.

* [%CD%](../cd) : Current directory.

* [%RANDOM%](../random) : A random number.

* [%DATE%](../time) : Date.

* [%TIME%](../time) : Time.

Some other variables are defined by the operating system or by 
[Dos9\_Auto.bat](../dos9auto):

* **%PATH%** : Dos9 paths list variable.

* **%SYSTEMDRIVE%** : Disk root.

* **%SYSTEMROOT%** : Operating system folder path. 

* **%USERPROFILE%** : Current user folder path.

## Note ##

Variables names are case insensitive \(eg. **%ErrorLevel%** is equivalent to 
**%errorlevel%**\).

## See also ##

[Special variables ](xvar), [Variable expansion](exp), [Specifications 
index](index). 

