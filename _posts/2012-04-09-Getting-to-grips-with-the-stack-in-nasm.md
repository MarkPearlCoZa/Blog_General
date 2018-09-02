---
layout: post
title: Getting to grips with the stack in nasm
tags: 
category: General
---
Today I spent a good part of my day getting to grips with the stack and nasm. After looking at my notes on nasm I think this is one area for the course I am doing they could focus more on… So here are some snippets I have put together that have helped me understand a little bit about the stack…

Simplest example of the stack
You will probably see examples like the following in circulation… these demonstrate the simplest use of the stack…

org 0x100 
bits 16 
jmp main 

main: 
push 42h 
push 43h 
push 44h 

mov ah,2h ;set to display characters 

pop dx    ;get the first value 
int 21h   ;and display it 

pop dx    ;get 2nd value 
int 21h   ;and display it 

pop dx    ;get 3rd value 
int 21h   ;and display it 

int 20h 

The output from above code would be…

DCB

Decoupling code using “call” and “ret”
This is great, but it oversimplifies what I want to use the stack for… I do not know if this goes against the grain of assembly programmers or not, but I want to write loosely coupled assembly code – and I want to use the stack as a mechanism for passing values into my decoupled code. In nasm we have the call and return instructions, which provides a mechanism for decoupling code, for example the following could be done…

org 0x100
bits 16
jmp main

;----------------------------------------
displayChar:
mov ah,2h
mov dx,41h
int 21h
ret

;----------------------------------------
main:
call displayChar
int 20h
 

This would output the following to the console

A

So, it would seem that call and ret allow us to jump to segments of our code and then return back to the calling position – a form of segmenting the code into what we would called in higher order languages “functions” or “methods”.

The only issue is, in higher order languages there is a way to pass parameters into the functions and return results. Because of the primitive nature of the call and ret instructions, this does not seem to be obvious. We could of course use the registers to pass values into the subroutine and set values coming out, but the problem with this is we…

Have a limited number of registers
Are threading our code with tight coupling (it would be hard to migrate methods outside of their intended use in a particular program to another one)
With that in mind, I turn to the stack to provide a loosely coupled way of calling subroutines…

First attempt with the Stack
Initially I thought this would be simple… we could use code that looks as follows to achieve what I want…

org 0x100
bits 16
jmp main

;----------------------------------------
displayChar:
mov ah,2h
pop dx
int 21h
ret

;----------------------------------------
main:
push 41h
call displayChar
int 20h
 

However running this application does not give the desired result, I want an ‘A’ to be returned, and I am getting something totally different (you will to).

Reading up on the call and ret instructions a discovery is made… they are pushing and popping things onto and off the stack as well…

When the call instruction is executed, the current value of IP (the address of the instruction to follow) is pushed onto the stack, when ret is called, the last value on the stack is popped off into the IP register. In effect what the above code is doing is as follows with the stack…

push 41h
push current value of ip
pop current value of ip to dx
pop 41h to ip
This is not what I want, I need to access the 41h that I pushed onto the stack, but the call value (which is necessary) is putting something in my way. So, what to do?

Remember we have other registers we can use as well as a thing called indirect addressing…

So, after some reading around, I came up with the following approach using indirect addressing…

org 0x100
bits 16
jmp main

;----------------------------------------
displayChar:
mov bp,sp
mov ah,2h
mov dx,[bp+2]
int 21h
ret

;----------------------------------------
main:
push 41h
call displayChar
int 20h
In essence, what I have done here is used a trick with the stack pointer… it goes as follows…

Push 41 onto the stack
Make the call to the function, which will push the IP register onto the stack and then jump to the displayChar label
Move the value in the stack point to the bp register (sp currently points at IP register)
Move the at the location of bp minus 2 bytes to dx (this is now the value 41h)
display it,
execute the ret instruction, which pops the ip value off the stack and goes back to the calling point
This approach is still very raw, some further reading around shows that I should be pushing the value of bp onto the stack before replacing it with sp, but it is the starting thread to getting loosely coupled subroutines.

Let’s see if you get what the following output would be?

org 0x100
bits 16
jmp main

;----------------------------------------
displayChar:
mov bp,sp
mov ah,2h

mov dx,[bp+4]
int 21h

mov dx,[bp+2]
int 21h
ret

;----------------------------------------
main:
push 41h
push 42h
call displayChar
int 20h
The output is…

AB

Where to from here?
If by any luck some assembly programmer comes along and see this code and notices that I have made some fundamental flaw in my logic… I would like to know, so please leave a comment… appreciate any feedback!