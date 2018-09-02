---
layout: post
title: Organization and Architecture UNISA Studies – Chap 6
tags: 
category: University
---
Learning Outcomes
Discuss the physical characteristics of magnetic disks
Describe how data is organized and accessed on a magnetic disk
Discuss the parameters that play a role in the performance of magnetic disks
Describe different optical memory devices
Magnetic Disk
The way data is stored on and retried from magnetic disks

Data is recorded on and later retrieved form the disk via a conducting coil named the head (in many systems there are two heads)
The writ mechanism exploits the fact that electricity flowing through a coil produces a magnetic field. Electric pulses are sent to the write head, and the resulting magnetic patterns are recorded on the surface below with different patterns for positive and negative currents
The physical characteristics of a magnetic disk

 

Summarize from book

 

The factors that play a role in the performance of a disk

Seek time – the time it takes to position the head at the track
Rotational delay / latency – the time it takes for the beginning of the sector to reach the head
Access time – the sum of the seek time and rotational delay
Transfer time – the time it takes to transfer data
RAID
The rate of improvement in secondary storage performance has been considerably less than the rate for processors and main memory. Thus secondary storage has become a bit of a bottleneck. RAID works on the concept that if one disk can be pushed so far, additional gains in performance are to be had by using multiple parallel components.

Points to note about RAID…

RAID is a set of physical disk drives viewed by the operating system as a single logical drive
Data is distributed across the physical drives of an array in a scheme known as striping
Redundant disk capacity is used to store parity information, which guarantees data recoverability in case of a disk failure (not supported by RAID 0 or RAID 1)
Interesting to note that the increase in the number of drives, increases the probability of failure. To compensate for this decreased reliability RAID makes use of stored parity information that enables the recovery of data lost due to a disk failure.

 

The RAID scheme consists of 7 levels…

 

Category	Level	Description	Disks Required	Data Availability	Large I/O Data Transfer Capacity	Small I/O Request Rate
Striping	0	Non Redundant	N	Lower than single disk	Very high	Very high for both read and write
Mirroring	1	Mirrored	2N	Higher than RAID 2 – 5 but lower than RAID 6	Higher than single disk	Up to twice that of a signle disk for read
Parallel Access	2	Redundant via Hamming Code	N + m	Much higher than single disk	Highest of all listed alternatives	Approximately twice that of a single disk
Parallel Access	3	Bit interleaved parity	N + 1	Much higher than single disk	Highest of all listed alternatives	Approximately twice that of a single disk
Independent Access	4	Block interleaved parity	N + 1	Much higher than single disk	Similar to RAID 0 for read, significantly lower than single disk for write	Similar to RAID 0 for read, significantly lower than single disk for write
Independent Access	5	Block interleaved parity	N + 1	Much higher than single disk	Similar to RAID 0 for read, lower than single disk for write	Similar to RAID 0 for read, generally  lower than single disk for write
Independent Access	6	Block interleaved parity	N + 2	Highest of all listed alternatives	Similar to RAID 0 for read; lower than RAID 5 for write	Similar to RAID 0 for read, significantly lower than RAID 5  for write
 

Read page 215 – 221 for detailed explanation on RAID levels

Optical Memory
There are a variety of optical-disk systems available.

Read through the table on page 222 – 223

Some of the devices include…

CD
CD-ROM
CD-R
CD-RW
DVD
DVD-R
DVD-RW
Blue-Ray DVD
Magnetic Tape
Most modern systems use serial recording – data is lade out as a sequence of bits along each track. The typical recording used in serial is referred to as serpentine recording. In this technique when data is being recorded, the first set of bits is recorded along the whole length of the tape. When the end of the tape is reached the heads are repostioned to record a new track, and the tape is again recorded on its whole length, this time in the opposite direction. That process continued back and forth until the tape is full. To increase speed, the read-write head is capable of reading and writing a number of adjacent tracks simultaneously. Data is still recorded serially along individual tracks, but blocks in sequence are stored on adjacent tracks as suggested.

A tape drive is a sequential access device.

Magnetic tape was the first kind of secondary memory. It is still widely used as the lowest-cost, slowest speed member of the memory hierarchy.