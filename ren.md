# REN and RENAME Commands #

**REN** and **RENAME** commands are used to rename files. Theses commands can 
only rename files, they can not move them.

## Synopsis ##

    REN file name.ext
    RENAME file name.ext

Renames **file**:

* **file** : A path referring to the file to be renamed. It can not be a 
  [regular expression](spec/regexp).

* **nom.ext** : The new name and extension of the file. The extension can be 
  omitted

## Compatibility ##

Available since **0.4**.

Fully compatible with **cmd.exe**

## See Also ##

[COPY Command](copy), [MOVE Command](move), [TYPE and MORE Commands](type) 
[DEL and ERASE Commands](del) 

