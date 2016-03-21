---
layout: post
title: Ubuntu Notes
tags: Useful
category: Tech
---

#### Working with a terminal ####

Open a new terminal from outside of a terminal
~~~
CTRL+ALT+T
~~~

Open a new tab in the current terminal
~~~
ctrl+shift+t
~~~

Toggle between terminal tabs
~~~
alt+[num+of+window]
~~~

#### Mounting a drive in Ubuntu ####

Something that took me a while to figure out was if you have a secondary or external drive, you need to mount it if you want it to be accessible in Ubuntu. This is what worked for me...

~~~
sudo mount /dev/sdb1 /media/Storage -t ntfs -o nls=utf8,umask=0222
~~~

#### Open up graphical equivalent to Windows Explorer from CLI ####

~~~
xdg-open .
~~~

#### Shutdown from CLI ####

~~~
sudo poweroff
~~~

~~~
sudo reboot
~~~

### User Management ###

#### Change current users password ####

~~~
passwd
~~~

#### Add Users ####

~~~
adduser username
~~~

### Directory Meanings ###

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

#### Init.D Directory ####

This directory contains start / stop scripts for managing common processes that you don't normally want to just kill.

[More info](http://www.ghacks.net/2009/04/04/get-to-know-linux-the-etcinitd-directory/)

### Network Settings ###

Check the following file

~~~
/etc/network/interfaces 
~~~

Restart a network interface

~~~
sudo ifdown eth0 && sudo ifup eth0
~~~

### Misc ###

#### Multiple Ttys over Putty ####

~~~
screen
~~~

~~~
ctrl+A + Command
~~~
In screen mode this get's you to screens menu

#### Get Ip Addresses ####

~~~
ifconfig -a
~~~

#### Command Line Browsing ####

Elinks

[More Options](http://askubuntu.com/questions/29540/browsing-the-internet-from-the-command-line)

#### Get Ubuntu Version ####

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

#### Map Capslock as escape ####

~~~
dconf write /org/gnome/desktop/input-sources/xkb-options "['caps:escape']"
~~~

#### Screen ####

Make window full-screen F11

### References ###

[Keyboard Shortcuts](https://help.ubuntu.com/community/KeyboardShortcuts)  
[How to install LAMP](https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-ubuntu)
