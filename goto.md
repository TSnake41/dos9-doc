# GOTO command #

Jump to a label in a batch script. This command is among the first commands 
learned while learning batch script, and it is usefull since it allow 
**conditional execution**.

It might be preferable to use [multiline if](if), especially in the case of a 
quite short piece of instructions.

## Synopsis ##

    GOTO [:]label [file] [/Q]

Jump to a label.

* **label** : the label where [Dos9](dos9) will jump. A **label** is a word, 
  or even a couple of words, which are used to identify the different pieces 
  of codes, and this couple of words must be preceded by a column **:**. It is 
  not necessary for labels to start at column 1.

* **file** : The file in which [Dos9](dos9) will seek the specified 
  **label**. This option requires the [dos9 extensions](spec/ext) to be 
  enabled.

* **/Q** : Silently ignore warning if the given **label** is not found on the 
  given **file** and continue script execution at next line. This switch 
  enables creating a kind of **switch/case** statement.

If the **GOTO** command is called within a command bloc \(such as within a 
[FOR loop](for) or within a [IF](if)\), then block execution is aborted and 
execution restart at given label.

The command **GOTO** does not affect [%ERRORLEVEL%](errorlevel) variable. If a 
jump failed, the execution continues after the command.

If **:label** is **:eof** then the **GOTO** command returns from the current 
subroutine to the previous execution level.

## Constructing a switch/case statement ##

The **GOTO** command allows constructing conditional statements such as 
**switch/case**. This functionality relies on the fact that **\[:\]label** is 
subject to [expansion](spec/exp), as any other batch-language element. Thus, 
using the **/Q** switch, a batch using somewhat of a **switch/case** statement 
can be achieved.

    @ECHO OFF
    
    :menu
    ECHO MENU
    ECHO  1. Choice 1
    ECHO  2. Choice 2
    ECHO  3. Choice 3
    ECHO.
    SET /P choice=Make your choice:
    
    :: start of switch/case
    GOTO /Q :case_%choice%
    
    :: if we got bad input, echo an error
    :: and go back to menu
    ECHO %choice% is not a valid choice
    ECHO.
    GOTO :menu
    
    :case_1
    :: Choosed 1
    ECHO You choosed 1
    GOTO :switch_end
    
    :case_2
    :: Choosed 2
    ECHO You choosed 2
    GOTO :switch_end
    
    :case_3
    :: Choosed 3
    ECHO You choosed 3
    
    :switch_end
    ::End of the batch
    

## Notes ##

For compatibility purpose, the **GOTO** supports syntax that consist in not 
separating **label** from the command name.

## Compatibility ##

This command is compatible with **cmd.exe**, excepted the **file** parameter 
which is only supported by **Dos9**, since version **0.7**

## See also ##

[IF command](if), [FOR loop](for), [Conditional running](spec/cond) [Command 
list](commands) 

