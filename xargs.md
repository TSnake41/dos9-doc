# XARGS Command #

The **XARGS** command allow to run a command with arguments from the standard 
input.

## Synopsis ##

    XARGS [command ...]

Run a command with arguments from the standard input.

* **command ...**: A command, either internal or external. Any special 
  charactersUne encountered in command or in the command input \(| et &\) will 
  have no effect.

As **Dos9** reads through the standard input, only newlines will be removed 
from final parameters. If a line read from the standard contains spaces or 
delimiters \(ie. tabs, comma, semicolon\) then the whole line will 
automatically be quoted by **xargs** to create a single parameter.

## Compatibility ##

Unavailable on **cmd.exe**. Available since **217.1**.

## See Also ##

[Command list](commands), [WC command](wc)

