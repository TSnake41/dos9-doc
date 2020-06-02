# TYPE command #

Display a text file.

## Synopsis ##

    TYPE [file ...]

Display a text file.

* **file ...** : A list of files to display. File names may be [regular 
  expressions](spec/regexp). If a file name does not refer to an existing 
  file, the command stop and display an error message. If the file name refers 
  to a directory, then, they will not be displayed.

  If no file has been specifed, then the **TYPE** command does not return an 
  error \(although **cmd.exe** does\) and read its input from the standard 
  input.

In spite of **cmd.exe**'s behaviour, Dos9 only display the file name prior to 
the file content if various files are to be displayed \(cmd.exe displays it 
also when only one file matches a regular expression\). File names are sent to 
standard error output, enabling them to be removed easily from the output 
using [redirections](spec/red).

Displaying a binary file directly to the terminal is unspecified behaviour. To 
view the content of such files, the use of [DUMP](dump) should be preferred. 
If the output of **TYPE** is [redirected](spec/red), then it is possible to 
print binary files safely.

On Unix-based platforms, it is not possible to display the content of 
directories even though directories are actually files as **TYPE** filters 
them.

## Compatibility ##

Available since revision **0.4**.

Fully compatible with **cmd.exe**.

## See also ##

[MORE command](more), [Command list](commands) 

