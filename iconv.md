# ICONV / GNU ICONV command #

**GNU Iconv** is a free software maintained and developped by the **GNU** 
project and the **Free Software Foundation**. **ICONV** allows converting 
files from encoding to encoding, and provide a large set of encoding.

This is really helpfull when you want to port batch scripts between platforms 
because for exemple, GNU/Linux uses **UTF-8** charset whereas WINDOWS uses a 
various set of codepages, as **CP863** for western europe.

**Iconv** is distributed as a free software by the **GNU** project, and 
licensed under the terms of the **GNU GPLv3**

## Synopsis ##

     ICONV [-c] [-s] [-f encoding1] [-t encoding2] [fichier]
     ICONV -l

Converts a file from an encoding to another one.

* **-c** : Silently ignore characters that can't be converted to destination 
  encoding.

* **-s** : Ignore errors messages caused by character conversion error, but 
  places this characters on se destination text though.

* **-f encoding1** : Set **encoding1** as source encoding.

* **-t encoding2** : Set **encoding2** as destination encoding.

* **-l** : Outputs a list of all supported encoding.

## Compatibility ##

Avaliable since version **0.7**.

Uncompatible with **cmd.exe**, this command comes from the gnu operating 
system.

## See also ##

[NANO / GNU Nano editor](nano), [HLP command](hlp) 

