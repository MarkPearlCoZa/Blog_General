---
layout: post
title: Shell Scripting Notes
tags: Linux
category: Tech
---
### Outline

- [Executing a Script](#executing-a-script)  
- [Script Format](#script-format)  
- [Passing parameters to a script](#passing-parameters-to-a-script)

### Executing a Script

#### Making it Executable

To make a script file executable run the following command:  

~~~
chmod u+x file.sh   # makes it executable just for you
chmod a+x file.sh   # makes it executable for everyone  

comod a-x file.sh   # remove permission to execut
~~~

#### Calling a script

If a script is in your path variable, you can just call it like a regular command.
If a script is NOT in your path variable, you need to include the location when calling it.  

~~~
./file.sh

# or

/home/documents/file.sh
~~~

#### Have a bin folder for your scripts

Make a bin folder where you keep all your scripts. This way you can have it in version control and it is easy to know where all your scripts are located. It also makes it easier to centrally locate all your scripts.  

To add your bin folder to the path variable you can add the following in your .bash_profile file  

~~~
export PATH=$PATH:/Users/mark.pearl/Source/personal/Settings_Bash/
~~~

Assume /Users/mark.pearl/Source/personal/Settings_Bash/ is where you script files are located.   


#### Handling aliases 

Another useful technique I have found is to store all your aliases in a script file. In your .bash_profile file you then do the following

~~~
source /Users/mark.pearl/Source/personal/Settings_Bash/general_aliases.sh
~~~

Assume /Users/mark.pearl/Source/personal/Settings_Bash/general_aliases.sh is where you script file containing your aliases is located.  

### Script Format

#### Start with a Shebang  

The first line of a script file tells the OS what language the script file is based in. For bash shell scripts we want this to be a shebang (#!) with bash.

~~~
#!/bin/bash
~~~

Other OS like windows might have a different location for bash. Below is the most compatible shebang to use.

~~~
#!/usr/bin/env bash
~~~

### Passing parameters to a script

#### Positional Parameters

$1, $2, $3 hold positional parameters

Use curly braces for double digits or more...

${10}, ${11}, ...

#### $0 - name of script

$0 holds the name of the script as it was called. 

If you use symbolic links etc, it would have the original name that triggered the script.

#### $@ - all parameters passed in

$@ is equivalent to $1, $2, $3, ..., $n

Using double quotes around $@ keeps parameters with multiple words in them intact i.e. "$@" 

#### $* 

Usually don't use this.

#### $# 

$# holds the count of the arguments passed to the script

#### References 

[Why sh is not running automatically without putting sh in front](http://apple.stackexchange.com/questions/101170/why-do-i-need-to-put-sh-before-running-sh-files)
