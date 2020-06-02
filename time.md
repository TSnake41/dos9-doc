# %DATE% and %TIME% variables #

The **%DATE%** and **%TIME%** environment variable expand to current date and 
time.

## Synopsis ##

    %TIME%

Expands to the current hour, using appropriate locale format. \(usually 
**HH:MM:SS,cc**\). The support of centiseconds depends on the platform. Since 
version **218.2** centiseconds are supported using windows, though this is 
still not the case for \*nixes. Note that the **%TIME%** variable includes 
leading **0** for hours also. 

    %DATE%

Expands to current date, using appropriate locale format. Leading zeros are 
also added between fields.

## Note ##

**%TIME%** and **%DATE%** are dynamic variables, meaning that they are 
generated during the [variable expansion](spec/exp). Thus these variables can 
not be modified using [SET](set).

## Compatiblity ##

Compatible with **cmd.exe**.

Available since **0.7**

## See also ##

[Environment variable](spec/var), [Specification index](spec/index)

