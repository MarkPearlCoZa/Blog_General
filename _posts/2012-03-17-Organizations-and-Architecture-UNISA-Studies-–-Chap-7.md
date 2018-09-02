---
layout: post
title: Organizations and Architecture UNISA Studies – Chap 7
tags: 
category: University
---
Learning Outcomes
Name different device categories
Discuss the functions and structure of I/.O modules
Describe the principles of Programmed I/O
Describe the principles of Interrupt-driven I/O
Describe the principles of DMA
Discuss the evolution characteristic of I/O channels
Describe different types of I/O interface
Explain the principles of point-to-point and multipoint configurations
Discuss the way in which a FireWire serial bus functions
Discuss the principles of InfiniBand architecture
External Devices
An external device attaches to the computer by a link to an I/O module. The link is used to exchange control, status, and data between the I/O module and the external device.

External devices can be classified into 3 categories…

Human readable – e.g. video display
Machine readable – e.g. magnetic disk
Communications – e.g. wifi card
I/O Modules
An I/O module has two major functions…

Interface to the processor and memory via the system bus or central switch
Interface to one or more peripheral devices by tailored data links
Module Functions

The major functions or requirements for an I/O module fall into the following categories…

Control and timing
Processor communication
Device communication
Data buffering
Error detection
I/O function includes a control and timing requirement, to coordinate the flow of traffic between internal resources and external devices.

Processor communication involves the following…

Command decoding
Data
Status reporting
Address recognition
The I/O device must be able to perform device communication. This communication involves commands, status information, and data.

An essential task of an I/O module is data buffering due to the relative slow speeds of most external devices.

An I/O module is often responsible for error detection and for subsequently reporting errors to the processor.

I/O Module Structure

An I/O module functions to allow the processor to view a wide range of devices in a simple minded way.
The I/O module may hide the details of timing, formats, and the electro mechanics of an external device so that the processor can function in terms of simple reads and write commands.
An I/O channel/processor is an I/O module that takes on most of the detailed processing burden, presenting a high-level interface to the processor.
There are 3 techniques are possible for I/O operations

Programmed I/O
Interrupt[t I/O
DMA Access
Programmed I/O
When a processor is executing a program and encounters an instruction relating to I/O it executes that instruction by issuing a command to the appropriate I/O module. With programmed I/O, the I/O module will perform the requested action and then set the appropriate bits in the I/O status register. The I/O module takes no further actions to alert the processor.

I/O Commands

To execute an I/O related instruction, the processor issues an address, specifying the particular I/O module and external device, and an I/O command. There are four types of I/O commands that an I/O module may receive when it is addressed by a processor…

Control – used to activate a peripheral and tell it what to do
Test – Used to test various status conditions associated with an I/O module and its peripherals
Read – Causes the I/O module to obtain an item of data from the peripheral and place it in an internal buffer
Write – Causes the I/O module to take an item of data form the data bus and subsequently transmit that data item to the peripheral
The main disadvantage of this technique is it is a time consuming process that keeps the processor busy needlessly

I/O Instructions

With programmed I/O there is a close correspondence between the I/O related instructions that the processor fetches from memory and the I/O commands that the processor issues to an I/O module to execute the instructions.

Typically there will be many I/O devices connected through I/O modules to the system – each device is given a unique identifier or address – when the processor issues an I/O command, the command contains the address of the address of the desired device, thus each I/O module must interpret the address lines to determine if the command is for itself.

When the processor, main memory and I/O share a common bus, two modes of addressing are possible…

Memory mapped I/O
Isolated I/O
(for a detailed explanation read page 245 of book)

The advantage of memory mapped I/O over isolated I/O is that it has a large repertoire of instructions that can be used, allowing more efficient programming.
The disadvantage of memory mapped I/O over isolated I/O is that valuable memory address space is sued up.
Interrupts driven I/O
Interrupt driven I/O works as follows…

The processor issues an I/O command to a module and then goes on to do some other useful work
The I/O module will then interrupts the processor to request service when is is ready to exchange data with the processor
The processor then executes the data transfer and then resumes its former processing
Interrupt Processing

The occurrence of an interrupt triggers a number of events, both in the processor hardware and in software. When an I/O device completes an I/O operations the following sequence of hardware events occurs…

The device issues an interrupt signal to the processor
The processor finishes execution of the current instruction before responding to the interrupt
The processor tests for an interrupt – determines that there is one – and sends an acknowledgement signal to the device that issues the interrupt. The acknowledgement allows the device to remove its interrupt signal
The processor now needs to prepare to transfer control to the interrupt routine. To begin, it needs to save information needed to resume the current program at the point of interrupt. The minimum information required is the status of the processor and the location of the next instruction to be executed.
The processor now loads the program counter with the entry location of the interrupt-handling program that will respond to this interrupt.
It also saves the values of the process registers because the Interrupt operation may modify these
The interrupt handler processes the interrupt – this includes examination of status information relating to the I/O operation or other event that caused an interrupt
When interrupt processing is complete, the saved register values are retrieved from the stack and restored to the registers
Finally, the PSW and program counter values from the stack are restored.
Design Issues

Two design issues arise in implementing interrupt I/O

Because there will be multiple I/O modules, how does the processor determine which device issued the interrupt?
If multiple interrupts have occurred, how does the processor decide which one to process?
Addressing device recognition, 4 general categories of techniques are in common use…

Multiple interrupt lines
Software poll
Daisy chain
Bus arbitration
For a detailed explanation of these approaches read page 250 of the textbook.

Interrupt driven I/O while more efficient than simple programmed I/O still requires the active intervention of the processor to transfer data between memory and an I/O module, and any data transfer must traverse a path through the processor. Thus is suffers from two inherent drawbacks…

The I/O transfer rate is limited by the speed with which the processor can test and service a device
The processor is tied up in managing an I/O transfer; a number of instructions must be executed for each I/O transfer
Direct Memory Access
When large volumes of data are to be moved, an efficient technique is direct memory access (DMA)

DMA Function

DMA involves an additional module on the system bus. The DMA module is capable of mimicking the processor and taking over control of the system from the processor. It needs to do this to transfer data to and from memory over the system bus. DMA must the bus only when the processor does not need it, or it must force the processor to suspend operation temporarily (most common – referred to as cycle stealing).

When the processor wishes to read or write a block of data, it issues a command to the DMA module by sending to the DMA module the following information…

Whether a read or write is requested using the read or write control line between the processor and the DMA module
The address of the I/O device involved, communicated on the data lines
The starting location in memory to read from or write to, communicated on the data lines and stored by the DMA module in its address register
The number of words to be read or written, communicated via the data lines and stored in the data count register
The processor then continues with other work, it delegates the I/O operation to the DMA module which transfers the entire block of data, one word at a time, directly to or from memory without going through the processor. When the transfer is complete, the DMA module sends an interrupt signal to the processor, this the processor is involved only at the beginning and end of the transfer.

I/O Channels and Processors
Characteristics of I/O Channels

As one proceeds along the evolutionary path, more and more of the I/O function is performed without CPU involvement.

The I/O channel represents an extension of the DMA concept. An I/O channel ahs the ability to execute I/O instructions, which gives it complete control over I/O operations. In a computer system with such devices, the CPU does not execute I/O instructions – such instructions are stored in main memory to be executed by a special purpose processor in the I/O channel itself.

Two types of I/O channels are common

A selector channel controls multiple high-speed devices.
A multiplexor channel can handle I/O with multiple characters as fast as possible to multiple devices.
The external interface: FireWire and InfiniBand
Types of Interfaces

One major characteristic of the interface is whether it is serial or parallel

parallel interface – there are multiple lines connecting the I/O module and the peripheral, and multiple bits are transferred simultaneously
serial interface – there is only one line used to transmit data, and bits must be transmitted one at a time
With new generation serial interfaces, parallel interfaces are becoming less common.

In either case, the I/O module must engage in a dialogue with the peripheral. In general terms the dialog may look as follows…

The I/O module sends a control signal requesting permission to send data
The peripheral acknowledges the request
The I/O module transfers data
The peripheral acknowledges receipt of data
For a detailed explanation of FireWire and InfiniBand technology read page 264 – 270 of the textbook