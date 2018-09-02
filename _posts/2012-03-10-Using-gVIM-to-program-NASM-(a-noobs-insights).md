---
layout: post
title: Using gVIM to program NASM (a noobs insights)
tags: 
category: General
---
I’m new to vim and to nasm… several months ago I put up a post on how I had discovered a tutorial on VIM and was going to give it a second try – my first attempt failing dismally. At the time my second attempt fell through after about two weeks – I was just to comfortable with Windows and the concept of not having everything menu based was too daunting for me.

So when a few weeks ago I decided to give vim a third chance, it was pretty much a “last chance” - if I didn’t see any light at the end of the tunnel it was going to be bye bye vim. A few days in to my third attempt I discovered the command line in vim. Why I never understood that vim had a command line up to then is beyond me… looking back it seems fundamental and obvious. Since discovering the command line this has become my light at the end of the tunnel…

On a side note – I have had a few friends suggest that I give sublime a look as it seems to be the new cool on the block – my intention is to have a look at it only once I have gotten over vim… why learn to fly before you can walk?

So, today I am messing with nasm and I thought as a noob to nasm and vim, it would be nice to put up a post on how you can use vim as your editor for nasm. I am positive there will be better ways than this, so if you are a vim expert and see an obvious mistake, let me know…

Syntax highlighting in Vim
First thing for me is to get syntax highlighting on in vim. Go to the command line in vim (press escape and then : ). You can turn syntax highlighting on or off. To turn it on type…

:syntax on

Vim turns on highlighting based on the file extension – for me having the file extension of .asm has enabled the highlighting for nasm files. If you are not following the naming convention or haven’t saved you file yet (so it doesn’t have an extension) you can force the type of syntax highlighting with the following command…

:set syntax=nasm

Where nasm is the name of the type of syntax (you could use c or perl or any language that is set up).

Compiling  Nasm projects in Vim
When writing projects in nasm I have two applications open – a console window (for executing and evaluating my project) and gVim (to edit and modify my code). Something that bugged me for a while was in the console window I would compile my solution and then run it… this soon became tiring. That was when I discovered the ! command in vim, which allows you to execute command line commands directly from vim.

For instance in gVim do the following…

: !dir

This is the equivalent of typing dir in the command line of a windows console. Armed with this fact I tried the following…

: !nasm –f bin % –o temp.com –l temp.lst

Magically my nasm file was compiled and I had a temp.com sitting in my directory! Magic? Okay, so there are a few things here that you need to know upfront… % stands for the filename of the current vim file you have open.. To see what it contains type…

: !echo %

The rest of the syntax is nasm specific basically telling it to make a linker file and what the compiled app should be called. This was great, but still not what I wanted… in fact it would be more work than just repeating the text in the console window… That was when I discovered mapping of keyboard keys. Try the following…

:map <F2> :!echo hello world

In essence what we have done here is mapped the F2 key on the keyboard in vim so that whenever I press that it executes the text associated with it after the : . Armed with this I can now do the following…

:map <F5> :!nasm –f bin % –o temp.com –l temp.lst

Which has mapped the build command to the F5 key, now whenever I want to build my nasm project I follow the following key sequence…

[esc] [F5] [enter]

And everything is done!

Where to from here?
It is still early days with nasm and with gVim. I think I have made a small breakthrough with gVim, to the point where I would open it up instead of notepad. From what I can see it is a highly customizable tool, and is becoming extremely useful.