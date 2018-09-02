---
layout: post
title: Getting Started with NASM
tags: 
category: General
---
Today I got to play with NASM. This is an assembler and disassembler that can be used to write 16-bit, 32-bit & 64-bit programs. Let me say upfront that the last time I looked at assembly code at any depth was when I was studying Computer Science in Pietermaritzburg – ten years ago – and we never ever got to touch any real assembly code so a lot of what I am looking at today is very new to me.

The first thing I did was download NASM compiler. This turned out to be a bit more complicated than I thought. Originally I went to http://www.nasm.us/ and downloaded the nasm-2.09.04.zip file which I thought had all I needed. No luck! It seemed to just have the uncompiled code, and from what I could tell I would need to recompile and build it – possibly in c++? Well, I wasn’t going to waste my time with that, so a bit more searching and I found the Win32 (http://www.nasm.us/pub/nasm/releasebuilds/2.09.04/win32/) folder Nasm.exe which I downloaded.

Choosing an IDE

So, I have NASM compiler but to compile anything you need to pass a string of special characters in the command prompt. That’s fine if I was going to just do one program once every couple of years, but since I am aiming to do quite a bit more exploration of NASM I began searching for an IDE.

There were a few options, even apparently Visual Studio with a bit of tweeking could do the job, but from past experience I wanted to avoid the VS route as it can sometimes get confusing. I eventually settled on TextPad which I had used a few years ago for a similar project and it had been simple enough yet powerful enough to do the job. A bit of searching and I found a syntax file for NASM and everything seemed hunky dory.

Configuring TextPad to run the NASM Compiler

Next was to get TextPad to run the NASM compiler. TextPad has this external tools option that allows one to configure special commands. To simplify the process I first created a bat file in the NASM directory that allowed me to simply compile asm files.

The bat file was called as.bat and had just one line of code…

nasm -f bin %1.asm -o %1.com -l %1.lst

Once I had created as.bat I just needed to go into TextPad and create a tool. I have made a quick video of that just showing you where the various settings are which is viewable below.



The 64Bit Problem

So I now have an ‘IDE’ linked to my NASM compiler so everything should be fine right? No! Whenever I tried to compile an asm program it compiles fine, but when I try and run it I get an error – “This version of the file is not compatible with the version Windows you’re running. Check your computer’s system information to see whether you need an x86 (32-bit) or x64 (64-bit) version of the program, and then contact the software publisher."

Well.. it turns out there are a few complications with having a 64 bit OS! So after searching google and coming to any real solution that I could find other than perhaps attempting to build the code for nasm, I eventually resorted to running a VM with Windows XP on it and putting NASM there…

My first hello world program

So I attempt my first hello world program as per an example I found… the code was quite simple and is shown below…

bits16 
org 0x100 
jmp main 
message: db 'Hello World',0ah,0dh,'$' 
main: mov dx,message 
mov ah,09 
int 21h 
int 20h

Running the build tool from TextPad and everything compiles fine and I now have a console app with helllo world shown.

Conclusion

It’s very early days with NASM. I have been spoilt with Visual Studio and high order languages so I assume it will be a painful ride getting into the basics of assembly programming but I am hoping that at the end of it, I will at least have a bit more exposure to a language closer to the metal.
