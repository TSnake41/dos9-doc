# ALIAS command #

The **ALIAS** command defines alias to commands.

## Synopsis ##

    ALIAS [/f] name=command

Defines an alias.

* **name** : Name of the alias to be created.

* **command** : The command use to expand **name** on command line each time 
  **name** is called. Obviously **command** can contain switches and 
  parameters, but it is supposed to be static.

* **/f** : create an alias even if **name** corresponds to an already defined 
  alias or internal command.

**ALIAS** allows redefining an internal command. This functionnality is 
interesting if you have to hook some internal command.

**ALIAS** does not check that the aliases it creates are not self-calling 
\(eg. no circular declariation\). If **ALIAS** is used to create such aliases, 
these alias will lead to infinite loop \(or even a lack of memory\) when used.

By default, There is only one **alias** defined by [Dos9](dos9). It links 
[HELP](help) to [HLP](hlp).

## Compatibility ##

Does not exist in **cmd.exe**.

## See also ##

[Command list](commands) 

