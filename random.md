# %RANDOM% Variable #

The **%RANDOM%** variable generates a random number.

## Synopsis ##

    %RANDOM%

Gets expanded into a random generated number ranging from **0** to **32767** 
on Windows \(On Unix-like, the upper bound depends on the implementation\). 
The number changes every time a variable is expanded even during [delayed 
expansion](spec/exp).

## Compatibility ##

Compatible with **cmd.exe**

Available since **0.7**.

## A voir aussi ##

[Variables d'environement](spec/var), [Index des spécifications](spec/index) 

