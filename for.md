# FOR Command #

The **FOR** loop is the most powerfully tool provided by batch language to 
process various types of data, from integers, text files, command outputs and 
even directories. Thus, the **FOR** loop is an important piece to elaborate 
advanced and complex batch scripts and commands.

The **FOR** loops may seem difficult to understand and mysty for beginners, 
however, it is a very powerful tool for batch programmers.

If you wish to have more detailed description of the **FOR** loop syntax, 
please consider reading [FOR \(technical\)](for-tech)

## Synopsis - First Syntax ##

    FOR %%A IN (string) DO (
     :: some commands
    )

Split **string** in tokens and processes specified commands for each token.

* **%%A** : The name of the special var that will receive the token to be 
  processed with specified commands.

* **string** : The string to be split in tokens. The delimiters used split the 
  string in tokens are :

  * **' '** : Spaces.

  * **' '** : Tabs.

  * **'\n'** : Line feeds or new lines.

  * **:** : Columns.

  * **;** : Semi-columns.

  * **,** : Coma.

  Note that you can discard any of the previous delimiters \(expects line 
  feeds or new lines\) just by enclosing the token between single or double 
  quotes. Note also that the double or single quote will remain in the tokens 
  processed, to avoid this, just use **%%~A** instead of **%%A** \(for more 
  details see [special variables](spec/xvar)\).

Example : 

    FOR %%A IN (some stuff "some stuff") DO (
     ECHO The current token is %%A
    )

Output: 

    The current token is some
    The current token is stuff
    The current token is "some stuff"

## Synopsis - Second syntax ##

    FOR /F [options] %%A IN (object) DO (
     :: some commands
    )

Processes either a string, a command output or a file. For convenience, and to 
ease reading of the page, none of the previously described parameters will 
described again.

* **object** : The object to be processed by the **FOR** loop. This parameters 
  consist of a string that can be \(or not\) enclosed in only one type of the 
  following delimiters :

  * **'** : The object **object** is considered as a command line. The 
    **FOR** loop will run the given command line and then process the output 
    of the command line.

  * **"** : The object **object** is considered as a simple string. The 
    **FOR** loop will so process the string. If the string include either line 
    feeds or new lines, then they will not be split from the processed string, 
    and the string will be processed line-by-line.

  * If neither of the previous delimiters encloses **object**, then object 
    will be considered as a file name. The **FOR** loop will open the file 
    named by **object** and read all its content, and finally process what 
    have been read.

* **options** : The options that must be used by **FOR** to process 
  **object**. This must be, either a single parameter that gathers all options 
  or a combinations of short parameters that contain a part of the overall 
  options. Each options must be specified by using the name of the option 
  followed by an equal sign and finally by the value that is specified for 
  these options. The options name are:

  * **eol** : Specify characters that will be used as end-of line delimiters. 
    The default value of this option is the semi-colon \(ie. ";"\).

  * **skip** : Specify the number of lines to be skipped at the beginning of 
    the processed text. The default value is 0, obviously.

  * **tokens** : A list describing which tokens will be assigned to special 
    \(local\) variables, such as **%%A**. The token description must conform 
    to the following rules, separated by a comma:

    * **n** : Where **n** is a number. Select the n-th token.

    * **n-p** : Where both **n** and **p** are numbers. Cast all the tokens 
      from a range starting at the n-th token up to the p-th token.

    * **\*** : Select all the remaining tokens. This could be used for the 
      **p** parameter of the syntax **n-p**.

    Each token will be assigned to a different special var, starting from the 
    specified variable \(in the previous code **%%A**\) and incrementing the 
    ASCII code of the variables \(ranging from ``A'' to ``Z'', and from ``a'' 
    to ``z''\). You can get detailed information about the algorithm on the 
    page [FOR \(technical\)](for-tech).

  * **delims** : Specify characters that will be used as delimiters to split 
    the string to process in tokens. By default, the only delimiter used by 
    dos9 is the space \(`` ''\).

  * **usebackq** : Uses a new syntax. If **object** is enclosed in single 
    quotes, then it will be considered as a string. If **object** is enclosed 
    in backward quotes, then it will be considered as a command to run. This 
    options is not worth since it just changes syntax of the **FOR** loop. 
    Just provided for compatibility purpose.

**Example 1:** Parsing a string :

    :: This first examples parses a simple string
    :: in this example, we'll process http-header like
    :: data.
    
    FOR /F "tokens=1,* delims=: " %%A IN ("Content-Type: text/plain
    Connection: keep-alive") DO (
    
     :: The option 'delims=: ' selects ':' and ' ' as delimiters
     :: The option 'tokens=1,*' assigns
     ::  - the first token to %%A
     ::  - from second token to end to %%B
     :: If a ' ' follows a ':', it wil be considered as a single
     :: delimiter.
    
     ECHO The header entry is : %%A
     ECHO The header value is : %%B
    )

Output: 

    The header entry is : Content-Type
    The header value is : text/plain
    The header entry is : Connection
    The header value is : keep alive
    

**Example 2:** Getting the content of a directory:

    FOR /F "tokens=*" %%A IN ('dir /b /a:D') DO (
    
     :: The use of 'tokens=*' discard delimiters since
     :: it just assign the whole line to %%A
    
     :: The for get the string to proccess from running
     :: the command ``dir /b /a:D'' which only output
     :: subdirectories in the current directory
    
     ECHO A subdirectory is "%%A"
    
    )

If this script is ran on Dos9 ``bin'' directory, it gives the following 
output:

    A subdirectory is "share"
    A subdirectory is "cmd"

**Exemple 3:** Getting content of a csv file:

Assume we have the following file, named ``my\_csv.csv'': 

    Alan Turing,a british,mathematician,invented Turing machine
    Harry Nyquist,an american,engineer,contributed to communication theory
    Nathaniel B. Nichols,an american,engineer,contributed to control theory

So this is a list of some famous man who contributed to computer theory. Let's 
print it via a **FOR** loop:

    FOR /F "tokens=1,2,3 delims=," %%A IN (my_csv.csv) DO (
     :: split that file into tokens
     :: %%A will recieve the name
     :: %%B will recieve the citizenship
     :: %%C will recieve the proffession
     :: %%D will recieve the description
    
     ECHO %%A was %%B %%C who %%C
    )

The program will produce the following output.

    Alan Turing was a british mathematician who invented Turing machine
    Harry Nyquist was an american engineer who contributed to communication theory
    Nathaniel B. Nichols was an american engineer who contributed to control theory

## Synopsis - Third syntax ##

    FOR /L %%A IN (start,increment,end) DO (
     :: some commands
    )

Perform commands incrementing a variable \(like in **C** programming 
language\).

* **start** : The first value that will be assigned to **%%A**.

* **increment** : The value **%%A** will be incremented on each new loop.

* **end** : The value that specify when the loop will end. Once **%%A** is 
  greater than **end**, the loop stops. Note that if **end** is lower than 
  **start**, no loop action will be performed.

The **FOR** loop requires both **start**, **increment** and **end** to be 
integers numbers. If these are floating numbers, they will be truncated to the 
lower closest interger \(floored\). If these are strings, the result is 
undefined.

**Example:** Counting from 1 up to 10: 

    FOR /L %%A IN (1,1,10) DO (
     ECHO %%A
    )

Output:

    1
    2
    3
    4
    5
    6
    7
    8
    9
    10

## Synopsis - Other deprecated syntaxes ##

Both following syntax are deprecated as richer effects can be achieved through 
use of the previously described **/F** option.

The first syntax allows user to get files in a directory and in 
subdirectories, matching a given mask.

    FOR /R basedir %%A IN (mask) DO (
     :: some stuff
    )

* **basedir** : The directory where the search will begin.

* **mask** : The mask used to match files. This could contain a [regular 
  expression](spec/regexp).

This syntax is deprecated because the same \(and even richer\) result can be 
achieved by using the following syntax:

    FOR /F "tokens=*" %%A IN ('dir /b /s /a:-D basedir/mask') DO (
     :: some stuff
    )

The second syntax allows user to get subdirectories in a directory, matching 
up with a given mask. The syntax is the same as previous syntax, just replace 
**/R** switch by **/D**.

## Compatibility ##

Mostly compatible with **cmd.exe**. Nevertheless, the syntax is backward 
compatible with **cmd.exe**, so that any old code not written for Dos9 will 
run in Dos9.

The **FOR** command is available since version **0.7.0.0**. The **FOR /F** is 
fully functional since version **0.7.0.2**.

## See also ##

[FOR \(technical\)](for), [IF](if) 

