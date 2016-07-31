---
layout: post
title: Bash Notes
tags: Useful
category: Tech
---

## Alias's ##

Edit the file in the following location: ~/.bashrc

~~~
alias doSomething='commands'
~~~

## Basic File Management ##

### Copy a File ###

~~~
cp temp.sh file5.sh
~~~
copy temp.sh as file5.sh

~~~
cp temp* ..
~~~
copy files starting with temp to the parent folder.  

~~~
cp -R files/ backup/
~~~
copy all files and subdirectories to the backup directory

Copying files means you are creating a file, which means you take ownership. 

~~~
cp -a file1.txt file2.txt
~~~
copy files in archive mode, which maintains original ownership

### Deleting Files & Directories ###

~~~
rmdir
~~~
deletes empty directories

~~~
rm -rf directoryName
~~~
recursively deletes directory and all of its content

### Move or Rename File ###

~~~
mv temp.sp new.sh
~~~

### Compress a File ###

tar stands for tape archive

~~~
tar -c -v -f file.sp
~~~
creates a tar archive

~~~
tar -c -z -v -f directoryName
~~~
-z means to zip it up

### Navigating Directories ###

Navigate to previous directory

~~~
cd -
~~~

Navigate to user directory

~~~
cd ~
~~~

Navigate to home directory

~~~
cd
~~~

### Listing Files ###

~~~
ls -l
~~~
displays a listing with full format  

~~~
ls -F
~~~
displays the file or directory type in the listing  

~~~
ls --color=auto
~~~
diplays listing with color

### Finding Files ###

~~~
find . -newer file1
~~~

finds all files in the current and children directory that are newer than file1

~~~
find . -newer file1 -delete
~~~

finds and deletes all file in the current and children directory that are newer than file1

~~~
find . -name "*FileNameToMatch*"
~~~

~~~
find . -iname "*stuff*" 
~~~

**Find <target> -flags <search expression>**  

finds all files in the current and children directory that match the FileNameToMatch  

#### Finding Files using Regex ####

Find any files with 'stuff' in them

~~~
find . -iregex ".*stuff.*"
~~~

.* is equivalent to wildcard

By default regex checks the entire path. There is an implicit ^..$ implied which means "stuff" is actually "^stuff$"

#### Open First found file in Vim ####

~~~
vim $(find -name somefile.txt)
~~~

~~~
find -name somefile.txt -exec vim {} \;
~~~

### Manipulating Directories ###

Remove directory and all sub directories

~~~
rm -r dir
~~~

Remove directory and all sub directories (force)

~~~
rm -fr dir
~~~

Make directory

~~~
mkdir dir
~~~

### Imaging Tasks ###

~~~
rsync -av directoryName locationOfBackup
~~~
synchronizes copies

~~~
rsync -av --delete directoryName locationOfBackup
~~~
syncrhonizes deletions

### Search tool ###

~~~
grep
~~~
-----------------------------------------------------------------------

## Process Management ##

~~~
bg
~~~

Moves the current process into the brackground

~~~
ps
~~~

~~~
sleep 200 &
~~~

The & automatically starts a job in the background process

~~~
jobs
~~~

Shows a list of the current jobs

~~~
fg 1
~~~

Brings job number one into the foreground

~~~
pgrep
~~~

Searches for a current process

~~~
ps -l
~~~

Shows a long listing

~~~
ps -e
~~~

Shows all processes

~~~
pkill sleep
~~~

Kills the sleep process

~~~
kill -9 procnum
~~~

Really kills the process

~~~
top -n 1
~~~

The swiss army knife of processes

-----------------------------------------------------------------------

## Searching Text Files using Regex ##

~~~
grep Server /etc/ntp.conf
~~~

Search is case sensitive unless otherwise specified

~~~
grep -i
~~~

Search without case

~~~
grep -ve '^#' -ve '^$' /etc/ntp.conf
~~~

Removes commented lines ^# and empty lines ^$  
The -ve means an additional expression.  

~~~
sed -i '^#/d;^$/d' /etc/ntp.conf
~~~

The stream editor, edits the inline stream
-i stands for the inplace update  

~~~
grep -E 'regex'
~~~

-E stands for a full regex expression

-----------------------------------------------------------------------

## Analyze Text Files ##

**Please note we use test.sh as a placeholder for the file you are performing the action on.**  

### Piping output ###

~~~
>
~~~
e.g. ls > test.sh

### Pipe to vim to check syntax ##

~~~
11 | gvim --  
~~~

### Show contents of file ###

~~~
cat test.sh
~~~

### Making Files Exectuable ###

~~~
chmod +x test.sh
~~~

### Making Files Writeable ###

~~~
chmod 777 test.sh
~~~

### Removing unrecognized dos characters ###

~~~
dos2unix test.sh
~~~

### Head and Tails ###

Head shows the first ten lines of a file.  
Tail shows the last ten lines of a file.  

~~~
head -n 3 test.sh
~~~

The above shows the first 3 lines of test.sh

~~~
tail -f
~~~
The above follows the end of a file. Ctrl+C stops the following.

### More and Less ###

More allows us to page forward through a file.  
Less allows us to page forward, backward and to a specific location in a file.  

### Cut ###

Cut can be used to display only certain fields within a file.  

~~~
cut -f1,3 -d";" !$
~~~

Displays field 1 and field 3 of a delimitered file using ; as the delimiter where !$ was the last argument used (in this case cat test.sh).  

### Sort ###

Sort can be used to order the columns as desired. Sort without defining a column sorts on the first column.

~~~
sort -r test.sh
~~~

Reverses the sort

~~~
sort -k4 -t"," !$
~~~

sort the fourth column using , as the delimiter on the last command run.

~~~
sort -u
~~~

shows only unique results.

-----------------------------------------------------------------------

## Other ##

### List disks ###

~~~
fdisk -l
~~~

### Clear the screen ###

Ctrl+L - clears the console

### Run with root privelages ###

~~~ 
sudo -i 
~~~

### Run the last command again ###

~~~
!$
~~~

### Processes Running ###

Go to the /proc directory, if you perform a ls it will show you all the processes running currently. Running cat on the file mounts will show you all the drives currently mounted.

### Enable vi mode in bash ###

~~~
set -o vi  
~~~

### Show history of commands ###

~~~
history  
~~~

### Add custom autocomplete commands to bash ###

1.     Download the attached commands.txt file to your git bash home folder

a.     I need to figure out a way to keep this updated easier, currently I run the console with no parameters and manually copy the command names into the file 

2.     In your git bash home, open (or create) your .bash_profile file

3.     Add the following lines, adjusting kbrepo to where your console is built

kbrepo=/c/src/Keyblade/Keyblade
alias kbc='$kbrepo/KeyBlade.UI.Console/bin/Debug/Keyblade.UI.Console.exe c'
export COMMAND_FILE=~/commands.txt
_kbcommands()
{
            local cur=${COMP_WORDS[COMP_CWORD]}
            COMPREPLY=( $( compgen -W "$(cat ${COMMAND_FILE})" -- $cur ) )
}
complete -F _kbcommands kbc
 
4.     Now you can use ‘kbc [TAB]’ and it will show you a list of commands.

5.     OR

6.     kbc Ack[TAB] è kbc AcknowledgeConsoleFailures

### References ###

[Bash stuff from Coderwall](https://coderwall.com/p/kubxjq)
[Bash History](http://blog.pluralsight.com/how-to-use-bash-command-line-history?utm_campaign=newsletter_2014_0716&utm_source=newsletter&utm_medium=email&utm_term=blog)
