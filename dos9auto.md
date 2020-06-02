# Dos9 Initialization (Dos9_Auto.bat) #

[Dos9](dos9) is initialized through the execution of a batch script named 
**Dos9\_Auto.bat**. This file sets some variables and calls user defined 
scripts.

## Synopsis ##

    %DOS9_PATH%/Dos9_Auto.bat

This file is not meant to be edited directly, since it calls user defined 
scripts. It can be nonetheless useful to modify it to fit some special 
requirements. If you modify it, be careful not to do anything wrong with it as 
it can eventually affect the behaviour of some scripts.

Usually, the file **Dos9\_Auto.bat** sets [Dos9 global variables](dos9var) 
that are not dynamic.

Finally **Dos9\_Auto.bat** also call two user defined scripts :

* **%USERPROFILE%/.dos9/Dos9\_Auto.bat** : User startup file

* **%DOS9\_ETC%/Dos9\_Auto.bat** : System wide startup file.

In both of these script, any [Dos9 command](commands) can be used safely.

Note that since the first multi-threaded release **218.1**, the execution of 
**Dos9\_Auto.bat** has changed a lot. The script gets executed upon either:

* **Dos9** start-up, that is when a new interpreter is launched without 
  parents.

* or **Dos9** is **explicitly** called from a script or from the prompt. This 
  means **Dos9\_Auto.bat** does not get executed any more upon 
  [pipe](spec/condop) call or [FOR](for) command. 

## Compatibility ##

Not compatible with **cmd.exe**, the initialization mechanisms differ.

Available since **0.7**.

## See Also ##

[Environment variables](spec/var), [Specifications Index](spec/index) 

