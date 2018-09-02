---
layout: post
title: Computer Networks UNISA - Chap 15 – Network Management
tags: 
category: University
---
After reading this section you should be able to
Understand network management and the importance of documentation, baseline measurements, policies, and regulations to assess and maintain a network’s health.
Manage a network’s performance using SNMP-based network management software, system and event logs, and traffic-shaping techniques
Identify the reasons for and elements of an asset managements system
Plan and follow regular hardware and software maintenance routines
Fundamentals of Network Management
Network management refers to the assessment, monitoring, and maintenance of all aspects of a network including checking for hardware faults, ensuring high QoS, maintaining records of network assets, etc.

Scope of network management differs depending on the size and requirements of the network.

All sub topics of network management share the goals of enhancing the efficiency and performance while preventing costly downtime or loss.

Documentation

The way documentation is stored may vary, but to adequately manage a network one should at least record the following…

Physical topology (types of LAN and WAN topologies – ring, star, hybrid)
Access method (does it use Ethernet 802.3, token ring, etc.)
Protocols
Devices (Switches, routers, etc)
Operating Systems
Applications
Configurations (What version of operating system and config files for serve / client software)
Baseline Measurements

A baseline is a report of the network’s current state of operation. Baseline measurements might include the utilization rate for your network backbone, number of users logged on per day, etc.

Baseline measurements allow you to compare future performance increases or decreases caused by network changes or events with past network performance. Obtaining baseline measurements is the only way to know for certain whether a pattern of usage has changed, or whether a network upgrade has made a difference.

There are various tools available for measuring baseline performance on a network.

Policies, Procedures, and Regulations

Following rules helps limit chaos, confusion, and possibly downtime. The following policies and procedures and regulations make for sound network management.

Media installations and management (includes designing physical layout of cable, etc.)
Network addressing policies (includes choosing and applying a an addressing scheme)
Resource sharing and naming conventions (includes rules for logon ID’s)
Security related policies
Troubleshooting procedures
Backup and disaster recovery procedures
In addition to internal policies, a network manager must consider external regulatory rules.

Fault and Performance Management
After documenting every aspect of your network and following policies and best practices, you are ready to asses you networks status on an on going basis. This process includes both performance management and fault management.

Network Management Software

To accomplish both fault and performance management, organizations often use enterprise-wide network management software. There various software packages that do this, each collect data from multiple networked devices at regular intervals, in a process called polling. Each managed device runs a network management agent. So as not to affect the performance of a device while collecting information, agents do not demand significant processing resources.

The definition of a managed devices and their data are collected in a MIB (Management Information Base).

Agents communicate information about managed devices via any of several application layer protocols. On modern networks most agents use SNMP which is part of the TCP/IP suite and typically runs over UDP on port 161.

Because of the flexibility and sophisticated network management applications are a challenge to configure and fine-tune. One needs to be careful to only collect relevant information and not cause performance issues (i.e. pinging a device every 5 seconds can be a problem with thousands of devices).

MRTG (Multi Router Traffic Grapher) is a simple command line utility that uses SNMP to poll devices and collects data in a log file. MRTG can be used with Windows, UNIX and Linux.

System and Event Logs

Virtually every condition recognized by an operating system can be recorded. This is typically done using event logs. In Windows there is a GUI event log viewer. Similar information is recorded in UNIX and Linux in a system log.

Much of the information collected in event logs and syslog files does not point to a problem, even if it is marked with a warning so it is important to filter your logs appropriately to reduce the noise.

Traffic Shaping

When a network must handle high volumes of network traffic, users benefit from performance management technique called traffic shaping. Traffic shaping involves manipulating certain characteristics of packets, data streams, or connections to manage the type and amount of traffic traversing a network or interface at any moment. Its goals are to assure timely delivery of the most important traffic while offering the best possible performance for all users.

Several types of traffic prioritization exist including prioritizing traffic according to any of the following characteristics…

Protocol
IP address
User group
DiffServr
VLAN tag in a Data Link layer frame
Service or application
Caching

In addition to traffic shaping, a network or host might use caching to improve performance. Caching is the local storage of frequently needed files that would otherwise be obtained from an external source. By keeping files close to the requester, caching allows the user to access those files quickly.

The most common type of caching is Web caching, in which Web pages are stored locally. To an ISP, caching is much more than just convenience. It prevents a significant volume of WAN traffic, thus improving performance and saving money.

Asset Management
Another key component in managing networks is identifying and tracking its hardware. This is called asset management.

The first step to asset management is to take an inventory of each node on the network. You will also want to keep records of every piece of software purchased by your organization.

Asset management simplifies maintaining and upgrading the network chiefly because you know what the system includes. In addition, asset management provides network administrators with information about the costs and benefits of certain types of hardware or software.

Change Management
Networks are always in a stage of flux with various aspects including…

Software changes and patches
Client Upgrades
Shared Application Upgrades
NOS Upgrades
Hardware and Physical Plant Changes
Cabling Upgrades
Backbone Upgrades
For a detailed explanation on each of these read the textbook (Page 750 – 761)