# Conditional operators #

**Conditional operators** are operators useful allowing different commands to 
be interconnected. For example, using **conditionnal operators** a command can 
be executed only upon failure of another command.

## Synopsis ##

    command1 operator command2 ...

Run two commands linked by a conditional operator:

* **command1**, **command2** : Two valid [Dos9](../dos9) commands.

* **operator** : An operator linking **command1** and **command2**.

## Operators type ##

There is four types of conditional operators:

* **&** : No condition. **Command2** gets executed after **command1**.

  This operator is not really interesting as the same result can be achieved 
  by placing both commands on separates names \(through the use of parenthesis 
  for [FOR](../for) and [IF](../if) commands\), achieving also a higher 
  readability.

* **&&** : Run **command2** if the last executed command returned on success. 
  To determine if an error occured, [Dos9](../dos9) uses the value of the 
  **%ERRORLEVEL%** variable fixed by the last executed command :

  * if **%ERRORLEVEL%** is zero, then the command completed successfully.

  * else the command returned on error.

  if the last executed command returned upon a failure, **command2** is 
  ignored and **Dos9** tries to run any of the subsequent commands following 
  rules associated with each of the conditional operators.

* **||** : Run **command2** if the last executed command returned upon a 
  failure.

* **|** : Connects **command1** standard output to **command2** standard input 
  and run both simultaneously.

  As both commands are executed simultaneously, the process [Dos9](../dos9) 
  forks and a child interpreter is created. While **command2** runs on the 
  parent interpreter, **command1** is executed on the child. Once 
  **command1** exits, the child interpreter dies and the script execution 
  continues on the parent intepreter.

  Thus, if a **command1** modifies **Dos9** environment variable, the changes 
  will not affect the parent interpretor, and the environment of the parent 
  will be left unchanged. As an example:

        set example=1 | more test.txt

  will not assign the **%example%** variable. However, **command2** can 
  actually change environment variables of the parent interpreter. As an 
  example:

         more test.txt | set /p example=

  will assign the **%example%** variable.

  This behaviour is the opposite of **cmd.exe**, but it seem more worthwhile 
  to keep the current behaviour as it make possible to assign easily the 
  output of a command to a variable.

Obviously, there is no limitation in the number of conditional operators that 
can be used in a single line.

## FOR and IF behaviour ##

The [FOR](../for) and [IF](../if) are two special command because they change 
the precedence of **conditional operator**. By default, if there is no block 
encountered, then all the operator have the same priority.

This is not true using **IF** or **FOR** as they swallow all the commands on 
theirs right-side, acting as if a block was surrounding the command up to the 
end of the line.

This also means that the scope of the **IF** or the **FOR** commands start 
from the command up to the end of the command-line. For example, the following 
code will loop over **command1&command2** instead of looping over 
**command1** and then executing **command2**:

    for %%A in (1 2 3 4 5 6 7 8 9 10) do command1&command2

To prevent **IF** or **FOR** from swallowing every command up to the end of 
the command-line, enclose the command in a block, as follows:

    (for %%A in (1 2 3 4 5 6 7 8 9 10) do command1) & command2

## Compatibility ##

Available since **0.5.0.0**.

Compatible with **cmd.exe**, except for the order of process in pipes.

## See Also ##

[Specification index](index), [Environment variables](var) 

