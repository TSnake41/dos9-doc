# %ERRORLEVEL%, %=EXITCODEASCII% variables #

**%ERRORLEVEL%** is an environment variable defined automatically by 
[Dos9](dos9) at end of command execution. It enables checking if the previous 
command failed. With most commands, if **%ERRORLEVEL%** is equal to 0, then no 
error occurred.

## Synopsis ##

    %ERRORLEVEL%

A variable containing the exit code of the last command, either **internal** 
or **external** command. In general, a return value of **0** indicates the 
command ran successfully and any other value indicates an error, though this 
is not always the case.

The %ERRORLEVEL% variable should not be modified using the [SET](set) command 
because these changes will be overridden by the **SET** command exit code.

    %=EXITCODEASCII%

A variable containing the character associated to exit code according to the 
**ASCII** codeset. If [Dos9](dos9) has been build with UTF-8 support, then 
**%=EXITCODEASCII%** will contain the character associated according to UTF-8, 
taking account of all the bits of the exit code in **%ERRORLEVEL%**. If not, 
[Dos9](dos9) will only use the least significant 8 bits of the exit code.

## See also ##

[Variables](spec/var), [Commands list](commands)

