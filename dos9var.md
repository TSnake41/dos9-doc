# %DOS9_VERSION%, %DOS9_OS%, %DOS9_OS_TYPE%, %DOS9_PATH%, %DOS9_SHARE%, %DOS9_ETC%, %DOS9_IS_SCRIPT% variables #

The **%DOS9\_VERSION%** variable expands to the current version of 
[Dos9](dos9).

The **%DOS9\_OS%** variable expands to the name of the current **OS** running 
[Dos9](dos9).

The **%DOS9\_OS\_TYPE%** variable expands to the type of the current **OS** 
running [Dos9](dos9).

The **%DOS9\_PATH%** variables expands to the path to [Dos9](dos9) directory.

The **%DOS9\_IS\_SCRIPT%** variable is used to detect whether the execution 
flow comes from a script or from the prompt.

**%DOS9\_SHARE%** and **%DOS9\_ETC%** expands to the locations of various 
[Dos9](dos9) files.

## Synopsis ##

    %DOS9_VER%

Contain [Dos9](dos9) version number.

    %DOS9_OS%

Contains the OS name on which **Dos9** is runnig. This variable does not give 
any information on OS version though. The possible value are:

* **WINDOWS**

* **GNU/Linux**

* **NetBSD**

* **OpenBSD**

* **DragonFlyBSD** 

* If none of these operating system is found by **Dos9**, then 
  **%DOS9\_OS\_TYPE%** will contain the host triplet for which Dos9 has been 
  compiled.

This variable is interesting to execute specific code for any of these 
platforms. In most cases, the variable **%DOS9\_OS\_TYPE%** is sufficient.

    %DOS9_PATH%

**%DOS9\_PATH%** contains the path to the [Dos9](dos9) executable. This path 
is dinamically generated, so that the path will be correct even from non 
conventionnal paths, this enables making portable version on removable media.

    %DOS9_OS_TYPE%

Contains the type of operating system on which Dos9 is running. It can have 
two values:

* **\*NIX** : For Unix-based operating systems.

* **WINDOWS** : For windows based operating systems.

        %DOS9_IS_SCRIPT%

Expands to **false** if [Dos9](dos9) has been launched in interactive mode 
\(that is, with no script to execute\) or **true** else. This value is useful 
inside configuration scripts such as [Dos9\_Auto.bat](dos9auto). The value of 
**%DOS9\_IS\_SCRIPT%** is inherited when a script is [CALL](call)ed, however, 
the value is overwritten in any other case.

    %DOS9_SHARE%

Contains the path to the folder where Dos9 static data is stored.

    %DOS9_ETC%

Contains the path to the folder where Dos9 configuration files are stored.

## Compatibility ##

Uncompatible with **cmd.exe**, these variable are not defined.

Availiable since version **0.7**.

## See also ##

[Environment variables](spec/var), [Specifications index](spec/index) 

