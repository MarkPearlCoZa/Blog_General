---
layout: post
title: Writing multiple lines of text to the console in nasm
tags: 
category: General
---
In it’s simplest form… the following asm code should work

org 0x100
bits 16
jmp main

message: db 'example text ', 0xa,'and some more text', 0xa, 'and another line','$'

main:
mov dx,message
mov ah,09h
int 21h
int 20h
 

Points to look out for…

0xa is a newline operand…
‘$’ signifies the end of the text
Everything else should look pretty standard…