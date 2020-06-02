# SHIFT Command #

The **SHIFT** command shifts batch script arguments. This command is very 
useful to create batch scripts requiring many parameters.

## Synopsis ##

    SHIFT [/start | /s[:]start] [/d[:]step]

Changes position of parameters within the variable **%0** to **%9**.

* **/start** ou **/s\[:\]start** : Specify a number **start** between **0** 
  and **9** that indicate at which parameters the command should start. The 
  first syntax is compatible with **cmd.exe** while the other one is not. By 
  default, displacement of parameters starts at **%0**.

* **/d\[:\]step** : Specify the length of the displacement. **Step** has to be 
  a number between **0** and **9**. The default value is **1**. This is a Dos9 
  extension.

Displacement takes place from the the lowest parameter to the highest. If any 
argument is left empty by the process, then **SHIFT** tries to put some 
additional arguments using remaining arguments stored in **%+**. If **%+** is 
already empty, these variables are left empty.

The content of the variable **%\*** is not modified by the **SHIFT** command.

## Compatibility ##

Mostly compatible with **cmd.exe**. Indeed, while replacing the **%0** 
parameter, **cmd.exe** checks that the new argument refers to a file or a 
directory and if it is not, replace it by the current directory. This 
behaviours is not implemented by Dos9.

## See Also ##

[Commands list](commands), [Dos9](dos9) 

