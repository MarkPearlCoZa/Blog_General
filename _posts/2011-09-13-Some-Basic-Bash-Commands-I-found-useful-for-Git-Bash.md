---
layout: post
title: Some Basic Bash Commands I found useful for Git Bash
tags: 
category: General
---
The world of Bash is new to me so for those going through the same experience I thought I would list a few things to save time. Some of these are specific to me, while others may have general use.

Useful Commands
Open root folder - This opens up windows explorer at the root location.

explorer .

Create a folder

mkdir foldername

Get a directory listing

ls

Execute a script without specifying the .sh file extension

Once you have written your script files it can get annoying to have to keep specifying the .sh part of the file whenever executing the script. The following post on Stack Overflow runs you through getting past this. I was not able to get this working on my version of git bash but I am assured that this will work most normal instances of bash

Rename a file - instead of having a rename method, basically you are “moving” a file from one state to another.

mv oldname newname

Go to the bin folder of bash

cd /

Go to the users home directory

cd ~

Whenever you need to explicitly reference the current directory – it was explained to me on some flavours of bash you might need to explicitly state the location of the file regardless of whether you are currently in that location.

./

Change permissions of a file

chmod permissions file

I wanted to create some permanent aliases… after some research it turns out that the best place to store these is in the “.bashrc” file. This file should be located under the home directory. To create a new one you can type the following into bash… which will open up vim – in vim add the aliases and then save the file.

vim ~/.bashrc && source ~/.bashrc

Remove a folder with files in it.

rm –Rf FolderName

Display content of a file

cat filename

Concatenate two files into another file

cat filename1 filename2 > targetfilename