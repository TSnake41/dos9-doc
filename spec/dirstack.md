# Directories stack #

The **directories stack** allow saving and retrieving directory on a stack. 
This is useful in case one needs to move inside a directory and then return to 
the previous directory. It can also be used to detect if a directory exists 
without using [if exist](../if).

## Push or pop a directory on the stack ##

As a directory is pushed on the stack, it will get on the very top of the 
stack. The last insterted directory is then on the top.

As a directory is poped off the stack, the one preceding it is grabbed and 
used as the new current directory.

Example:

    cd dir1/
    :: We are in dir1/
    
    PUSHD dir2/
    :: dir1/ is pushed on the stack and the current directory 
    :: becomes dir2/
    
    PUSHD ..
    :: dir1/dir2/ is pushed on the stack and the 
    :: current directory becomes dir1/
    
    :: The stack now contains (from top to bottom)
    ::  - dir1/dir2/
    ::  - dir1/
    
    POPD
    :: current directory becomes dir1/dir2
    
    POPD
    :: current directory becomes dir1/
    :: the bottom of the heap is reached

## Compatibility ##

Fully compatible with **cmd.exe**.

## See also ##

[PUSHD Command](../pushd), [POPD Command ](../popd), [Specifications 
index](index) 

