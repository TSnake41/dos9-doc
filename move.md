# MOVE command #

MOVE one or several files to another location.

## Synopsis ##

    MOVE [/-Y | /Y] [/R] [/A[:]attributes] source [...] destination

Move one or several files to another location.

* **/-Y** : Prompt the user for confirmation.

* **/Y** : Do not prompt the user for confirmation.

* **source** : The path of files to be moved \(can include [regular 
  expressions](spec/regexp)\).

* **destination** : The new path of the files \(can not include [regular 
  expression](spec/regexp)\).

  **destination** is considered to be the new path of the files, unless,

  * **destination** refers to a folder;

  * **destination** ends with **/** or **\**;

  * **source** refers to multiple source files;

  In any of the previous cases, **destination** is considered to be the folder 
  where files refered to by **source** must be move. Thus files resulting from 
  move will keep their original names.

* **/R** : Turn on recursive mode. This mode allow moving a complete tree. If 
  **sources** refers to various tree, then the tree will be merged in the 
  **destination** folder. If **source** is a [regular 
  expression](spec/regexp), then the static part of the regular expression 
  will be removed from files absolute path to produce relative path in 
  **destination** folder.

  As an example, if **source** is **path/to/folder/\*.\*** then the file 
  **path/to/folder/my/file** will be moved to **destination**/**my/file**.

* **/A\[:\]attributes** : Copies only files that match **attributes**. For 
  more details, check [files attributes](spec/attr).

## Notes ##

If an error occurs while moving a file, the **MOVE** command continues moving 
other file passed through **source**. Obviously, **MOVE** returns an error, 
but this behaviour can lead to mess on file, or even loss of data. For 
something that need to be bug prof, rather use a combination of [COPY](copy) 
and [DEL](del).

## Compatibility ##

Available since version **0.4**

Fully compatible with **cmd.exe**. The **/R** and **/A** switches are 
[Dos9](dos9) extension.

## See also ##

[DEL and ERASE commands](del), [COPY command](copy) 

