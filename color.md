# COLOR command #

The **COLOR** command changes the colours of both console's background and 
text.

## Synopsis ##

    COLOR [code]

Change console both background and text colours. The code **code** should be 
constituted of two character. The rightmost hexadecimal digit should represent 
the text colour and the leftmost should represent the console background 
colour. These characters must be one of the following values :

    0 : Black        8 : Grey
    1 : Dark blue    9 : Bright blue
    2 : Green        A : Bright green
    3 : Grey-Blue    B : Cyan
    4 : Maroon       C : Red
    5 : Dark red     D : Pink
    6 : Khaki        E : Yellow
    7 : Bright grey  F : White
    
    . : Current default color

If you don't specify **code**, then the **color** command will reset the 
colours to default \(That is **07** on windows platforms and depends of the 
terminal settings on unix platforms\).

The **.** specifier refers to the current default color, either background or 
foreground color. Note that a call to **COLOR** changes the default color, as 
such, the color referred to by **.** is not fixed across numerous calls to 
**COLOR**, as it is across [PROMPT](prompt) calls.

## Compatibility ##

Fully compatible with **cmd.exe**.

Available since version **0.7**.

## See also ##

[CLS command](cls), [ECHO command](echo), [Command list](commands) 

