# Timeout command #

The **TIMEOUT** command sleeps for a delay specified in seconds, or until the 
user presses a key.

## Synopsis ##

    TIMEOUT [/T] [/NOBREAK] seconds[.milliseconds]

Wait for **seconds.millisecond** or for a keystroke to resume the execution.

* **/T** : Has no effect. provided for compatiblity only.

* **/NOBREAK** : Do not stop the delay when a keystroke is detected.

* **seconds** : The duration to wait specified in seconds.

* **.milliseconds** : An optional supplement to **seconds** specifying extra 
  milliseconds duration. This feature is a [Dos9](dos9) extension. 

## Compatiblity ##

Compatible with **cmd.exe**.

Available since **218.2**.

## See also ##

[List of Dos9 command](commands)

