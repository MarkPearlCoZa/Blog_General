---
layout: post
title: Organization and Architecture UNISA Studies – Chap 4
tags: 
category: University
---
Learning Outcomes
Explain the characteristics of memory systems
Describe the memory hierarchy
Discuss cache memory principles
Discuss issues relevant to cache design
Describe the cache organization of the Pentium
Computer Memory Systems
There are key characteristics of memory…

Location – internal or external
Capacity – expressed in terms of bytes
Unit of Transfer – the number of bits read out of or written into memory at a time
Access Method – sequential, direct, random or associative
From a users perspective the two most important characteristics of memory are…

Capacity
Performance – access time, memory cycle time, transfer rate
The trade off for memory happens along three axis…

Faster access time, greater cost per bit
Greater capacity, smaller cost per bit
Greater capacity, slower access time
This leads to people using a tiered approach in their use of memory

memory_hierarchy

 

As one goes down the hierarchy, the following occurs…

Decreasing cost per bit
Increasing capacity
Increasing access time
Decreasing frequency of access of the memory by the processor
The use of two levels of memory to reduce average access time works in principle, but only if conditions 1 to 4 apply. A variety of technologies exist that allow us to accomplish this. Thus it is possible to organize data across the hierarchy such that the percentage of accesses to each successively lower level is substantially less than that of the level above.

A portion of main memory can be used as a buffer to hold data temporarily that is to be read out to disk. This is sometimes referred to as a disk cache and improves performance in two ways…

Disk writes are clustered. Instead of many small transfers of data, we have a few large transfers of data. This improves disk performance and minimizes processor involvement.
Some data designed for write-out may be referenced by a program before the next dump to disk. In that case the data is retrieved rapidly from the software cache rather than slowly from disk.
Cache Memory Principles
Cache memory is substantially faster than main memory. A caching system works as follows..

When a processor attempts to read a word of memory, a check is made to see if this in in cache memory…
If it is, the data is supplied,
If it is not in the cache, a block of main memory, consisting of a fixed number of words is loaded to the cache.
Because of the phenomenon of locality of references, when a block of data is fetched into the cache, it is likely that there will be future references to that same memory location or to other words in the block.
Elements of Cache Design
While there are a large number of cache implementations, there are a few basic design elements that serve to classify and differentiate cache architectures…

Cache Addresses
Cache Size
Mapping Function
Replacement Algorithm
Write Policy
Line Size
Number of Caches
Cache Addresses

Almost all non-embedded processors support virtual memory. Virtual memory in essence allows a program to address memory from a logical point of view without needing to worry about the amount of physical memory available.

When virtual addresses are used the designer may choose to place the cache between the MMU (memory management unit) and the processor or between the MMU and main memory.

The disadvantage of virtual memory is that most virtual memory systems supply each application with the same virtual memory address space (each application sees virtual memory starting at memory address 0), which means the cache memory must be completely flushed with each application context switch or extra bits must be added to each line of the cache to identify which virtual address space the address refers to.

Cache Size

We would like the size of the cache to be small enough so that the overall average cost per bit is close to that of main memory alone and large enough so that the overall average access time is close to that of the cache alone.

Also, larger caches are slightly slower than smaller ones.

Mapping Function

Because there are fewer cache lines than main memory blocks, an algorithm is needed for mapping main memory blocks into cache lines. The choice of mapping function dictates how the cache is organized. Three techniques can be used…

Direct – simplest technique, maps each block of main memory into only one possible cache line
Associative – Each main memory block to be loaded into any line of the cache
Set Associative – exhibits the strengths of both the direct and associative approaches while reducing their disadvantages
For detailed explanations of each approach – read the text book (page 148 – 154)

Replacement Algorithm

For associative and set associating mapping a replacement algorithm is needed to determine which of the existing blocks in the cache must be replaced by a new block. There are four common approaches…

LRU (Least recently used)
FIFO (First in first out)
LFU (Least frequently used)
Random selection
Write Policy

When a block resident in the cache is to be replaced, there are two cases to consider

If no writes to that block have happened in the cache – discard it
If a write has occurred, a process needs to be initiated where the changes in the cache are propagated back to the main memory.
There are several approaches to achieve this including…

Write Through – all writes to the cache are done to the main memory as well at the point of the change
Write Back – when a block is replaced, all dirty bits are written back to main memory
The problem is complicated when we have multiple caches, there are techniques to accommodate for this but I have not summarized them.

Line Size

When a block of data is retrieved and placed in the cache, not only the desired word but also some number of adjacent words are retrieved. As the block size increases from very small to larger sizes, the hit ratio will at first increase because of the principle of locality, which states that the data in the vicinity of a referenced word are likely to be referenced in the near future. As the block size increases, more useful data are brought into cache. The hit ratio will begin to decrease as the block becomes even bigger and the probability of using the newly fetched information becomes less than the probability of using the newly fetched information that has to be replaced.

Two specific effects come into play…

Larger blocks reduce the number of blocks that fit into a cache. Because each block fetch overwrites older cache contents, a small number of blocks results in data being overwritten shortly after they are fetched.
As a block becomes larger, each additional word is farther from the requested word and therefore less likely to be needed in the near future.
The relationship between block size and hit ratio is complex, and no set approach is judged to be the best in all circumstances.

 

Pentium 4 and ARM cache organizations
The processor core consists of four major components:

Fetch/decode unit – fetches program instruction in order from the L2 cache, decodes these into a series of micro-operations, and stores the results in the L2 instruction cache
Out-of-order execution logic – Schedules execution of the micro-operations subject to data dependencies and resource availability – thus micro-operations may be scheduled for execution in a different order than they were fetched from the instruction stream. As time permits, this unit schedules speculative execution of micro-operations that may be required in the future
Execution units – These units execute micro-operations, fetching the required data from the L1 data cache and temporarily storing results in registers
Memory subsystem – This unit includes the L2 and L3 caches and the system bus, which is used to access main memory when the L1 and L2 caches have a cache miss and to access the system I/O resources