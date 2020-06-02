# START command #

The **START** command enables executing a command or a program inside another 
console or in background. **START** also enables opening files with 
appropriate programs, it is thus a very useful command.

## Synopsis ##

    START [/d dir] [/b] [/min] [/max] [/wait] ["title"] [command [parameter ...]]

Runs **command** in a separate windows, if the feature is available on the 
current operating system. If not, **command** is run as separate process.

* **command** : A path to the executable to be launched. This path can also 
  refer to a **file** name, in which case the executable associated with the 
  file type will be launched with **command** as argument. If no **command** 
  is given, **START** launches [Dos9](dos9) by default.

* **parameter ...** : A list of parameters to be passed to **command**.

* **"title"** : The new window title \(only supported under Windows\). The 
  **"title"** parameter is handled the same way as with cmd. That is, if the 
  first parameter in the line is surrounded by quotation marks, then **Dos9** 
  will use it as **"title"**. Thus it is quite important to specify 
  **"title"** \(even as an empty string\) to prevent buggy behaviours if 
  **command** happens to be also surrounded by quotes.

* **/d dir** : A path to **command**'s current directory.

* **/max** : Maximizes the window \(ignored under UNIX-based OSes\).

* **/min** : Minimizes the window \(ignored under UNIX-based OSes\).

* **/wait** : Waits until **command** returns

* **/b** : Start the process in background \(in the same console\).

If **command** is an internal command and the **/b** switch is specified, then 
the command will be ran as a thread of the current interpreter.

## Compatibility ##

Partially compatible with **cmd.exe**. Under UNIX-based operating systems, 
some features are ignored: **"title"**, **/max**, **/min**. The possibility of 
launching a new window is requiring the support of **mimeopen** or 
**xdg-open** in your platform, and obviously depends on the use of a graphical 
environment such as **X** to work.

Note that the implementation using **xdg-open** might be a bit buggy as this 
script has plenty of defaults, but it is more widespread than **mimeopen** as 
it is older. Dos9 gives priority to **mimeopen** thus installing it is highly 
recommended to get the best experience of [Dos9](dos9) on UNIX-based platforms

Available since **218.2**.

## See Also ##

[Call command](call), [Command list](commands) 

