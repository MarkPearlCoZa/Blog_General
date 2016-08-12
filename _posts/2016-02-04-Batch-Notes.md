---
layout: post
title: Batch Notes
tags: Useful Windows
category: Tech
---
#### Using parameters in Bat files ####

Parameters passed through the command line can be accessed in batch files with the notation %1 to %9. 
There are also two other tokens that you can use:

%0 is the executable (batch file) name as specified in the command line.
%* is all parameters specified in the command line -- this is very useful if you want to forward the parameters to another program.

#### References ####

[Using parameters in bat files](http://stackoverflow.com/questions/14286457/using-parameters-in-batch-files-at-dos-command-line)  

