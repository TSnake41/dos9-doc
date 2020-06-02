# HLP Command #

The **HLP** command print command help. It is a batch script acting as a 
front-end of the [TEA](tea) command.

## Synopsis ##

    HLP [name | /b language [encoding] | /l | /d]

Print a manual page.

* **name** : The name of the manual page to be printed.

* **/b** : Build documentation for a given language and a given encoding. This 
  switch is used to produce files from [TEA](tea) documents shipped with 
  **Dos9**. The parameters that can be specified are:

  * **language** : The language in which the documentation will be generated. 
    A list of languages available can be obtained through the **/l** switch.

  * **encoding** : The encoding that will be used by generated manual pages. 
    This parameters requires [GNU iconv](iconv) to be installled. The default 
    encoding is **utf-8**. This parameter is usefull if your terminal does not 
    support **utf-8** encoding.

* **/l** : Print a list of all languages avaliable on the current machine. 
  Available languages are shown through **POSIX** locales, that is in form of 
  **language\_COUNTRY** where **language** and **country** are both 
  abbreviations.

* **/c** : Configures **hlp.bat** command parameter. Prompt the user for the 
  selected language, format \(html, text or ansi\) and encoding to be used. 
  This option is an user-friendly way to configure the configuration file 
  **%USERPROFILE%/.dos9/hlp/hlp.conf.bat**.

## Config file ##

    %USERPROFILE%/share/hlp/hlp.conf.bat

A batch script defining hlp setting through a set of variables. This file can 
be generated using the **/c** switch. This file is run on **hlp.bat** startup. 
Variables that must be set are the following:

* **%mode%** : The file format to be used by **hlp.bat**. It must be one of 
  the following three formats:

  * **html** : Help pages will be displayed through an html medium and a web 
    browser. This requires a web browser and a working **start** command.

  * **ansi** : Help pages will be displayed at the command prompt, using ANSI 
    escape codes for formatting. This obviously requires an ANSI-compatible 
    terminal. -- **txt** : Help pages will be displayed at the command prompt 
    using plain text

* **%locale%** : The language of help pages using a **POSIX** local \(e.g 
  **language\_COUNTRY**\). The corresponding locale has to be installed in 
  **%DOS9\_PATH%/share/hlp/man**.

* **%view\_cmd%** : The command to be used for Help pages display. This can 
  either be an internal or an external command. By default, **hlp** uses :

        set view_cmd=!%mode%_prg!

  Where variables **%txt\_prg%**, **%html\_prg%** et **%ansi\_prg%** define 
  the commands to be executed for every format.

## Compatibility ##

**HLP** is not compatible with **cmd.exe**

Available since version **2014.0.9b**.

## See also ##

[HELP command](help), [TEA command](tea)

