# SETLOCAL command #

The **SETLOCAL** command allows setting local environment and changing 
[Dos9](dos9) interpretors settings at runtime.

To revert modifications to environment after a **SETLOCAL** command, use the 
[ENDLOCAL](endlocal) command.

## Synopsis ##

    SETLOCAL [ENABLEDELAYEDEXPANSION | DISABLEDELAYEDEXPANSION] [ENABLEFLOATS | DISABLEFLOATS] [CMDLYCORRECT | CMDLYINCORRECT]

Create a local environment so that changes to variables after the 
**SETLOCAL** command be discarded using the **ENDLOCAL** command. The option 
that can be specified allow enabling or disabling following modes :

* **ENABLEDELAYEDEXPANSION**, **DISABLEDELAYEDEXPANSION** : Enable or disable 
  [delayed expansion](spec/exp).

* **ENABLEFLOATS**, **DISABLEFLOATS** : Enable or disable [floating 
  numbers](spec/floats).

* **CMDLYCORRECT**, **CMDLYINCORRECT** : Enable or disable more compatibility 
  with **cmd.exe**.

When calling **SETLOCAL**, the [%ERRORLEVEL%](errorlevel) variable is left 
unmodified, except if an error occurs, then **%ERRORLEVEL%** will be set to 
**-1**.

## Compatibility ##

Fully compatible with **cmd.exe** since **218.2**. **ENABLEEXTENSION** and 
**DISABLEEXTENSIONS** are ignored by [Dos9](dos9), every extensions are 
enabled.

## See also ##

[ENDLOCAL command](endlocal), [SET Command](set), [Commands list](commands) 

