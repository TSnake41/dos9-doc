# DUMP command #

The **DUMP** command allows binary files to be dumped. It allows printing 
binary in various data types and in various numeric bases. It can be an 
interesting tool for generating embed file generators in batch.

## Synopsis ##

    DUMP [/H] [/T[:]type] [/B:format] [files ...]

Dump a file.

* **files ...** : A list of paths to the files to be dumped.

* **/H** : Enable hexadecimal dump mode. 

* **/T\[:\]type** : Specify the data type to be printed. It must be chosen 
  from the following list:

  * **C** : Byte.

  * **S** : Word \(2 bytes}.

  * **I** : Double-word \(4 bytes\).

  * **LL** : Quadruple-word \(8 bytes\).

  * **F** : Simple precision float.

  * **D** : Double precision float.

  Integral types can be prefixed by a **U** to specify that unsigned versions 
  of the types must be used.

* **/B:format** : Select the display format of the dumped files. The 
  **format** specifier must be a combination of the following:

  * **A** : display addresses.

  * **T** : display title.

  * **C** : display chars.

  * **Q** : quiet mode, do not display spaces.

By default, the printed text is configured like :

    DUMP file /T:C /H

## License ##

**DUMP** is free software distributed under the **GNU General Public 
License**.

## Authors ##

**DUMP** has been written in 2013 by **DarkBatcher** for the **Dos9 
Project**.

