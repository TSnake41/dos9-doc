# CALL command #

The **CALL** command enables label or command file execution within the 
current command promp context \(e.g. the command executed can change 
[environment variables](spec/var) values of calling script\).

## Synopsis ##

    CALL [/e] [file] [:label] [parameters ...]

Call either the file **file** or the label **:label** within the current 
**Dos9** context.

* **file** : A path to the file to be executed. If the label name **:label** 
  and the **/e** switch have been specified, then **Dos9** will serach the 
  given label in **file**.

* **:label** : A label where the command file execution will be started. If 
  neither **file** nor **/e** have been specified, then **:label** is to be 
  searched on the current file.

* **/e** : Indicate that both **file** and **:label** have been specified. 
  This switch avoid ambiguous behaviour toward parameter. By default, 
  **Dos9** will only take in account the very firs parameter. This switch has 
  no effect if not specified in first or second position, it will be 
  considered as a parameter to be passed in **parameters**.

* **parameters ...** : The parameters to be passed to the called script. The 
  parameters will be passed through **%1** - **%9**. You can give at most 9 
  parameters, that is largely sufficient.

The specified script will be executed in the current **Dos9** context. That 
means, it will be able to modify [environment variables](spec/var) but not 
[special variables](spec/xvar)/

The ability to provide either **file** and **:label** are a **Dos9** 
extension. You can get a **cmd.exe** compatible behavior by setting the option 
**CMDLYCORRECT** from the command [SETLOCAL](setlocal).

## Compatibility ##

Compatible with **cmd.exe**, exception made for the **/e** switch.

Available since version **2014.0.9**.

## See also ##

[FOR command](for), [IF command](if), [GOTO command](goto)

