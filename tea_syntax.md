# TEA language specification #

The **TEA language** is the language used for formatting [TEA](tea) source 
files. It is a really simple markup language intended to be used with 
[Dos9](dos9).

## Block delimiters ##

    {{...}}
    
    ${...}
    
    - ...
    
    ...

**Block delimiters** are used to change paragraph type. A paragraph is formed 
by a group lines of text following each other without a blank line. There is 4 
types of block delimiters.

* **{{...}}** : Denotes a title.

* **${...}** : Denotes a block of code.

* **- ...** : Denotes a list. Several list can be nested by using two or more 
  minus signs. It is possible to hide the **-** by using a **@** before them.

* **...** : Denotes a normal paragraph.

## Inline delimiters ##

    {foo}
    {target|text}

**Inline delimiters** are used to add features to a paragraph. They can not be 
used in a **code block** though. There is two of them:

* **{foo}** : Denotes an emphasis on **foo**

* **{target|text}** : Denotes a link. The parameter **text** is used as the 
  text representing the link while **target** is the path to the target of the 
  line. If **target** specifies no file extension, **TEA** will automatically 
  add an appropriate extension unless the link begins with **http://**, 
  **https://** or **mail://**.

## Comments ##

Comments can be introduced using the **#** character

    # comment

It is important that the dash **#** is at the first column of the source file 
for [TEA](tea) to interpret it as a comment.

## Escaping ##

Any character can be escaped using **\**.

## See Also ##

[TEA Command](tea) 

