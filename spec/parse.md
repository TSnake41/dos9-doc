# Parsing #

The command line **parsing** is done by [Dos9](../dos9) in a precise order. 
Knowing the order of different parsing step is really useful to a batch 
programmer.

## Parsing steps ##

During parsing, Dos9 execute steps in the following order:

* **Line reading**: During this step [Dos9](../dos9) reads text lines, either 
  from commands typed in the prompt or from a file. The line reading can occur 
  in two different ways, depending on the **CMDLYCORRECT** setting of 
  [SETLOCAL command](../setlocal):

  * If **CMDLYCORRECT** is disabled, the file is read entirely at start-up, 
    pre-parsing lines. and labels. This behaviour is specific to 
    [Dos9](../dos9), this enables saving up execution time compared to the 
    historical reading method of batch files. Before every new line execution, 
    **Dos9** checks that the source file has not been modified, it is, it 
    loads it again and continues execution at same line number.

  * If **CMDLYCORRECT** is enabled, **Dos9** uses the same mechanics as 
    **cmd.exe**. That is, before every new line reading, the script file is 
    opened, the line is read, and then the script is closed. This method is 
    inherited from older versions of ms-dos which had very few memory. Even 
    though this strategy saves up memory, it causes a high penalty on 
    execution speed. Thus this method is not the default any more for **Dos9**

  A change of **CMDLYCORRECT** setting during script execution leads to a 
  restart of the script from the beginning. Thus, any **CMDLYCORRECT** change 
  is discouraged during a script execution.

* **Conventional expansion**: When lines are read from a file or the prompt, 
  **Dos9** perform the very first step of variable expansion, following rules 
  described in [variables expansion](var).

* [Command line](cmdline) and [conditional operators](condop) parsing: Once 
  variable are expanded, **Dos9** does two tasks simultaneously. Conditional 
  operators are parsed while blocks are matched to check there is the same 
  number of block opening and closing.

* [Redirections](red) parsing: Dos9 tries to detect active redirections of the 
  standard streams on the command-line and applies it.

* [Command](command) detection and parsing: After redirections parsing, 
  **Dos9** searches command boundaries, and tries to extract command arguments 
  according to argument parsing policies.

* [Special variables](xvar) expansion: In each of the detected argument, 
  **Dos9** then performs special variable expansion.

* [Delayed expansion](var): Once special variable expanded, the delayed 
  expansion takes finally places. This is the final step before 
  **execution**.

* **Execution**: After all the preceding step, the command is finally executed 
  by the appropriate command. 

## See also ##

[Command line](cmdline), [Conditional operators](condop)

