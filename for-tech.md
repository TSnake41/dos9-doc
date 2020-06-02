# FOR Command (Technical) #

**Warning: this manual page is a technical version of the FOR command.** This 
pages give full FOR command specifications. This manual page includes many 
particular cases. If you are not interested in very sharp information about 
the command, just check out the [FOR](for) regular man page.

**FOR** is by no doubt the most useful tool that batch programming provides. 
It enables processing of numerous type of objects, files, command output, 
integers. Thus **FOR** is a really interresting tool to create advanced 
scripts.

**FOR** loop may seem difficult to use at first sight, nonetheless it is the 
most important tool to batch programming.

## Synopsis - First syntax ##

The first syntax allows processing strings.

    FOR %%A IN (string) DO (
     :: some commands 
    )

Splits a **string** in chunks and execute the specified commands on each of 
them.

* **%%A** : The name of the [special variable](spec/xvar) that will receive 
  the chunk to be processed.

  The proprietary software **cmd.exe** needed the users to use two different 
  syntaxes, depending on the input mode \(console or script\). In the first 
  case, the user had to use **%A** instead of **%%A**, which was required in 
  the second case. [Dos9](dos9) uses a single syntax based on the batch syntax 
  \(ie. always **%%**\).

* **string** : The string to split in chunks. Dos9 uses the following 
  delimiters:

  * **' '** : space.

  * **' '** : tabs.

  * **'\n'** : line feed.

  * **:** : colon.

  * **;** : semi-colon.

  * **,** : comma.

  Any of these delimiters \(except new lines\) can be ignored using quotes 
  \(simple or double\). This quote will be kept in the variable. To remove 
  quotes, use **%%~A** instead of **%%A** \(for more informations, see 
  [special variable](spec/xvar)\).

  If any of the chunks consist in a [regular expression](spec/regexp), then it 
  is replaced by the files matching it. If no files match, the chunk is 
  skipped. If the chunk contains quotes, they will be removed.

Example :

    FOR %%A IN (some stuff "some stuff") DO (
     ECHO current element : %%A
    )

Output : 

    current element : some
    current element : stuff
    current element : "some stuff"

## Synopsis - Second syntax ##

The second syntax is based on the **/f** switch. This allow making some 
transformations on string, commands or files. Note that strings are not split 
the same way as using the preceding syntax.

    FOR /F [options] %%A IN (object) DO (
     :: some commands
    )

Execute some command on a string, a command output or a file. To ease the 
reading of this page, parameters and switches described in the preceding 
paragraph will not be described again.

* **object** : the object that as to be used as the **FOR** command input 
  **FOR**. This parameter can be \(or not\) surrounded by one of these 
  following delimiters:

  * **'** : **Object** refers to a command whose output is used as **FOR** 
    loop input.

    The corresponding command line is executed asynchronously \(that is both 
    **FOR** loop commands and **object** are run simultaneously\).

    Using **cmd.exe**, if the command line was to contain any end of line 
    characters, the said characters will be removed and line would be executed 
    as if it was a single line, preventing user from using complex scripts as 
    input. [Dos9](dos9) removed this restriction, as such more complex script 
    can be used as input.

  * **"** : **Object** refer to a string of characters. The **FOR** loop will 
    then use **object** as input. If this string contains any end-of-line 
    characters, then this line will be used line by line.

  * If neither of the preceding characters surround **object**, then 
    **object** refers to a file name. The **FOR** loop will then open the file 
    and read it entire content and run the commands specified on its content.

    This file can obviously be multiline, but it is supposed to be somehow a 
    **text** file. If the file is not a **text** file, then the behaviour is 
    unspecified.

    As opposed to **cmd.exe**, **Dos9** does not remove empty lines from the 
    loop input. Nonetheless, a compatible behaviour can be enabled using 
    **CMDLYCORRECT** option from the command [SETLOCAL](setlocal).

* **options** : options that must be used by the **FOR** loop. This options 
  have to be either one parameter containing all the options or a combination 
  of various parameters containing a bit of all information on options. Every 
  option has to be specified using the option name followed by the "=" sign 
  and the value associated with the option:

  * **eol** : Specify some characters to be used as end of line. All the 
    characters following the eol are used as end of line. By default, this 
    parameter is the semi colon **;**.

    At most **FILENAME\_MAX-1** \(ie. 259 characters using windows\) different 
    characters from **ASCII** table, or from a single byte encoding \(however, 
    no utf-8 character is accepted yet\).

    If this parameter is specified more than once, then, the **FOR** command 
    will only consider the last occurrence of this parameter.

  * **skip** : Skip a given number of lines that should be ignored at the 
    start of the loop.

    If the number given surpasses the actual length of the input, then the 
    loop will be skipped. The default value is 0.

  * **tokens** : A list specifying the way chunks of input lines will be 
    assigned to [special variables](spec/xvar) such as %%A. The list must 
    conform to the following rules, elements of the list must be separated 
    using commas:

    * **n** : Where **n** is an integer. Select the **n**-th tokens.

    * **n-p** : Where **n** and **p** are integers. Select input from the 
      **n**-th tokens up to the **p**-th included.

    * **\*** : Selects all of the remaining tokens \(all those following the 
      last selected token\). This parameter can be used as **p** for the 
      preceding syntax **n-p**, in this case, it selects all of the tokens 
      remaining after the **n**-th token \(included\).

    Every selected set of tokens is assigned to a different [special 
    variable](spec/xvar), starting with the specified **FOR** loop variable 
    and incrementing the **ASCII** code for every new set of token \(roughly 
    corresponding to an alphabetical progression\). If the code passes over 
    **0x7F**, then the following variable will be **0x21** \(ie **!**\).

    If **FOR** has to assign an already assigned var, the loops stoops on 
    error.

    The tokens positions start at **1**. As opposed to **cmd.exe**, Dos9 does 
    not have any constraints on the order of selections of the token \(ie. 
    sets may overlap or be in "reverse" order\).

  * **delims** : A set of characters used as delimiters to split input lines 
    got through **object** into tokens. By default, the only delimiter is 
    **space**.

    If this parameter is specified, then **space** is a delimiter any more and 
    is replaced by the given character set. If **Dos9** encounters a 
    sub-string containing only delimiter in the input, then **Dos9** behaves 
    as if the sub-string was only one single delimiter \(no empty tokens are 
    created\).

    At most **FILENAME\_MAX-1** characters can be specified. If there is 
    several instances of **delims** within **options**, only the last one is 
    used by the **FOR** loop.

  * **usebackq** : Uses the new syntax introduced with **Windows NT**; If 
    **object** is enclosed in single quotes, then string input is assumed. 
    However, if it enclosed in backward quotes, then command input is assumed. 
    This parameter is the only one requiring neither an equal sign nor a value 
    attached to it.

    This parameter was really usefull using **cmd.exe** that frequently 
    truncates strings input from **FOR** whenever some usual double quote is 
    encountered. However, this is no more relevant using **Dos9**. 

**Example 1:** String parsing

    :: The first example parses simple strings
    :: from http headers
    
    FOR /F "tokens=1,* delims=: " %%A IN ("Content-Type: text/plain
    Connection: keep-alive") DO (
    
     :: 'delims=: ' select either of ':' and ' ' as delimiters
     :: 'tokens=1,*' assigns :
     ::   - The first token to %%A
     ::  - All the remaining tokens to %%B
     :: A ' ' following a ':', is considered as a single
     :: delimiter
     ECHO The header field is : %%A
     ECHO Its value is : %%B
    )

Output: 

    The header field is : Content-Type
    Its value is :  text/plain
    The header field is : Connection
    Its value is : keep alive
    

**Example 2:** Listing sub directories

    FOR /F "tokens=*" %%A IN ('dir /b /a:D') DO (
    
     :: "tokens=*" assigns the full line to %%A
    
     :: The loop uses ``dir /b /a:D'' output to
     :: print only the sub-dirs
    
     ECHO Sub-dir : "%%A"
    
    )

If this loop is run on the ``bin'' folder of **Dos9**, the following output is 
obtained.

    Sub-dir : "share"
    Sub-dir : "cmd"

**Example 3:** Parsing a **.csv** file

Suppose we have a file named **infos.csv** containing.

    Wally,British,Waldo's counterpart in Britain
    Waldo,American,Charlie's counterpart in US
    Charlie,French,Wally's counterpart in France

It consist of names of **Wally** from the books **Where is wally** in 
different countries, followed by their nationality and a brief description.

Donc il s'agit d'une liste d'hommmes célèbres qui on contribué à la théorie 
informatique; Nous pouvons l'afficher avec une boucle **FOR**:

\(Note the variant on the **option** syntax.\)

    FOR /F "tokens=1,2,3" "delims=," %%A IN (infos.csv) DO (
     :: Separates different fields
     :: %%A receives name
     :: %%B receives nationality
     :: %%C receives brief
    
     ECHO %%A is %%C. He is %%C
    )

The script output is:

    Wally is British. He is Waldo's counterpart in Britain
    Waldo is American. He is Charlie's counterpart in US
    Charlie is French. He is Wally's counterpart in France

## Synopsis - Third syntax ##

The third syntaxe allows doing traditional **FOR** loops \(ie. a loop 
incrementing a variable every new loop; in a somehow **C**-like manner\).

    FOR /L %%A IN (start,step,end) DO (
     :: Some commands
    )

* **start** : The first value assigned to **%%A**

* **step** : Steps value.

* **end** : The maximum value that **%%A** can reach by looping. When **%%A** 
  gets greater than **end**, the loop stops. If **end** is less than 
  **start**, the loop is not run.

The **FOR** loop requires **start**, **step** and **end** to be integers. If 
floating point numbers are specified, they will be floored. If string is 
specified, the behaviours is not defined.

**Example:** Counting from 1 to 10:

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

## Synopsis - Deprecated syntaxes ##

The following syntaxes have been deprecated since **FOR** no allows to achieve 
more robust, more flexible alternatives to theses. 

The first deprecated syntax enables obtaining files within a folder and its 
sub-folders that match a given [regular expression](regexp).

    FOR /R basedir %%A IN (regexp) DO (
     :: some stuff
    )

* **basedir** : The base folder for the search.

* **regexp** : A regular expression to select matching files.

This syntax is deprecated since the same result can be achieved using:

    FOR /F "tokens=*" %%A IN ('dir /b /s /a:-D basedir/regexp') DO (
     :: some stuff
    )

The second syntax behaves pretty much the same way as the preceding except 
that it requires the **/D** switch and selects only folders matching 
**regexp**.

## Compatibility ##

Mostly compatible with **cmd.exe**. However, any code from **cmd.exe** can be 
executed with no bugs under **Dos9** concerning **FOR** loops.

However, one can come across some unexpected behaviour using the **tokens** 
options. Indeed, if tokens specifiers are not specified from the lowest to the 
highest, then **cmd.exe** will silently try to sort the tokens. However 
**Dos9** does not do so, leading to a potential unexpected behaviour. In 
addition, **Dos9** performs all right when two tokens specifiers overlap \(eg. 
"4-6,5-7"\) although **cmd.exe** fails to handle such specifiers correctly.

Also, **Dos9** does process empty lines while using **/F** switches while 
**cmd.exe** keeps skipping them. However this behaviour may be changed using 
**CMDLYCORRECT**.

The **FOR** command is availables since version **0.7.0.0**. The **FOR /F** 
command is totally functionnal since version **0.7.0.2**.

## See also ##

[FOR Command](for), [IF command](if)

