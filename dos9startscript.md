# %DOS9_START_SCRIPT% environment variable #

This page is discussing a topic affecting only **UNIX**-based OSes. The 
**%DOS9\_START\_SCRIPT%** variable specify a script to handle operating system 
file associations.

## Synopsis ##

    %DOS9_START_SCRIPT%

A variable containing the absolute path of a script used to handle operating 
system file assocation. This script is crucial to ensure [START 
command](start) and [Dos9](dos9) can run files that are not executable.

The script referred to by **%DOS9\_START\_SCRIPT%** is called with the 
following command line:

    %DOS9_START_SCRIPT% file [arguments ...]

* **file** : The file to be run.

* **arguments** : optionnals arguments specified or passed to **START**.

By default **Dos9** looks for available installed scripts to handle file 
association when it is compiled. And hardcodes one of the value of the 
detected script.

However, this value is overriden by the default [Dos9\_Auto.bat](dos9auto) 
which sets its value to **dos9\_start**.

If the variable is left undefined or erased, then all subsequent calls to 
non-executable file formats will fail. 

## Compatibility ##

Not compatible with **cmd.exe**, the initialization mechanisms differ.

Available since **0.7**.

## See Also ##

[Environment variables](spec/var), [Specifications Index](spec/index) 

