# PROMPT Command and %PROMPT% Variable #

The **PROMPT** command and the **%PROMPT%** enable changing the text of the 
command prompt.

## Synopsis ##

    PROMPT prompt_format
    SET PROMPT=prompt_format

The **PROMPT** command is equivalent to a call to [SET](set) modifying the 
**%PROMPT%** variable. The new format is specified through 
**prompt\_format**, that can be any sequence of characters where the following 
sub strings will be expanded:

* **$a** : Expands to **&**.

* **$b** : Expands to []().

* **$c** : Expands to **\(**.

* **$d** : Expands to the content of [%DATE% variable](time).

* **$e** : Expands to an escape character \(code 27\).

* **$f** : Expands to **\)**.

* **$g** : Expands to **>**.

* **$h** : Expands to a backspace character.

* **$l** : Expands to **<**.

* **$n** : Expands to current drive \(root, if the OS running [Dos9](dos9) 
  does not provide an equivalent for the windows concept\).

* **$p** : Expands to the current working directory.

* **$q** : Expands to **=**.

* **$s** : Expands to a space.

* **$t** : Expands to the content of [%TIME% variable](time).

* **$u** : Expands to the content of [%USERNAME% variable](dos9var). That is, 
  if not modified, the current user name.

* **$w** : Expands to the content of [%USERDOMAIN% variable](dos9var). That 
  is, if not modified, the current user domain name.

* **$xCODE;** : Changes locally the color of the text displayed according to 
  **CODE**, where **CODE** is a code that can be accepted by the [COLOR 
  command](color). Changes of color using this method will not affect the 
  **.** specifiers values. The original color of text is not restored after 
  displaying the prompt, but you can restore default values using **$x..;**.

* **$\_** : Expands to a new line.

* **$$** : Expands to **$**.

* **$+** : Prints as many **+** as pushed directories inside the [directory 
  stack](spec/dirstack).

**PROMPT** without arguments resets **%PROMPT%** variable to its default 
value.

## Compatibility ##

Mostly compatible with **cmd.exe**. However, the **$m** specifier is 
unsupported. In addition, **$xCODE;** specifier is a [Dos9](dos9) extension.

Available since **218.2**.

## See also ##

[Commands list](commands)

