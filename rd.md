# RD and RMDIR commands #

Removes a directory.

## Synopsis ##

    RMDIR [/S] [/Q] directory
    RD [/S] [/Q] directory

Removes a directory.

* **directory** : The folder to be suppressed.

* **/Q** : Enable silenced mode; do not prompt the user for confirmation.

* **/S** : Deletes files and subfolders contained by **directory**. Use this 
  switch to delete an entire tree.

## Notes ##

By default, **RD** and **RMDIR** do not delete non empty folder. To force 
folder deletion, use the **/S** switch.

## Compatibility ##

Available since **0.4** revision.

Fully compatible with **cmd.exe**.

## See also ##

[MD and MKDIR commands](md), [DEL and ERASE commands](del), [MOVE 
command](move) 

