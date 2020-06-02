# MD and MKDIR commands #

Creates a new directory.

## Synopsis ##

    MD directory
    MKDIR directory

Creates a new folder.

* **directory** : Path of the directory to be created. If **directory** 
  contain several folder names that do not already exist, these are created 
  either. For example, if neither **a**, **b** nor **c** are existing, then:

        MD a/b/c

  Is the same as :

        MD a
        MD a/b
        MD a/b/c

## Compatibility ##

Available since version **0.4**.

Fully compatible with **cmd.exe**.

## See also ##

[RD and RMDIR command](rd), [DEL and ERASE command](del), [MOVE 
command](move), [COPY command](copy) 

