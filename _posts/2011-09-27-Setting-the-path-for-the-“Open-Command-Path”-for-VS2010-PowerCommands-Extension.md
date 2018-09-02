---
layout: post
title: Setting the path for the “Open Command Path” for VS2010 PowerCommands Extension
tags: 
category: General
--- 

I have power commands installed for VS2010 and when I right click on a file I get the “Open Command Prompt” option, however I want to modify the path holder so that I can add additional paths.

For instance I want to add the JetBrains dotCover path…

If you go to the “C:\Program Files (x86)\Microsoft Visual Studio 10.0\Common7\Tools” folder and edit the vsvars32.bat file" and add the following under the @rem PATH section…

@set "PATH=%ProgramFiles%\JetBrains\dotCover\v1.1\Bin;%PATH%"

Then save the file and close and it will now have that path appended.
