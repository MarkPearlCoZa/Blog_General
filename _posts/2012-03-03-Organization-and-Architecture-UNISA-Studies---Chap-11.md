---
layout: post
title: Organization and Architecture UNISA Studies - Chap 11
tags: 
category: University
---
Learning Outcomes
Identify the addressing mode used in a given instruction
Give examples of instructions in which specific Pentium addressing modes are used
Discuss the advantages and disadvantages of different instruction formats
Addressing
Addressing mode used in an instruction indicates the way in which the operand is accessed.

The most common addressing modes include
Immediate
Direct
Indirect
Register
Register Indirect
Displacement
Stack
General Note

Typically we have two operands in binary operations (e.g. addition) but generally at least one of the operands is stored in a register. Consequently we refer to the addressing mode of the operand that is not obtained directly from a register as the addressing mode of the instruction.

x86 Addressing Modes
The x86 is equipped with a variety of addressing modes intended to allow the efficient execution of high-level languages.

x86 Addressing Modes available include...

Register Operand
Immediate
Displacement
Base
Base with Displacement
Scaled Index with Displacement
Base with Index and Displacement
Relative
A number of different addressing modes can be identified in the Pentium instruction set. The addressing mode is determine by the operands in the instruction. The following addressing modes are quite straight forward…

Register Addressing
Similar to direct addressing, the only difference is that the address field refers to a register rather than a main memory address.

Advantages - only small address field is needed in the instruction and no time consuming memory references are required
Disadvantages - address space is very limited
Both operands are in registers. The first operand is always the destination operand.

Mov ax,bx               ;Load the value of BX into AX
Add ax,bx               ;AX = AX + BX
Immediate Addressing
This mode can be used to define and use constants or set initial values of variables.

Advantage - no memory reference other than the instruction fetch is required to obtain the operand, thus saving one memory or cache cycle in the instruction cycle.
Disadvantage - size of the number is restricted to the size of the address field, which in most instruction sets is small compared with the word length.
One of the operands is a value that is stored as part of the instruction.

Mov ax,1                ;Load the value 1 into AX
Mov bx,0x010C        ;Load the hexadecimal value 010C into BX
Direct Addressing (Displacement Addressing)
A very simple form of addressing. The address field contains the effective address of the operand.

Disadvantage - it provides only a limited address space
One of the operands is the address of the actual operand. This address is the offset (displacement) from the start of the Data Segment

Mov ax,[102h]         ;Load the contents of memory location 102h into AX
Mov [temp],bx         ;Store the context of BX in the memory location with label temp
Indirect Addressing
Indirect addressing means that the operand given in the instruction contains the address of the actual operand. On the Pentium indirect addressing is only possible when the address of the operand is in a register. We can only have indirect addressing using SI, DI, BP and BX. Hence indexed addressing and base-index addressing, which we consider in the 3 examples given below, are both forms of register indirect addressing. We can also use BP and BX for indirect addressing. If BX or BP is used we call it base addressing.

Indirect addressing has an address field refer to the address of a word in memory, which in turn contains a full length address of the operand

Indirect Addressing Has an address field refer to the address of a word in memory, which in turn contains a full length address of the operand Advantage - for a word length of N, an address space of 2^N is available Disadvantage - instruction execution requires two memory references to fetch the operand, one to get its address and a second to get its value

Indexed Addressing Mode
Example 1

Take a situation where we want to access each individual element in a character string. We can regard the string as an array of characters and use a pointer to access each individual character. Suppose we have the following string that starts at memory position 102h:

String	S	C	I	E	N
Offset	0	1	2	3	4
 

If we set SI (the source index register) to the start of the string, we can use SI as a pointer to access the characters one at a time. The character ‘S’ is stored at offset 0 from the start of the string and the character ‘N’ is stored at offset 13 (base 10) from the start of the string.

db ‘SCIENCE IS FUN’

mov si,102h    ;Move address of start of string to SI

add si,11        ;Add 11 to SI. Nasm assumes that numbers are decimal

mov al,[si]      ;Move the contents of the address pointed to by SI to AL. AL will contain the character ‘F’

Base-Indexed Addressing
Base-indexed addressing can also be used to access array elements. BX and BP can be sued as base registers. When we use this type of addressing mode, the base register is normally set to the start of the array and the index register is used as an offset from the start of the array.

Displacement Addressing
A powerful mode of addressing combines the capabilities of direct addressing and register indirect addressing. It requires that the instruction have two address fields, at least one of which is explicit. The value contained in one address field is used directly. The other address field, or an implicit reference based on opcode refers to a register whose contents are added to A to produce the effective addressing. Some of its implementations include…

Relative Addressing
Base-register addressing
Indexing
Stack Addressing
A stack is a linear array of locations. The stack pointer is maintained by a register, thus references to stack locations in memory are in fact register indirect addresses. The stack mode of addressing is a form of implied addressing. The machine instructions need not include a memory reference but implicitly operate on the top of the stack.

The SP register contains the offset from the beginning of the stack to the top of the stack. We use the instructions PUSH and POP to push values onto the stack and to pop them off the stack respectively. This addressing mode is called ‘stack addressing’

PUSH: An item is stored on top of the stack and the stack pointer adjusted accordingly. SP is decremented before a new item is placed on the stack. This means that the stack grows from high memory to low memory. We say that the stack ‘grows’ backward in memory. SP points to the last item that was pushed onto the stack.

POP: An item is removed from the top of the stack and the stack pointer adjusted accordingly. SP is incremented after an item has been removed from the stack. SP points to the new top of stack

Note that the operations of PUSH and POP are slightly different on some older machines – pre Pentium era – but since that was significantly long ago I am not going to worry about covering it.

Instruction Formats
An instruction format defines the layout of the bits of an instruction in terms of its constituent fields. An instruction format must include an opcode and implicitly or explicitly

Allocation of bits

The following factors go into deciding…

Number of addressing modes
Number of operands
Register versus memory
Number of register sets
Address range
Address granularity
Variable-Length Instructions

The benefit of variable length instructions is that it is easy to provide a large number of opcodes, with different lengths and more flexible addressing.

The price you pay for variable length instructions is an increase in the complexity of the processor.

The use of variable length instructions does not remove the desirability of making all of the instruction lengths integrally related related to the word length. A typical approach is because the processor does not know the length of the next instruction, it will fetch a number of bytes or words equal to at least the longest possible instruction. This means that sometimes multiple instructions are fetched.

x86 and ARM Instruction Formats
x86 Instruction Formats

The x86 is equipped with a variety of instruction formats. Instructions are made up of from zero to four optional instruction prefixes, a 1 or 2 byte opcode, an address specifier (which consists of the ModR/m byte and the Scale Index byte) an optional displacement and an optional immediate field.

Instruction prefixes – if present consists of the LOCK prefix or one of the repeat prefixes. Lock is used to mark memory for exclusive use in a multiprocessor environment. The repeat prefixes specify repeated operation of a string, which enables the x86 to process strings much faster than with a regular software loop.
Segment override – explicitly specifies which segment register an instruction should use, overriding the default segment-register selection generated by the x86 for that instruction
Operand size – an instruction has a default operand size of 16 or 32 bits, and the operand prefix switches between 32 bit and 16 bit operands
Address size – the processor can address memory using either 16 or 32 bit addresses. The address size determines the displacement size in instructions and the size of address offsets generated during effective address calculation
Opcode – The opcode field is 1,2 or 3 bytes in length. The opcode may also include bits that specify if data is byte, or full-size, direction of data operation and whether an immediate data field must be sign extended
ModR/m – this byte and the next provide addressing information. The ModR/m byte specifies whether an operand is in a register or in memory, if it is in memory, then fields within the byte specify the addressing mode to be used.
SIB – certain encoding of the ModR/m byte specifies the inclusion of the SIB byte to specify fully the addressing mode. The SIB byte consists of three field.
Displacement – when the addressing mode specifier indicates that a displacement is used, an 8, 16 or 32 bit signed integer displacement field is added
Immediate – provides the value of an 8, 16, or 32 bit operand
The encoding of the x86 instruction set is very complex. This is partly to do with the need to be backward compatible with the 8086 machine and partly with a desire on the part of the designers to provide every possible assistance to the compiler writer in producing efficient code.

ARM Instruction Formats

All instructions in the ARM architecture are 32 bits long and follow a regular format.

Assembly Language
A processor can understand and execute machine instructions. Such instructions are simply binary numbers stored in the computer. If a programmer wished to program directly in machine language, then it would be necessary to enter the program as binary data.

A improvement to this is to make use of the symbolic name or mnemonic of each instruction. Each line of input still represent one memory location.

Programs written in assembly language are translated into machine language by an assembler. An assembler must not only do the symbolic translation but also assign some form of memory addresses to symbolic addresses.

The development of assembly language was a major milestone in the evolution of computer technology. It was the first step to the high-level languages in use today. Although few programmers use assembly language, virtually all machines provide one. They are used, if at all, for system programs such as compilers and I/O routines.