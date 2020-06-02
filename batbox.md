# BATBOX Command #

Batbox is a command that allow creating easily console graphics and provide a 
simple interface to get user inputs through keyboard and mouse.

This manual page is about the 5.x versions of the batbox command in both 
module and external executable format. For a quick history of the command, 
please check out the **history** section.

5.x series are available as a separate executable and as a module for 
**Dos9**, which enable much faster execution speed compared to separate 
executable. The **BATBOX** command is available for **WINDOWS** and 
**Unix**-based OSes.

## Synopsis ##

    MOD modules/batbox
    :: command to load Dos9 batbox module
    
    BATBOX  [/a chr] [/d string] [/g X Y] [/k[_] [name] | /l[_] [name]] [/w duration] [/c color] [/n] [/h show] [/m[_] [X Y type] | /y [X Y type]] ...

Create console graphics or get user input:

* **/a chr** : Prints character asociated with the given **chr** ASCII code. 
  Unicode characters might also be printed depending on the OS.

* **/d string** : Prints a string at the console.

* **/g X Y** : Moves the cursor to the cell located at coordinates 
  \(**X**;**Y**\), \(**0**;**0**\) being the top left console cell.

* **/k\[\_\] \[name\]** : Get keyboard input. When using **/k** subcommand, 
  **BATBOX** waits for a keyboard user input and sets the **name** variable to 
  a code associated with the press key. If no **name** parameter is supplied 
  to **BATBOX**, the command stops and return the key code through 
  **%ERRORLEVEL%**. The **/k\_** subcommand behaves the same way, except that 
  **BATBOX** does not waits for keystrokes. If no keystroke is available, the 
  **/k\_** command is skipped and **name** is left unmodified.

* **/l\[\_\] \[name\]** : Similar to **/k\[\_\]** subcommand, except that 
  **name** is set to the character associated with the keystroke. If the 
  keystroke can not be associated with a character, **name** is left 
  unmodified.

* **/w duration** : Delays for **duration** milliseconds.

* **/c color** : Changes the console text color to **color**. The color codes 
  used by this subcommand are the same as those used by the **COLOR** command. 
  However, the **code** must begin by **0x** to denote hexadecimal base.

* **/n** : Go to the next line. Move the cursor a row under where the last 
  call to **/g** subcommand has moved the cursor.

* **/h show** : Changes the cursor visibility. If **show** is **1**, the 
  cursor is visible; If **show** is **0**, the cursor is hidden.

* **/m\[\_\] \[X Y type\]** : Get mouse input. When using **/m**, **BATBOX** 
  waits for a click, and if **X**, **Y** and **type** have been specified, 
  **X** and **Y** are set to the coordinates of the click, while **type** is 
  set to a value representing the mouse button pressed:

  * 1 : Left click.

  * 2 : Right click.

  * 3 : Double left click.

  * 4 : Double right click.

  * 5 : Middle click.

  * 6 : Scroll up.

  * 7 : Scroll down.

  If **/m\_** is used, **BATBOX** also waits for mouse moves, and if so, set 
  **X** and **Y** to the new mouse position and **type** to one of the 
  previous values or **0** if the mouse has only moved.

  If neither **X**, **Y**, nor **type** is specified, **BATBOX** prints 
  **X:Y:type** to the current output, allowing this output to be processed by 
  a FOR loop as follows:

        FOR /F "tokens=1,2,3 delims=:" %%A in ('BatBox /m') DO (
         SET %3=%%C
         SET %2=%%B
            SET %1=%%A
        )

* **/y** : Old subcommand name for **/m\_**.

Several subcommands can be mixed, as sugested by **...** in the command line. 
To mix subcommands, just specify several command one after another just as 
follows:

    BATBOX /g 10 10 /d "Hello world" /g 0 0

This notations enables speed and size gains and makes the commands really 
versatile.

**BATBOX** 5.x is planned to come in two versions:

* As an external executable designed to provide a working command on 
  **cmd.exe**, however, this version suffers from slow execution speed since 
  it is external, and is not compatible with **Dos9**.

* As a module for **Dos9**. This new format allows significant performances 
  improvements since older **3.x**, **4.x** and **2.x** versions, running 
  nealy 50 times as fast as the older counterparts. In addition, this module 
  is shipped with **Dos9**. However, before being able to use **BATBOX**, the 
  module **modules/batbox** must be loaded using:

        MOD modules/batbox

However as of version 5.0, the external version designed to be used with 
**cmd.exe** is not released but its release is planned for version 5.1. 

## Numbers ##

Some subcommands require numbers to be passed to **BATBOX**. Such numbers can 
be specified in three numeral bases with the following prefixes :

* **0x** : Denotes an hexadecimal number.

* **0** : Denotes an octal number.

* Else the number will be processed as a decimal number. 

For theses reasons, it is important to prepend the **0x** suffix when dealing 
with the **/c** subcommand to specify hexadecimal notation.

## History ##

The very first batbox command was programmed by Romain Garbi \(also known as 
DarkBatcher\) around the end of 2010 using C as programming language. The 
version 1.0 was released around the end of 2011 on the batch.xoo.it forum and 
had a little success thanks to its versatily but was quite handicaped by its 
big binary. Several minor version where released in order to lower the size of 
the binary.

To continue reducing the footprint of the command, a new version \(2.0\) 
entirely written in assembly language was released in april 2012. This allowed 
Batbox binary to become as little as 1.5 kB so it could be embedded in batch 
scrips. This new version met quite a lot of success among batch programmers. 
The command was regularly updated until march 2015, when version 3.1 was 
released, almost reaching the limits of the command architecture.

As a replacement for the old command, Romain Garbi started to develop a new 
command, superbox, that read commands through a named pipe instead of using 
command parameters. A beta was released in march 2015 but the command 
development was dropped because input commands caused data races with cmd.exe.

A command inspired by batbox and superbox, called darkbox was released by 
Teddy Astie \(aka TSnake41\) on October 2017. This command successfully fixed 
the races problem by using unamed pipes. Making it a fast and reliable server 
and a very good replacement to batbox. 

After several years inactive, Romain Garbi started to develop a new 
experimental command, batbox4, to provide some innovative support to the old 
batbox command still being used. Based on the concept of lightweight server, 
this projet was dropped because it syntax was complex and darkbox already 
existed.

In november 2018, as modules features were starting to be added to the 
**Dos9** interpretor, a batbox module has been written, seeing in module the 
capability to make batbox more efficient and more flexible, resulting in 
version 5.x. This new implementation allows for new features such as setting 
environment variable in the parent interpretor.

## License ##

Batbox is provided under the GNU GPL license, copyrighted 2018 by Romain 
Garbi. Older versions are also licensed under the 3-clause BSD license.

Batbox uses libDos9 which code includes portions of darkbox by Teddy Astie.

