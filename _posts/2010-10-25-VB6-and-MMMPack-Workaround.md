---
layout: post
title: VB6 and MMMPack Workaround
tags: 
category: General
---
So, I recently put up a post on using the MMMPack tool to help package old VB6 projects so that they work in Vista and Windows 7. I am a real fan of this tool because it saves me a ton of time.\

Recently though I needed to re-setup my machine to get the whole thing working properly and came across a few little gremlins that come with beta products.

So I downloaded the latest MMMPack from their website and when using the tool on my project I got the following error.

1a


“Application has failed to start because its side-by-side configuration is incorrect…”

I didn’t have time then to figure out what was going on, but my buddy Brendon did… He applied the following steps…

1a) Looked up in the windows event viewer and found the error.

1b

1c) Turned off mainifest embedding in MMM.

1c 

2) Found the mainifest file for the exe.

2 

3) Went to the line specified in 1b and found that MMM was inserting invalid characters, probably a bug in escaping.

 

3


4) Manually removed invalid characters.

4


5) Manually embedded the manifest file into the exe using a program called reshack and everything worked fine….

 

Interestingly enough, the previous version of MMMPack did not have this error. If you would like to use it I have put it up for download below…

