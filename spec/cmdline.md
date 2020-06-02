# The command-line #

The **command-line** is probably one of the most important concepts of batch 
programming. It describes a set of command and blocks \(possibly nested\) 
separated by [conditional operators](condop).

## Block ##

A **block** is a construct that allows grouping several command-lines 
separated by a new line. inside a single execution context, enabling them to 
share the same output or to be executed together. Such a block can be 
specified by enclosing several **command-lines** in parenthesis, such as:

    (echo command line 1
    echo command line 2)

One of the most important features provided by block is to group output and 
input of commands so that they can share input or output through 
[pipes](condop) or [redirections](red), as shown in the following examples

    (echo command1
    echo command2 ) > file

Blocks can also be used to affect precedence of [conditional 
operators](condop). By default, there is no precedence for conditional 
operators and the commands are executed from left to right. Adding blocks can 
modify the control flow:

    command1 && command2 || command3

In this example, there is no precedence rules and the operators are executed 
from left to right, that is:

* **command1** is run, then depending on the return state of **command1**:

  * Upon successful return of **command1**, **command2** is run:

    * Upon failure of **command2**, **command3** is run.

  * Upon failure of **command1**, then **command2** is skipped and 
    **command3** gets executed.

However, precedence can be modified using blocks as follows:

    command1 && (command2 || command3)

In this case, **command3** only gets executed upon a failure of **command2** 
which is ran only if **command1** succeeds.

## Command-line ##

A command-line is the most general construct existing in batch programming. It 
refers to a well-constructed code line that can contain a combination of 
blocks \(possibly nested\), [commands](command) and [conditional 
operators](condop), and that is executed within a single pass by **Dos9** 
\(that is, only one reading operation and only one [conventional 
expansion](var) takes place\).

To match command-lines, Dos9 uses the following rules for associating and 
nesting command, command-lines and blocks:

* A **command-line** is made of at least one **command** or block.

* [Conditional operators](condop) delimit **commands** or **blocks** inside a 
  **command-line**.

* A **block** can contain several **command-lines** separated by newlines.

* A **command** can contain some blocks its [IF](../if) or [FOR](../for). Dos9 
  does no syntax check to verify whether the syntax of the command is correct.

A more formal description of this behaviour is the following using Backus-Naur 
form for describing grammars.

    conditional-operator = "&" | "&&" | "||" | "|"
    command-line = block
                   | command
          | command-line conditional-operator command
          | command-line conditional-operator block
    
    block = "(" block-expression ")"
    
    block-expression = command-line
          | block-expression "\n" command-line
          
    command = "for" command-line
             | "if" command-line
             | "if" command-line "else" command-line
       | normal-command
    

## See also ##

[Commands](command), [Conditional operators](condop)

