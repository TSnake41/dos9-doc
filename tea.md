# TEA Command #

The **TEA** \(Tea Expands Ascii\) command is a text preprocessor allowing easy 
and fast formating for documents \(either text or html\).

The **TEA** markup language is lightweight and designed to be simple to learn 
and to understand, allowing the preprocessor to have the tiniest size as 
possible.

## Synopsis ##

    TEA source [output] [/E[:]encoding] [/O[:]mode]

Creates a text or HTML document from the **source**.

* **source** : The source file that **TEA** will preprocess \(this file should 
  be using [TEA syntax](tea\_syntax)\)

* **output** : The file that **TEA** will generate. You have to specify the 
  correct extension for the file as **TEA** does not use this to determine the 
  type of the output.

* **/E\[:\]encoding** : Specify the encoding that should be used to process 
  the text. The encoding can be :

  * **UTF-8** : Use utf-8. If you choose this encoding, then any BOM will be 
    ignored from **source**.

  * Any other encoding will be treated as a single-byte encoding.

* **/O\[:\]mode** : Chooses an output format

  * **TEXT** : Produce a text file without coloration. Characters are used to 
    denote the formating and target of links are integrated in the file. This 
    is the defautlt Output

  * **TEXT-PLAIN** : Produce a text file that is more easy to read but with 
    less formating

  * **TEXT-ANSI** : Produces a text file formated using ANSI escape code so 
    that it is readable on any compatible terminal.

  * **HTML** : Produces a HTML document.

## Synopsis - HTML Options ##

You can specify some more option for HTML generation, which are the following 
:

    TEA source output /O:HTML [/M meta] [/H head] [/F foot] [/T title] [/C[:]mode]

Where :

* **/M meta** : A file to include within the <head> tag of **output**.

* **/H head** : A file to include just after the <body> tag of **output**.

* **/F foot** : A file to include just before the </body> tag of **output**.

* **/T title** : Specifies a prefix that should be added to the title.

* **/C\[:\]mode** : Chooses some compatibility mode \(default output is 
  HTML5\)

  * **HTML4** : Generate a valid HTML4.1 file

  * **XHTML** : Generate a valid XHTML file

  * **MD** : Generate a valid markdown file for **dos9.org**

## TEA Syntax ##

The tea syntax is described in [TEA Syntax](tea\_syntax) page.

## Auteur ##

**TEA** was developed by Romain GARBI, it is free software

## À voir aussi ##

[Dos9](dos9), [TEA Syntax](tea\_syntax) 

