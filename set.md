# SET command #

The **SET** command can display, set, or remove environment variables that can 
be later retrieved through [variable expansion](spec/exp).

## Synopsis - Simple set ##

    SET variable[=[content]]

Assign **content** to variable **variable**. If **content** is not specified, 
the the variable **variable** is removed from the environment.

If neither the equal sign nor **content** are specified, **SET** will list 
variables which name begin with **variable** and their content.

The way **SET** deals with quotes and spaces is a bit special and inherited 
from cmd's **SET** behaviour:

* if **variable** is followed by trailing spaces before the equal sign, theses 
  spaces will be removed;

* However if spaces or blanks follow the equal sign, they will be kept.

* Quotation marks on the right-hand-side of the assignment will not be 
  affected unless there is also a quotation mark preceding **variable**, in 
  which case, **content** will be trimmed at the last occurrence of a 
  quotation mark.

## Synopsis - Arithmetic evaluation ##

    SET /a[[:][i|f]] variable=expression

Computes the value of the arithmetical expression **expression** and assign 
its value to variable **variable**. This command behaviour depends on mode set 
through [SETLOCAL](setlocal) command \(parameter **ENABLEFLOATS**\).

Options can be given in addition to **/a**. These options are:

* **i** : Force use of **integer** mode, regardless of mode set through 
  [SETLOCAL](setlocal).

* **f** : Force use of **float** mode.

To get extended help about **arithmetical expressions**, please see the 
following manual pages: [SET \(/a\)\(integers\)](setai) and [SET 
\(/a\)\(floats\)](setaf).

    SET /p variable=question

Prompt **question**, wait for an input from user and assign it to the variable 
**variable**.

## See also ##

[Command list](commands), [ECHO command](echo), [PAUSE command](pause), [SET 
command \(/a\)\(integers](setai), [SET command \(/a\)\(floats\)](setaf).

