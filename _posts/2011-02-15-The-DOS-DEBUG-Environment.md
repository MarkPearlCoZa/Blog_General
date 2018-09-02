---
layout: post
title: The DOS DEBUG Environment
tags: 
category: General
---
 

Today I thought I would go back in time and have a look at the DEBUG command that has been available since the beginning of dawn in DOS, MS-DOS and Microsoft Windows. up to today I always knew it was there, but had no clue on how to use it so for those that are interested this might be a great geek party trick to pull out when you want the awe of the younger generation and want to show them what “real” programming is about.

But wait, you will have to do it relatively quickly as it seems like DEBUG was finally dumped from the Windows group in Windows 7. Not to worry, pull out that Windows XP box which will get you even more geek points and you can still poke DEBUG a bit. So, for those that are interested and want to find out a bit about the history of DEBUG read the wiki link here.

That all put aside, lets get our hands dirty..

How to Start DEBUG in Windows

Make sure your version of Windows supports DEBUG.

Open up a console window

Make a directory where you want to play with debug – in my instance I called it C221

Enter the directory and type Debug

You will get a response with a – as illustrated in the image below…

001

 

The commands available in DEBUG

There are several commands available in DEBUG. The most common ones are

A (Assemble)
R (Register)
T (Trace)
G (Go)
D (Dump or Display)
U (Unassemble)
E (Enter)
P (Proceed)
N (Name)
L (Load)
W (Write)
H (Hexadecimal)
I (Input)
O (Output)
Q (Quit)
I am not going to cover all these commands, but what I will do is go through a few of them briefly.

A is for Assemble Command (to write code)

The A command translates assembly language statements into machine code. It is quite useful for writing small assembly programs.

Below I have written a very basic assembly program.

002

The code typed out is as follows

mov ax,0015

mov cx,0023

sub cx,ax

mov [120],al

mov cl,[120]A

nop

R is for Register (to jump to a point in memory)

The r command turns out to be one of the most frequent commands you will use in DEBUG. It allows you to view the contents of registers and to change their values. It can be used with the following combinations…

R – Displays the contents of all the registers
R f – Displays the flags register
R register_name – Displays the contents of a specific register
013

All three methods are illustrated in the image above

T is for Trace (To execute a program step by step)

The t command allows us to execute the program step by step. Before we can trace the program we need to point back to the beginning of the program. We do this by typing in r ip, which moves us back to memory point 100.

We then type trace which executes the first line of code (line 100) (As shown in the image below starting from the red arrow).

003

You can see from the above image that the register AX now contains 0015 as per our instruction mov ax,0015

You can also see that the IP points to line 0103 which has the MOV CX,0023 command

If we type t again it will now execute the second line of the program which moves 23 in the cx register.

004

Again, we can see that the line of code was executed and that the CX register now holds the value of 23.

What I would like to highlight now is the section underlined in red. These are the status flags. The ones we are going to look at now are 1st (NV), 4th (PL), 5th (NZ) & 8th (NC)

NV means no overflow, the alternate would be OV
PL means that the sign of the previous arithmetic operation was Plus, the alternate would be NG (Negative)
NZ means that the results of the previous arithmetic operation operation was Not Zero, the alternate would be ZR
NC means that No final Carry resulted from the previous arithmetic operation. CY means that there was a final Carry.
We could now follow this process of entering the t command until the entire program is executed line by line.

G is for Go (To execute a program up to a certain line number)

So we have looked at executing a program line by line, which is fine if your program is minuscule BUT totally unpractical if we have any decent sized program. A quicker way to run some lines of code is to use the G command.

The ‘g’ command executes a program up to a certain specified point. It can be used in connection with the the reset IP command. You would set your initial point and then run the G command with the line you want to end on.

005

P is for Proceed (Similar to trace but slightly more streamlined)

Another command similar to trace is the proceed command. All that the p command does is if it is called and it encounters a CALL, INT or LOOP command it terminates the program execution. In the example below I modified our example program to include an int 20 at the end of it as illustrated in the image below…

007

Then when executing the code when I encountered the int 20 command I typed the P command and the program terminated normally (illustrated below).

006

D is for Dump (or for those more polite Display)

So, we have all these assembly lines of code, but if you have ever opened up an exe or com file in a text/hex editor, it looks nothing like assembly code. The D command is a way that we can see what our code looks like in memory (or in a hex editor).

008

If we examined the image above, we can see that Debug is storing our assembly code with each instruction following immediately after the previous one. For instance in memory address 110 we have int and 111 we have 20. If we examine the dump of memory we can see at memory point 110 CD is stored and at memory point 111 20 is stored.

U is for Unassemble (or Convert Machine code to Assembly Code)

So up to now we have gone through a bunch of commands, but probably one of the most useful is the U command. Let’s say we don’t understand machine code so well and so instead we want to see it in its equivalent assembly code. We can type the U command followed by the start memory point, followed by the end memory point and it will show us the assembly code equivalent of the machine code.

009

E is for a bunch of things…

The E command can be used for a bunch of things… One example is to enter data or machine code instructions directly into memory. It can also be used to display the contents of memory locations. I am not going to worry to much about it in this post.

N / L / W is for Name, Load & Write

So we have written out assembly code in debug, and now we want to save it to disk, or write it as a com file or load it. This is where the N, L & W command come in handy.

The n command is used to give a name to the executable program file and is pretty simple to use.

The w command is a bit trickier. It saves to disk all the memory between point bx and point cx so you need to specify the bx memory address and the cx memory address for it to write your code. Let’s look at an example illustrated below. You do this by calling the r command followed by the either bx or cx.

010

We can then go to the directory where we were working and will see the new file with the name we specified.

011

The L command is relatively simple. You would first specify the name of the file you would like to load using the N command, and then call the L command.

012

Q is for Quit

The last command that I am going to write about in this post is the Q command. Simply put, calling the Q command exits DEBUG.

Commands we did not Cover

Out of the standard DEBUG commands we covered A, T, G, D, U, E, P, R, N, L & W.

The ones we did not cover were H, I & O – I might make mention of these in a later post, but for the basics they are not really needed.

Some Useful Resources

Please note this post is based on the COS2213 handouts for UNISA
A Guide to DEBUG - http://mirror.href.com/thestarman/asm/debug/debug.htm#NT