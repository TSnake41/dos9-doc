# MORE command #

The **MORE** command displays output on a per screen basis. **MORE** can also 
be used in the same way as **TYPE** to print a file to the terminal.

## Synopsis ##

    MORE [/E] [/C] [/P] [/T[:]n] [/S] [/A] [/U] [+n] [files ...]

Displays output one screen at a time, pausing between two screens.

* **/E** : Enable extended mode. This switch should be specified each time you 
  need to use switches **/C**, **/P** and **/S**, or the **+n** parameter. 
  However, this switch is ignored by [Dos9](dos9), it is only provided for 
  compatibility reasons.

* **/C** : Clear screen before printing a new screen. This switch is ignored 
  if the output of **MORE** does not refer to a terminal device \(eg. if 
  output is redirected or sent through a pipe}. Uppon use of this switch, you 
  can only access full screen scrolls \(scrolling screen by screen as opposed 
  to line by line\).

* **/P** : Develop form-feed characters. This switch is not supported by 
  [Dos9](dos9), and is ignored instead

* **/S** : Squeezes multiples blank lines into a single line.

* **/T\[:\]n** : Expands tabs to **n** spaces.

* **+n** : Display files starting at line **n**.

* **/A** : Count ANSI escape codes as printed characters.

* **/U** : Do not consider text to be utf-8. Consider instead that it is 
  byte-based encoding. 

* **files ...** : A list of files to be displayed \(possibly containing 
  [regular expressions](spec/regexp). If **files** is empty, then **MORE** use 
  the standard input as input.

If standard output is not redirected, then the **MORE** command uses it 
interactive more \(the command prompts the **MORE** prompt\).

    -- MORE --

**MORE** accepts the following commands:

* **Pn** : Display next **n** lines.

* **Sn** : Skip next **n** lines.

* **F** : Display next file.

* **=** : Show line number.

* **Q** : Quit.

If [Dos9](dos9) has been compiled with **--disable-console**, then the 
**more** command should always use the **/C** switch, Thus, line by line 
scrolling should not be possible.

## Compatibility ##

Compatible with **cmd.exe**, excepting **/P** switch that does nothing.

Available since **2014.0.9b** revision. Before **MORE** was only a 
[TYPE](type) alias.

## See also ##

[Command list](commands), [TYPE command](type), [DUMP command](dump)

