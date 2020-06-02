# PUSHD command #

The **PUSHD** command permit to display which directory is at the top of **the 
directory stack** and change current directory by pushing the previous into 
**the directory stack**.

## Synopsis ##

     PUSHD [path1] [path2] [path3] [pathX]  

For each specified directories : change the **current directory** then pushd 
the previous to **the directory stack**.

If no path is specified, show which **directory** is at the top of the **the 
directory stack**.

In case of error, the **error code** match with the failed **path**.

## Compatibility ##

Mostly compatible with **cmd.exe**. The paths containing spaces must be 
delimited by double quotes to use multiples directories without confusion.

Multiples directories are an **Dos9** extension.

## See also ##

[CD command](cd), [POPD command](popd), [Directory stack](spec/dirstack), 
[Command list](commands) 

