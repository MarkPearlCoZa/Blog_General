---
layout: post
title: NASM – writing to the console
tags: 
category: General
---
If you are new to NASM like me – you might find the following code snippets useful just to get started… (this is targeted to the Windows environment, it may be different in Linux)

Printing the number 6 character to the console… the value in the ah register changes to 02h and you mov the message to dl

org 0x100
bits 16
jmp main

displayCharacter:
mov ah,2h
int 21h
ret

main:
mov dl,36h
call displayCharacter
int 20h
Printing a string to the console…. the value in the ah register changes to 09h and you mov the message to dx

org 0x100
bits 16
jmp main

message: db 'example text'

displayString:
mov ah,09h
int 21h
ret

main:
mov dx,message
call displayString
int 20h