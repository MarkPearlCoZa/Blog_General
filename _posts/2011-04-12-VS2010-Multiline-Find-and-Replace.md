---
layout: post
title: VS2010 Multiline Find and Replace
tags: 
category: General
---
I have been busy refactoring a legacy application where there are numerous blocks of code that are identical. To make the code more readable I wrote a sub function that performed the block of code and then I wanted Visual Studio to parse may file and replace any occurrence of that block of code with a new string.

Originally I got stuck as it seemed VS2010 only allowed a single line replace, however after a bit of searching I found out that thankfully it does support multiline replace, it is just a bit cryptic on how to do this.

So, for those that are in the same position as me, these are the step…

Step 1)

Select the block of code you want to replace.

Step 2)

View the Macro Explorer in VS2010

VSMultiLine

Step 3)

Select the FindLine Macro

VS2011-04-12 10-51-22 AM

Step 4)

Click the “Quick Replace” Button and type in the replace string.

VS2011-04-12 10-53-24 AM

Step 5)

Click the “Replace All” button, and there you go, multiline replace in VS2010