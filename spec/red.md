# Redirections #

Redirections allow standard input and outputs to me redirected by the command 
interpretor.

## Interpreter's input and outputs ##

Traditionally, every console program is given three files that a referred to 
as standard output and inputs.

* **Standard input** \(stdin\) : The default input of console programs. 
  Usually this input refers to text typed directly in the the terminal. As an 
  example, when no file path is given to [Dos9](../dos9), it reads commands 
  directly from the standard input.

* **Standard Output** \(stdout\) : The default output for console programs. 
  Usually, this output refers to the terminal. This output is usually the 
  default output for programs. As an example, [TYPE](../type) uses **stdout** 
  to output files. 

* **Standard Error** \(stderr\) : This is the default output used to print 
  error message. It is usually used to separate error message from actual 
  output in redirections.

Theses three output can be redirected using **Dos9**. However, **cmd.exe** 
allows user to redirect any file descriptor through redirections. But this 
could lead to absurd results since knowing which descriptor refers to which 
file. Moreover, this behavior can lead to strange side effects. Thus, this 
feature is not supported by [Dos9](../dos9).

## Redirecting input and outputs ##

[Dos9](../dos9) uses **<** and **>** characters to set redirections. **>** 
character is used to redirect **stdout** and **stderr**, whereas the **<** is 
used to specify **stdin** redirections.

When [dos9](../dos9) encounters either a **>** or a **<**, then Dos9 uses the 
very first parameter to the right of the same an use it as the name of a file 
to which the input or output will be redirected. The name of the file and the 
sign do not have to be separated by any blank character. Then Dos9 removes the 
file name from the command line. The **>** or **<** signs can be used anywhere 
in the command line, all of the following lines are valid.

    echo >file redirection test
    > file echo redirection test
    echo redirection test > file

Any of the previous syntax are valid. However, some of them give the code more 
readability, as such, using the third syntax is highly recommended.

Although the is only one syntax using **<**, redirections using **>** are 
provided with a bunch of different syntaxes, which are the following.

* The default behaviour if you use only the **>** sign, is to redirect the 
  standard output to the specified file.

        echo redirecting stdout > file

  The previous example will redirect stdout to **file**. That is, **file** 
  will be emptied and will recieve **"redirecting stdout"** as its new 
  content.

  File emptying can be inhibited by doubling the **>** sign to get the 
  following code. In that case, the line "redirecting stdout" will be added at 
  the end of **file**.

        echo redirecting stdout >> file

* Either of stdout or stderr can be chosen by preceding the **>** sign by 
  either **1** or **2**. As a result, the stream that gets redirected to 
  **file** change depending on the number:

  * **1** : standard output.

  * **2** : standard error.

  As an example, **stderr** can be redirected to **file** using:

        echo redirecting stderr 2> file

* It possible to redirect either stderr to stdout or stdout to stderr using 
  **2>&1** or **1>&2**.

  Thus, **stderr** and **stdout** can be redirected to **file** using the 
  following syntax:

        echo redirecting stderr and stdout at the same > file 2>&1

  Note that Dos9 allow the **2>&1** to be placed before the actual 
  redirection, even though this would raise an error using **cmd.exe**

## Compatibility ##

Partially compatible with **cmd.exe**.

Available since **0.48**.

## See Also ##

[Command line](cmdline), [Conditionnal operators](condop)

