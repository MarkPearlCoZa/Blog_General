---
layout: post
title: Organization and Architecture UNISA Studies - Chap 12
tags: 
category: University
---
Learning Outcomes
Describe the internal structure of the CPU in general
Describe the register organization of the x86/Pentium
Describe what an interrupt is and what happens when an interrupt occurs
Describe what an exception is and what happens when an exception occurs
Describe the instruction cycle for indirect addressing
Discuss the basic principle of instruction pipelining
Processor Organization
A processor must be able to do the following…

Fetch Instructions
Interpret Instruction
Fetch Data
Process Data
Write Data
To perform these actions the processor needs some way to store instructions and data temporarily. A simple representation of a processor could be shown as follows..

Basic CPU

If you look closer at the internal organization of a processor you will notice that it is very similar to the construction of a computer.

CPU Internal

Register Organization
Within the processor there is a set of registers that function as a level of memory above the main memory and cache in the hierarchy/ The registers in the processor perform two roles

User-visible registers – enable machine or assembly language programmer to minimize main memory references by optimizing use of registers
Control and status registers – Used by control unit to control the operation of the processor and by privileged operating system programs to control the execution of programs
Note there is no clean separation of registers into these two categories. On some machines the program counter is user visible while on others it is not.

User Visible Registers

User visible registers can be categorized into the following categories…

General Purpose
Data
Address
Condition codes
Control & Status Registers

There are a variety of processor registers that are used to control the operation of the processor – most of these are not visible to the user but some may be visible to machine instructions executed in a control or operating system mode.

Four registers are essential to instruction execution

Program counter (PC) – address of an instruction to be fetched
Instruction register (IR) – instruction most recently fetched
Memory address register (MAR) – address of a location in memory
Memory buffer register (MBR) – word of data to be written to memory or the word most recently read
Many processors include a register or set of registers known as the program status word (PSW) that contains status information. Some of the common fields include…

Sign – sign bit of the result of the last arithmetic operation
Zero – Set when the result is 0
Carry – Set if an operation resulted in a carry into or borrow out of a high-order bit
Equal – Set if a logical compare result is equality
Overflow – Used to indicate arithmetic overflow
Interrupt Enable/Disable – Used to enable / disable interrupts
Supervisor – indicates whether the processor is executing in supervisor or user mode
Instruction Pipelining
Instruction pipelining is a technique that helps improve performance of a processor.

The concept is very similar to an assembly line, by having a set of processes set up, you can have multiple items worked on simultaneously. The constraints of instruction pipelining is that the current process is always limited to the speed of the process before it.

Refer to the text book (pages 466 to 468) for a detailed walkthrough of instruction pipelining.

In addition, the more processes you work on simultaneously, the more complexity you add to the design.

Two dominants factors to note are…

At each stage of the pipeline, there is some overhead in moving data from buffer to buffer in performing various preparation and delivery functions. This overhead can significantly lengthen the total execution time of a single instruction. This is significant when sequential instructions are logically dependent, either through heavy use of branching or through memory access dependencies.
The amount of control logic required to handle memory and register dependencies and to optimize the use of the pipeline increases enormously with the number of stages. This can lead to a situation where the logic controlling the gating between stages is more complex than the stages being controlled.
The x86/Pentium Processor
NB: The notes in the textbook are fairly hard to grasp but you should read through them. Notes in the study guide are better.

Registers

Registers are special storage components inside the CPU. The registers common to all the Intel processors are 16 bits in size and can be classified as follows:

General purpose registers (AX, BX, CX, DX)
Segment registers (CS, DS, SS, ES)
Index registers (SI, DI)
Pointers (BP, IP, SP)
Flags register (Nine of the bits/flags in this register are of some importance)
The 80386/80486 and subsequent processors including the Pentium have extended general purpose registers, extended index registers and extended pointer registers that are 32 bits long. These are written as above with a prefix E. The extended versions of the general purpose registers are called EAX, EBX, ECX and EDX.

 

General Purpose Registers

Used for data movement and for arithmetic
Each register can be addressed as either one 16 bit (2 bytes) register or as two 8 bit (1 byte) registers
The leftmost byte is the high portion and the rightmost byte is the low portion
NB Bits are numbered from right to left on Intel machines

The ARM Processor

AX Register – known as the primary accumulator. AX is mainly used for operations involving data movement, input/output and arithmetic. Some instructions like MUL and DIV assume that AX contains the multiplicand and dividend.

BX Register – only general purpose register that can be used as a pointer to extend addressing. Referred to as the base register. It is also used form arithmetic.

CX Register – known as the count register. Used top control the number of times loops are to be executed or the number of shifts to perform. Also used for arithmetic.

DX Register – Some input/output operations like IN and OUT use the DX register. Multiply and divide operations involving 16 bit registers make use of the combination of DX and AX. Known as the data register.

Segments and segment registers

Memory consists of a collection of segments, each segment is 64k long
A segment is an area in memory that begins on a paragraph boundary (an address that is a multiple of 1610)
Segments can overlap
The starting address of a segment always end with a 0 (in Hex) thus the designers decided to not store the last digit since it was predictable
A segment may be located anywhere in memory and may be as small as 1 paragraph
A program written in Intel assembly language is divided into three primary segments:

Code segment
Data segment
Stack segment
The code segment…

Is pointed to by the CS register
Contains the machine instructions of the program
All references to memory locations that contain instructions of a program are relative to the start of a segment specified by the contents of the CS register
A byte of memory is referenced by the segment that contains it, followed by an offset form the beginning of that segment indicated by the IP register (instruction pointer)
The notations used is segment:offset
The IP register always contains the offset of the next instruction to be executed
The data segment…

Pointed to by the DS register
Contains the variables, constants and work areas of a program
The actual address where data is fetched from memory when a instruction is executed is not the physical memory locations but the memory location relative to the contents of the DS register
The stack segment…

Contains the program stack
The extra segment register….

ES is used during the manipulation of sequences of characters by some string operations
Index Registers

Index registers contain the offset, relative to the start of the segment.
SI and DI are used to indicate source and destination addresses when strings of characters are written to and read from memory
SI usually contains an offset value from the DS register, but it can address any variable
The source string is pointed to by the SI register
The DI register is the destination for string movement instructions
Pointer and stack registers

The stack is a special area in memory that is used fro the temporary storage of addresses and data
The stack is located in the stack segment
The stack pointer register holds the address of the last element to be added to the stack
The base pointer register contains an offset from the SS register
The flags register

EFLAGS register is used as a flags register
Nine of the 32 bits of this register are common to all Intel processors – we do not worry about the other bits in this course
Each time an arithmetic instruction is executed, certain flags will be set either to 1 or 0 to indicate the outcome of the operation
Not all instructions affect the flags and not all flags are affected by instructions that do have an effect on flags
Refer to your course summary to see the bits in the flags register that represent the individual flags

The flags that concern us most are SF, ZF, CF and OF
CF & OF are the most complicated ones
CF flag…

During arithmetic operations, the carry flag indicates whether the unsigned number which is the result of the operation is too big or too small to be held in the specified register or memory location. For unsigned data, all bits are intended to be data bits and the largest unsigned number that can be stored in n bits is (2^n)-1 thus the largest unsigned numbers that van be stored in an 8-bit and 16-bit register are 255 and 65 535 respectively.

Reverse Byte Order in Memory

Intel machines store bytes in reverse byte order in memory. Consider the number 0015h – two bytes are required to store this number. The 16 bit number 0015h consists of a high-order byte (00) and a low order byte (15h)

In memory this would be represented as…

Memory position	101h	102h
Hex number	15h	00
 

This could be confusing and so special care should be taken to keep this in mind when storing number in memory (not registers).

Interrupts

An interrupt causes the interruption of normal program execution. The flow of control is interrupted. Interrupts can be caused by both hardware or software. Interrupts are handled by either DOS or BIOS.

Software interrupts…

Generated by an INT instruction and is a call to a specific interrupt routine
Interrupts can be invoked by using the INT instruction
Hardware interrupts…

Sometimes called an external interrupts
Generated by a special chip called the Interrupt Controller
IC requests the CPU to suspend the current program temporarily and to process the interrupts
Hardware interrupt is handled by the interrupt handler which associates a specific vector in the interrupt vector table with that particular hardware interrupt
The interrupt vector table

Each of the interrupts available on the Intel chips has a 4 byte entry in the interrupt vector table to accommodate an offset and a code segment address.
Each code segment and offset points to its own interrupt handler. This is a block of code similar to a procedure, which must be executed if the particular interrupt occurs.
the INT instruction

The operating system does most of the work with interrupts. The developer only needs to place one or more values in register and invoke the relevant interrupt instruction. The interrupt instruction used for Intel machines is INT.

The format of the INT instruction is as follows: int number

Interrupt instructions that we will use frequently are

INT 20h (causes the program to terminate and control to be transferred to DOS)
INT 21 (allows operations such as reading a character from the keyboard, printing a character, displaying etc). We call the specific action to be performed a function or service. The AH register is used to specify which function is required.