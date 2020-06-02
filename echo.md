# ECHO command #

The **ECHO** command has various uses :

* Enable/disable current directory echoing.

* Show text in console.

## Synopsis ##

     ECHO [OFF|ON]
     ECHO text
     ECHO.text

Enables/disables current directory echoing \(i.e. **``DOS9 ...>''**\).

* **ON** : Enable

* **OFF** : Disable

Show text in console.

* **text** : Text to be printed. If you use **ECHO.**, the **text** can be 
  void, in this case, [Dos9](dos9) will print an empty line.

## Compatibility ##

Fully compatible with **cmd.exe**.

## See also ##

[PAUSE command](pause),[SET command](set),[TITLE command](title),[CLS 
command](cls),[Command list](commands) 

