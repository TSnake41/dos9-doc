# DEL and ERASE commands #

Delete one or more files.

## Synopsis ##

    DEL [/P] [/F] [/S] [/Q] [/A[:]attributes] name ...
    ERASE [/P] [/F] [/S] [/Q] [/A[:]attributes] name ...

Delete one or more files.

* **/P** : Ask confirmation before deleting file.

* **/F** : Force read-only files deletion.

* **/Q** : Do not ask confirmation when using [regular 
  expressions](spec/regexp).

* **/A\[:\]attributes** : Delete only the files that match the specified 
  attributes. Check [regular expression](spec/regexp) for more information.

* **/S** : Recursive mode. Deletes files in folders and sub folders.

* **name** : A list of files to be deleted. Paths can include [regular 
  expressions](spec/regexp). If any of the paths specified refer to a 
  directory, every file inside that directory is deleted.

## Compatibility ##

Available since revision **0.4**.

Fully compatible with **cmd.exe**.

## See also ##

[RD and RMDIR commands](rd), [MD and MKDIR commands](md), [MOVE 
command](move) 

