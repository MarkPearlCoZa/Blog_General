---
layout: post
title: Ubuntu Notes
tags: Linux
category: Tech
---

### Terminal Management

#### Opening a Terminal

Open a new terminal from outside of a terminal

~~~
CTRL+ALT+T  
~~~

Open a new tab in the current terminal

~~~
CTRL+SHIFT+T
~~~

#### Moving Between Terminals

Toggle between terminal tabs

~~~
ALT+[NUM+OF+WINDOW]
~~~

-------------------------------------------------------------------------------------------------------

### User Management 

#### Who is the current user

~~~
whoami
~~~

#### Add new user

~~~
adduser username
~~~

#### Change current users password

~~~
passwd
~~~

-------------------------------------------------------------------------------------------------------

### Drive Management  

#### Mounting a Drive

~~~
sudo mount /dev/sdb1 /media/Storage -t ntfs -o nls=utf8,umask=0222
~~~

#### Equivalent to Windows Explorer

~~~
xdg-open .
~~~

-------------------------------------------------------------------------------------------------------

### Directory Management

#### Directory Meanings

bin = binary = binary files (executableS)  
boot = boot = stuff the system needs to boot  
dev = device = printer(s), hard drives, mouse ...  
etc = etcetera  
home = location for home directories  
lib = libraries = library files - sort of like dlls in windows  
mnt = mount = where some file systems are mounted  
opt = optional  
root = home directory of the root user  
sbin = system binaries like hdparm, fsck, init ...  
tmp = temporary = storage for temporary files  
var = variable = storage for variable data i.e. logs  
usr = user files  

#### Init.D Directory

This directory contains start / stop scripts for managing common processes that you don't normally want to just kill.

[More info](http://www.ghacks.net/2009/04/04/get-to-know-linux-the-etcinitd-directory/)

-------------------------------------------------------------------------------------------------------

### Applicaiton Management

To find a package that was previously installed on your system using apt-get go to...

~~~
/var/cache/apt/archives
~~~

#### Installing a new package

~~~
sudo apt-get install PACKAGE_NAME
~~~

#### Removing a package

~~~
sudo apt-get remove PACKAGE_NAME
~~~

-------------------------------------------------------------------------------------------------------

### Network Management

Check the following file

~~~
/etc/network/interfaces 
~~~

Restart a network interface

~~~
sudo ifdown eth0 && sudo ifup eth0
~~~

#### Get Ip Addresses

~~~
ifconfig -a
~~~

-------------------------------------------------------------------------------------------------------

### Customizing for VIM

#### Sharing the clipboard between memory registers

[How can I copy text to the system clipboard from vim](http://vi.stackexchange.com/questions/84/how-can-i-copy-text-to-the-system-clipboard-from-vim)  

-------------------------------------------------------------------------------------------------------

### Misc ###


#### Multiple Ttys over Putty

~~~
screen
~~~

In screen mode this get's you to screens menu

~~~
ctrl+A + Command
~~~

#### Get Ubuntu Version

~~~
lsb_release -a
~~~

#### Network share via cli ####

~~~
net usershare add Documents /home/michael/Documents "Michael documents" everyone:F guest_ok=
~~~

[More details](http://www.leewardassociates.com/481-sharing-folders-in-ubuntu-12-04-via-command-line)

#### Installation ####

[Great article](http://www.codecoffee.com/tipsforlinux/articles/27.html) on make process and what it means.

#### Show the file size in megabytes ####

~~~
ls -lah
~~~

### Screen Management

Make window full-screen F11

### Shutting Down

~~~
sudo poweroff
~~~

~~~
sudo reboot
~~~

### Misc

#### Map Capslock as escape ####

~~~
dconf write /org/gnome/desktop/input-sources/xkb-options "['caps:escape']"
~~~


### References ###

[Keyboard Shortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)  
[How to install LAMP](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu)
