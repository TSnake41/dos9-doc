# DIR command #

The **DIR** command lists the content of a folder, and select files froms 
attributes, or name using [regular expression](spec/regexp).

## Synopsis ##

     DIR [/A[:]attributes] [/S] [/B] [path]

Search and list files and folders.

* **path** : Path of the files or folders to seek. This can contain [regular 
  expressions](spec/regexp). If no file is specified, then [Dos9](dos9) will 
  show current folder's content.

* **/A\[:\]attributes** : Specifies a list of attributes that determines files 
  and folders that will be listed. For more informations, see 
  [/A\[:\]attribute switch](spec/attr).

* **/B** : Simplified output. Output only files and folders name, without 
  printing date, size, nor attributes. This switch eases the processing by a 
  [FOR](for) loop.

* **/S** : Sets recursive search. See [regular expressions](spec/regexp) for 
  more informations.

## Compatibility ##

Supported since **0.4** version.

Mostly compatible with **cmd.exe**. Nevertheless, many switchs used to change 
output style are not supported.

## See Also ##

[Commande COPY](copy), [Commandes REN et RENAME](ren), [Commande Move](move), 
[Commandes DEL et ERASE](del) 

