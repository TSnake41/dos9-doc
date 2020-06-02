# Dos9 command #

**Dos9** is a free, cross-platform command prompt used for batch scripts and 
command processing.

**Dos9** is a free software, designed to be as compatible as possible with 
**cmd.exe** proprietary software from **Microsoft**.

## Synopsis ##

     DOS9 [/A[:]attr] [/i input] [/o output] [file] [/ commande | /k command]

Run a command file or wait for an user input.

* **file** : Path of the batch script to be run.

* **/c command** : Run **command** and exit **Dos9**.

* **/k command** : Run **command** and stay active.

* **/A\[:\]attr** : Some attributes to set **Dos9** behaviour:

    **v** : Enables [delayed expansion](spec/var).

    **c** : Enables **CMDLYCORRECT** option from the [SETLOCAL](setlocal) 
    command. This forces **cmd.exe** compatible mode.

    **f** : Enables [floating numbers](spec/exp).

    **e** : Disable current directory echoing.

    **q** : Run Dos9 quietly \(ie. does not show the intro screen at 
    startup\).

* **/i input** : redirects standard input to file descriptor **input**.

* **/o output** : redirects standard output to file descriptor **output**.

## Compatibility ##

Compatible with any version of **Dos9**. Incompatible with **cmd.exe**.

**Dos9** is cross-platform so that it can be run either on **MS-WINDOWS** or 
**GNU/Linux**. Moreover, Dos9 should be easily portable to operating systems 
that support either **POSIX** \(and define **\_POSIX\_C\_SOURCE**\) or a 
**MS-WINDOWS** compatible API, including any POSIX-compatible function that is 
provided by it.

## License ##

**Dos9** is a free software distributed under [GNU General Public 
License](http://www.gnu.org/licenses/gpl.html) terms. For more informations 
about free software's philosophy, see [Free Software 
Fundation's](http://www.fsf.org) website.

## Author ##

**Dos9** have been written since 2010 by **Darkbatcher \(Romain Garbi\)**. It 
uses severals helpful free libraries from the [GNU operating 
system](http://www.gnu.org/), mostly 
[libmatheval](http://www.gnu.org/software/libmatheval/), 
[gettext](https://www.gnu.org/software/gettext/).

Dos9 uses a few open-source project. Theses project include GNU Iconv, GNU 
Gettext, GNU libmatheval, and linenoise. Dos9 also includes a few functions 
from **darkbox** by TSnake41.

## See Also ##

[ECHO Command](echo), [Commands list](commands) 

