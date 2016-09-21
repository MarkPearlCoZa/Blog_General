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

Make a bin folder where you keep all your scripts. This way you can have it in version control and it is easy to know where all your scripts are located

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


#### References 

[Why sh is not running automatically without putting sh in front](http://apple.stackexchange.com/questions/101170/why-do-i-need-to-put-sh-before-running-sh-files)
