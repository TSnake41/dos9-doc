# EXIT Command #

The **EXIT** command quit [Dos9](dos9) current instance, optionally returning 
an exit code. Exit can also be used to exit the current subroutine.

## Synopsis ##

    EXIT [/b] [code]

Exit the command prompt.

* **/b** : Exit only from the current execution level \(the current 
  subroutine\), with a behaviour similar to [GOTO:EOF](goto), except a return 
  value can be specified. If employed outside a subroutine, **/b** has no 
  impact on the command behaviour.

* **code** : Specify an integer to be returned as exit code. This integer is 
  usually bound to a 32-bit signed integer, that is between **2147483647** and 
  **-2147483648**. The exit code can be accessed through the variables 
  [%ERRORLEVEL% and %=EXITCODEASCII%](errorlevel).

If **code** is not specified, then the **%ERRORLEVEL%** value is unchanged.

## Compatibility ##

Available since **0.4**.

Compatible with **cmd.exe**

## See also ##

[GOTO command](goto), [Command list](commands)

