# COPY command #

Copy one or several files to another location.

## Synopsis ##

    COPY [/-Y | /Y] [/R] [/A[:]attributes] source [+] [...] destination

Copy one or several files to another location.

* **/-Y** : Prompt the user for confirmation.

* **/Y** : Do not prompt the user for confirmation.

* **source** : The path of files to be copied \(can include [regular 
  expressions](spec/regexp)\). By using the **+** sign between at least two 
  paths, the behaviour of **COPY** will be affected as follows: instead of 
  trying to copy **source** into **destination**, the files referred to by 
  **source** will be concatenated in **destination**.

* **destination** : The path of the new files to be created \(can not include 
  [regular expression](spec/regexp)\).

  **destination** is considered to be the path of the destination files, 
  unless,

  * **destination** refers to a folder;

  * **destination** ends with **/** or **\**;

  In any of the previous cases, **destination** is considered to be the folder 
  where files referred to by **source** must be copied. Thus files resulting 
  from copy will keep their original names. If neither of these conditions are 
  met nor is the **/R** mode set, and **source** refers to multiple files, 
  then the files will be concatenated inside **destination**.

* **/R** : Turn on recursive mode. This mode allow copying a complete tree. If 
  **sources** refers to various tree, then the tree will be merged in the 
  **destination** folder. If **source** is a [regular 
  expression](spec/regexp), then the static part of the regular expression 
  will be removed from files absolute path to produce relative path in 
  **destination** folder.

  As an example, if **source** is **path/to/folder/\*.\*** then the file 
  **path/to/folder/my/file** will be copied to **destination**/**my/file**.

* **/A\[:\]attributes** : Copies only files that match **attributes**. For 
  more details, check [files attributes](spec/attr).

## Compatibility ##

Available since version **0.4**.

Partially compatible with **cmd.exe**. Some **cmd.exe** are ignored because 
they do not make sense anymore. The **/A** switch is a [Dos9](dos9) extension.

## See also ##

[DEL and ERASE commands](del), [MOVE command](move) 

