---
layout: post
title: Organization and Architecture UNISA Studies – Chap 13
tags: 
category: University
---
Learning Outcomes
Explain the advantages of using a large number of registers
Discuss the way in which compilers optimize register usage
Discuss the evolution of CISC machines
Describe the characteristics of RISC architecture
Discuss the RISC vs. CISC controversy
Describe the way in which RISC and CISC design principles can be combined
Instruction Execution Characteristics
To understand the the line of reasoning of RISC advocates, we need a brief overview of instruction execution characteristics. These include…

Operations
Operands
Procedure Calls
These three sections can be studied in depth in the textbook at pages 503 - 505

A number of groups have come up with the conclusion that the attempt to make the instruction set architecture closer to HLLs (High Level Languages) is not the most effective design strategy. Rather HLL’s can be best supported by optimizing performance of the most time-consuming features of typical HLL programs.

Generally 3 main characteristics came up to improve performance…

Use a large number of registers or use a compiler to optimize register usage
Careful attention needs to be paid to the design of instruction pipelines
A simplified (reduced) instruction set is indicated
The use of a large register optimization
One of the most important design principles of RISC machines is the use of a large number of registers. The concept of register windows and the use of a large register file versus the use of cache memory are discussed.

On the face of it, the use of a large set of registers should decrease the need to access memory. The design task is to organize the registers in such a fashion that this goal is realized.

Read page 507 – 510 for a detailed explanation.

Compiler-based register optimization
 

Reduced Instructions Set Architecture
There are two advantages to smaller programs…

Because the program takes up less memory, there is a savings in that resource (this was more compelling when memory was more expensive)
Smaller programs should improve performance, and this will happen in two ways – fewer instructions means fewer instruction bytes to be fetched and in a paging environment smaller programs occupy fewer pages, reducing page faults.
Certain characteristics are common to RISC processors…

One instruction per cycle
Register-to-register operations
Simple addressing modes
Simple instruction formats
RISC vs. CISC
After initial enthusiasm for RISC machines, there has been a growing realization that

RISC designs may benefit from the inclusion of some CISC features
CISC designs may benefit from the inclusion of some RISC features