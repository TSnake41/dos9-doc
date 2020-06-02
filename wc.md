# WC Command #

The **WC** command display count of a files \(size, number of lines or 
words\).

## Synopsis ##

    WC [/L] [/C] [/M] [/W] [files ...]

Print files counts and the associated total if several **files** have be 
specified.

* **files ...**: A liste of paths referring to the files which counts will be 
  printed. This path may contain [regular expression](spec/regexp). If no 
  files have been specified, Dos9 will show standard input counts.

* **/L**: Display the number of lines.

* **/C**: Display the number of bytes.

* **/M**: Counts characters on an utf-8 basis. If Dos9 have not been compiled 
  with utf-8 support, this option is identical to **/C**.

* **/W**: Display the number of lines.

The counts are printed in the following order. If any count have been omited, 
these are not displayed by the command.

    line_number word_number byte_number character_numbers file

If no switch was supplied to Dos9, the default command is:

    WC /C files ...

## Compatibility ##

Not available on **cmd.exe**. Available since **217.1**.

## See Also ##

[Command list](commands), [XARGS command](xargs) 

