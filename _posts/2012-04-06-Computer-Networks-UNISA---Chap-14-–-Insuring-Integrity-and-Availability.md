---
layout: post
title: Computer Networks UNISA - Chap 14 – Insuring Integrity and Availability
tags: 
category: University
---
After reading this section you should be able to
Identify the characteristics of a network that keep data safe from loss or damage
Protect an enterprise-wide network from viruses
Explain network and system level fault tolerance techniques
Discuss issues related to network backup and recovery strategies
Describe the components of a useful disaster recovery plan and the options for disaster contingencies
What are integrity and availability?
Integrity – the soundness of a networks programs, data, services, devices, and connections
Availability – How consistently and reliably a file or system can be accessed by authorized personnel
A number of phenomena can compromise both integrity and availability including…

security breaches
natural disasters
malicious intruders
power flaws
human error
users
etc
Although you cannot predict every type of vulnerability, you can take measures to guard against the most damaging events. The following are some guidelines…

Allow only network administrators to create or modify NOS and application system users.
Monitor the network for unauthorized access or changes
Record authorized system changes in a change management system’
Install redundant components
Perform regular health checks on the network
Check system performance, error logs, and the system log book regularly
Keep backups
Implement and enforce security and disaster recovery policies
These are just some of the basics…

Malware
Malware refers to any program or piece of code designed to intrude upon or harm a system or its resources.

Types of Malware…

Boot sector viruses
Macro viruses
File infector viruses
Worms
Trojan Horse
Network Viruses – propagate themselves via network protocols, commands, messaging programs and data links
Bots
Malware characteristics

Some common characteristics of Malware include…

Encryption
Stealth
Polymorphism
Time dependence
Malware Protection

There are various tools available to protect you from malware called anti-malware software. These monitor your system for indications that a program is performing potential malware operations. A number of techniques are used to detect malware including…

Signature Scanning
Integrity Checking
Monitoring unexpected file changes or virus like behaviours
It is important to decide where anti-malware tools will be installed and find a balance between performance and protection. There are several general purpose malware policies that can be implemented to protect your network including…

Every compute in an organization should be equipped with malware detection and cleaning software that regularly runs
Users should not be allowed to alter or disable the anti-malware software
Users should know what to do in case the anti-malware program detects a malware virus
Users should be prohibited from installing any unauthorized software on their systems
System wide alerts should be issued to network users notifying them if a serious malware virus has been detected.
Fault Tolerance
Besides guarding against malware, another key factor in maintaining the availability and integrity of data is fault tolerance. Fault tolerance is the ability for a system to continue performing despite an unexpected hardware or software malfunction.

Fault tolerance can be realized in varying degrees, the optimal level of fault tolerance for a system depends on how critical its services and files are to productivity. Generally the more fault tolerant the system, the more expensive it is.

The following describe some of the areas that need to be considered for fault tolerance.

Environment (Temperature and humidity)
Power
Topology and Connectivity
Servers
Storage
Power

Typical power flaws include

Surges – a brief increase in voltage due to lightening strikes, solar flares or some idiot at City Power
Noise – Fluctuation in voltage levels caused by other devices on the network or electromagnetic interference
Brownout – A sag in voltage for just a moment
Blackout – A complete power loss
The are various alternate power sources to consider including UPS’s and Generators.

UPS’s are found in two categories…

Standby UPS – provides continuous power when mains goes down (brief period of switching over)
Online UPS – is online all the time and the device receives power from the UPS all the time (the UPS is charged continuously)
Servers

There are various techniques for fault tolerance with servers.

Server mirroring is an option where one device or component duplicates the activities of another. It is generally an expensive process.
Clustering is a fault tolerance technique that links multiple servers together to appear as a single server. They share processing and storage responsibilities and if one unit in the cluster goes down, another unit can be brought in to replace it.
Storage

There are various techniques available including the following…

RAID Arrays
NAS (Storage (Network Attached Storage)
SANs (Storage Area Networks)
Data Backup
A backup is a copy of data or program files created for archiving or safekeeping. Many different options for backups exist with various media including… These vary in cost and speed.

Optical Media
Tape Backup
External Disk Drives
Network Backups
Backup Strategy

After selecting the appropriate tool for performing your servers backup, devise a backup strategy to guide you through performing reliable backups that provide maximum data protection. Questions that should be answered include…

What data must be backed up
At what time of day or night will the backups occur
How will you verify the accuracy of the backups
Where and for how long will backup media be stored
Who will take responsibility for ensuring that backups occurred
How long will you save backups
Where will backup and recovery documentation be stored
Different backup methods provide varying levels of certainty and corresponding labour cost. There are also different ways to determine which files should be backed up including…

Full backup – all data on all servers is copied to storage media
Incremental backup – Only data that has changed since the last full or incremental backup is copied to a storage medium
Differential backup – Only data that has changed since the last backup is coped to a storage medium
Disaster Recovery
Disaster recovery is the process of restoring your critical functionality and data after an enterprise wide outage has occurred.

A disaster recovery plan is for extreme scenarios (i.e. fire, line fault, etc).

A cold site is a place were the computers, devices, and connectivity necessary to rebuild a network exist but they are not appropriately configured.
A warm site is a place where the computers, devices, and connectivity necessary to rebuild a network exists with some appropriately configured devices.
A hot site is a place where the computers, devices, and connectivity necessary to rebuild a network exists and all are appropriately configured.