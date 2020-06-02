# Files attributes #

Every file has specific files attributes defined by operating systems. 
[Dos9](../dos9) can handle these attributes to change the behaviour of command 
scripts.

\[Warning:} All these attributes are not portable on Unix-like system. Anyway 
if you choose to use them, they will just be ignored by the interpreter.

## Synopsis ##

Usualy, [Ds9](../dos9) provides a standard switch to specify attributes 
filters. The syntax is:

    /a[:]attr

The use of the column is not mandatory but it is recommanded for readability 
reasons.

* **attr** : A sequence of letters \(optionnally preceded by hyphen **-** to 
  discard an attribute\).

## Attributes ##

The following letters denote the following :

* On windows **WINDOWS** and **UNIX-like** systems:

  * **D** : is a directory.

  * **R** : is read-only.

  * **I** : is empty.

* On windows **WINDOWS** systems:

  * **H** : is hidden.

  * **S** : is system.

  * **A** : is an archive.

  * **L** : is an analyse.

You can select file not having an attributes by prefixing the letter by an 
hyphen **-**.

## Example ##

    /A:R-I

Select read-only files that are not empty.

## Compatibility ##

Available since **0.4.0.2**.

Compatible since **cmd.exe**.

## See also ##

[Specification index](index), [DIR Command](../dir), [DEL Command](../del) 

