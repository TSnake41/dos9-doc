# MOD Command #

The **MOD** command is [Dos9](dos9)-specific command that enable external 
modules designed for **Dos9** to be loaded at runtime in order to provide 
extra functionalities through additional internal commands.

## Synopsis ##

    MOD [/l] [/q] [module ...]

Load or list loaded modules.

* **/l** : List loaded modules.

* **/q** : Ignore **module** silently if it has already been loaded.

* **module** : A path to the module to be loaded. If **module** is a relative 
  path, then the associated file is searched inside the module default path 
  \(which is **%DOS9\_PATH%/modules**\). If **module** is an absolute path, 
  the preceding behaviour is overridden and **MOD** tries to load the file 
  referred to by **module**.

Modules files are executables that can be dynamically loaded by **Dos9** and 
that have been programmed to add commands to the interpretor.

The process of writing a module for Dos9 and their capabilities are described 
inside the **GUIDELINES** file of the source distribution.

## Compatibility ##

Not compatible with **cmd.exe**, this is an extension. Available since version 
**218.3**.

## See also ##

[Batbox modules](modules/batbox) 

