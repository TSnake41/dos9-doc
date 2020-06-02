# ENDLOCAL command #

The **ENDLOCAL** command reverts modifications to environment that have 
happened since the last [SETLOCAL](setlocal) command call.

## Synopsis ##

    ENDLOCAL

Reverts changes to the environment since last [SETLOCAL](setlocal) command, 
and also reverts modifications to [Dos9](dos9) options by the last 
**SETLOCAL**. If there is no previous call of this command, then the command 
does nothing. 

**SETLOCAL** and **ENDLOCAL** statements can be nested, so that various 
environment states can be saved. However upon a [CALL](call) command, the 
scope of **ENDLOCAL** is reduced: it can only revert changes made after 
**SETLOCAL** commands called after the last **CALL** command.

When calling **ENDLOCAL**, the [%ERRORLEVEL%](errorlevel) variable is left 
unmodified.

## Saving a modification to parent environment ##

**ENDLOCAL** reverts all modification to environment. To keep the some 
modifications, [conditional operators](spec/condop) can be used as follow:

    SET my_var=1
    SETLOCAL
    SET my_var=2
    ENDLOCAL & SET my_var=%my_var%

## Compatibility ##

Fully compatible with **cmd.exe** since **218.2**. 

## See also ##

[SETLOCAL command](setlocal), [SET Command](set), [Commands list](commands) 

