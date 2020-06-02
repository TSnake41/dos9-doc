# List of Dos9 internal and external commands #

This is a list containing all the name of [Dos9](dos9) internal and external 
commands. The command tagged with **\[int\]** are internal, and those tagged 
with **\[ext\]** are external.

An internal command is a command which is directly intergrated on 
[Dos9](dos9), so that it does not need any additional binaries to work. These 
commands are the faster and the most compatible.

An external command is a command which needs an additionnal binaries. These 
commands provide more flexibility to batch programs.

The specification can be found in [specifications index](spec/index).

## User-interface command ##

* [COLOR](color) **\[int\]** : Change the console screen color.

* [CLS](cls) **\[int\]** : Clear the console screen.

* [ECHO](echo) **\[int\]** : Display text in the console.

* [PAUSE](pause) **\[int\]** : Make a pause in a batch script

* [TITLE](title) **\[int\]** : Change console title.

* [BREAK](break) **\[int\]** : Enable/disable CTRL-C handling.

* [PROMPT](prompt) **\[int\]** : Changes Dos9 command prompt.

* [PECHO](pecho) **\[int\]** : Display a text formatted for **PROMPT**

## Scripting command ##

* [ALIAS](alias) **\[int\]** : Define an alias.

* [SHIFT](shift) **\[int\]** : Change position of command-line arguments in 
  batch files.

* [FOR](for) **\[int\]** : Loop in a script.

* [GOTO](goto) **\[int\]** : Jump to a label in a script.

* [CALL](call) **\[int\]** : Call a external script or a routine, within the 
  current command context.

* [SET](set) **\[int\]** : Modify an environment variable. Either through a 
  string litteral, a mathematical expression or an user input.

* [START](start) **\[int\]** : Run a command.

* [SETLOCAL](setlocal) **\[int\]** : Creates local environment and changes 
  [Dos9](dos9) mode.

* [ENDLOCAL](endlocal) **\[int\]** : Reverts changes to local environment 
  after [SETLOCAL](setlocal) call.

* [REM](rem) **\[int\]** : Introduce a comment.

* [EXIT](exit) **\[int\]** : Exit [Dos9](dos9).

## File commands ##

* [CD, CHDIR](cd) **\[int\]** : Change current directory.

* [DIR](dir) **\[int\]** : Browse subdirectories.

* [DEL, ERASE](del) **\[int\]** : Delete files.

* [MD, MKDIR](md) **\[int\]** : Create directory.

* [RD, RMDIR](rd) **\[int\]** : Delete directory.

* [PUSHD](pushd) **\[int\]** : Change current directory and push the previous 
  on the directory stack.

* [POPD](popd) **\[int\]** : Pull a directory on the directory stack to define 
  the current directory.

* [TYPE](type) **\[int\]** : Type files.

* [MORE](more) **\[int\]** : Display files screen by screen.

* [MOVE](move) **\[int\]** : Move files.

* [COPY](copy) **\[int\]** : Copy files.

* [RENAME, REN](ren) **\[int\]** : Rename files.

* [FIND](find) **\[int\]** : Find strings in files.

* [WC](wc) **\[int\]** : Display file counts.

* [XARGS](xargs) **\[int\]** : Run a command taking argument on standard 
  input.

* [TEA](tea) **\[ext\]** : Fast and simple text preprocessor. 

