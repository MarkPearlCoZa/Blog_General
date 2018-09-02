---
layout: post
title: Organization and Architecture UNISA Studies – Chap 5
tags: 
category: University
---
Learning Outcomes
Describe the operation of a memory cell
Explain the difference between DRAM and SRAM
Discuss the different types of ROM
Explain the concepts of a hard failure and a soft error respectively
Describe SDRAM organization
Semiconductor Main Memory
The two traditional forms of RAM used in computers are DRAM and SRAM

DRAM (Dynamic RAM)

Divided into two technologies…

Dynamic
Static
Dynamic RAM is made with cells that store data as charge on capacitors. The presence or absence of charge in a capacitor is interpreted as a binary 1 or 0. Because capacitors have natural tendency to discharge, dynamic RAM requires periodic charge refreshing to maintain data storage. The term dynamic refers to the tendency of the stored charge to leak away, even with power continuously applied.

Although the DRAM cell is used to store a single bit (0 or 1), it is essentially an analogue device. The capacitor can store any charge value within a range, a threshold value determines whether the charge is interpreted as a 1 or 0.

SRAM (Static RAM)

SRAM is a digital device that uses the same logic elements used in the processor. In SRAM, binary values are stored using traditional flip flop logic configurations.

SRAM will hold its data as along as power is supplied to it.

Unlike DRAM, no refresh is required to retain data.

SRAM vs. DRAM

DRAM is simpler and smaller than SRAM. Thus it is more dense and less expensive than SRAM.

The cost of the refreshing circuitry for DRAM needs to be considered, but if the machine requires a large amount of memory, DRAM turns out to be cheaper than SRAM.

SRAMS are somewhat faster than DRAM, thus SRAM is generally used for cache memory and DRAM is used for main memory.

Types of ROM

Read Only Memory (ROM) contains a permanent pattern of data that cannot be changed. ROM is non volatile meaning no power source is required to maintain the bit values in memory.

While it is possible to read a ROM, it is not possible to write new data into it.

An important application of ROM is microprogramming, other applications include library subroutines for frequently wanted functions, System programs, Function tables.

A ROM is created like any other integrated circuit chip, with the data actually wired into the chip as part of the fabrication process.

To reduce costs of fabrication, we have PROMS.

PROMS are…

Written only once
Non-volatile
Written after fabrication
Another variation of ROM is the read-mostly memory, which is useful for applications in which read operations are far more frequent than write operations, but for which non volatile storage is required. There are three common forms of read-mostly memory, namely…

EPROM
EEPROM
Flash memory
Error Correction
Semiconductor memory is subject to errors, which can be classed into two categories…

Hard failure – Permanent physical defect so that the memory cell or cells cannot reliably store data
Soft failure – Random error that alters the contents of one or more memory cells without damaging the memory (common cause includes power supply issues, etc.)
Most modern main memory systems include logic for both detecting and correcting errors.

Error detection works as follows…

When data is to be read into memory, a calculation is performed on the data to produce a code
Both the code and the data are stored
When the previously stored word is read out, the code is used to detect and possibly correct errors
The error checking provides one of 3 possible results…

No errors are detected – the fetched data bits are sent out
An error is detected, and it is possible to correct the error. The data bits plus error correction bits are fed into a corrector, which produces a corrected set of bits to be sent out
An error is detected, but it is not possible to correct it. This condition is reported
Hamming Code

See wiki for detailed explanation.

We will probably need to know how to do a hemming code – refer to the textbook (pg. 188 – 189)

Advanced DRAM organization
One of the most critical system bottlenecks when using high-performance processors is the interface to main memory. This interface is the most important pathway in the entire computer system. The basic building block of main memory remains the DRAM chip.

In recent years a number of enhancements to the basic DRAM architecture have been explored, and some of these are now on the market including…

SDRAM (Synchronous DRAM)
DDR-DRAM
RDRAM
SDRAM (Synchronous DRAM)

SDRAM exchanges data with the processor synchronized to an external clock signal and running at the full speed of the processor/memory bus without imposing wait states.
SDRAM employs a burst mode to eliminate the address setup time and row and column line precharge time after the first access
In burst mode a series of data bits can be clocked out rapidly after the first bit has been accessed
SDRAM has a multiple bank internal architecture that improves opportunities for on chip parallelism
SDRAM performs best when it is transferring large blocks of data serially
There is now an enhanced version of SDRAM known as double data rate SDRAM or DDR-SDRAM that overcomes the once-per-cycle limitation of SDRAM