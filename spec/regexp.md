# Regular expressions #

**Regular expressions** are a way to peek some elements following a specific 
syntax among a set of elements. They allow elements or files to be selected 
using an **expression**.

**Regular expressions** provided by [Dos9](dos9) are based on those provided 
by **cmd.exe**. As such, they are considerably less flexible than 
state-of-the-art regular expressions like **PCRE**.

## Syntax ##

**Regular expressions follow the following syntax**.

    expresion

Where **expression** is made of any sequence of characters. Some characters 
have special meaning:

* **\*** : Accepts any character sequence \(may be an empty sequence\).

* **?** : Accepts any character.

* For any other character in **expression**, the string to be checked must 
  contain exactly the same character in the same position.

When **\*** is used, [Dos9](../dos9) uses the shortest correspondence between 
the **expression** and the string to test. As an example the string 
**atest\_test** does not match the expression **u\*test** whereas it matches 
the expression **u\*\_test**.

It is possible to specify some kind of absurd combinations such as **?\*** or 
**\*\***, these are treated like a single **\***.

## File search expressions ##

**Regular expressions** can be used to search files in directories. In this 
case, any directory delimiter \(eg. **\** or **/**\) is used to cut 
**expression** in smaller tokens, which are used to search files within the 
directory tree.

As an example, the following **regular expression** will be executed as 
described below.

    my/regu*/expressi?n/*

* **my** : **Dos9** looks for a file nammed **my** in the current directory.

* **regu\*** : **Dos9** looks for directories which name matches **regu\*** 
  \(ie. name beginning by the string "regu"\) in **my/** folder

* **expressi?n** : **Dos9** looks for directories which name matches 
  **expressi?n** inside the set of directories found previously.

* **\*** : **Dos9** looks for files and directories which name matches inside 
  the set of directories from the previous set.

A recursive mode is available for file search, in this case, all the tokens 
excepting the last one are used to find directories where the recursive search 
will take place. Then, **Dos9** searches recursively for any file or directory 
matching the last token within the search directories.

If we consider the same expression:

    my/regu*/expressi?n/*

* **my/regu\*/expressi?n/** : **Dos9** looks for directories that match 
  **my/regu\*/expressi?n/**

* **\*** : Dos9 looks for any directories or files inside the directories 
  found at the previous step which name matches **\***.

## Note ##

Currently **Dos9** include no backtracking systems, meaning that it is always 
the most greedy possible. In addition, using **cmd.exe** the expression 
**\*.\*** is a bit specific because it basically means "only files". This is 
not included inside windows thanks to the wide support of [files 
attributes](attr).

## Compatibility ##

Almost compatible with **cmd.exe**.

Available since **0.7.2**.

## See also ##

[DIR Command](../dir), [List commands](../commands), [Specification 
index](index) 

