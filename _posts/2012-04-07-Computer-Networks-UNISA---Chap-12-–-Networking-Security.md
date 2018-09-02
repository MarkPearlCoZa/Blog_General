---
layout: post
title: Computer Networks UNISA - Chap 12 – Networking Security
tags: 
category: University
---
After reading this section you should be able to
Identify security risks in LANs and WANs and design security policies that minimize risks
Explain how physical security contributes to network security
Discuss hardware and design based security techniques
Understand methods of encryption such as SSL and IPSec, that can secure data in storage and in transit
Describe how popular authentication protocols such as RADIUS< TACACS,Kerberos, PAP, CHAP, and MS-CHAP function
Use network operating system techniques to provide basic security
Understand wireless security protocols such as WEP, WPA and 802.11i
Security Audits
Before spending time and money on network security, examine your networks security risks – rate and prioritize risks. Different organizations have different levels of network security requirements.

Security Risks
Not all security breaches result from a manipulation of network technology – there are human factors that can play a role as well. The following categories are areas of considerations…

Risks associated with People
Risks associated with Transmission and Hardware
Risks associated with Protocols and Software
Risks associated with Internet Access
Risks associated with People

Intruders or attackers using social engineering or snooping to obtain user passwords
An administrator incorrectly creating or configuring user ID’s, groups, and their associated rights on a file server
Network administrators overlooking security flaws in topology or hardware configuration
Network administrators overlooking security flaws in the operating system or application configuration
Lack of proper documentation and communication of security policies
Dishonest or disgruntled employees abusing their file and access rights
An unused computer or terminal being left logged on to the network
Users or administrators choosing easy to guess passwords
Authorized staff leaving computer room doors open or unlocked
Staff discarding disks or backup tapes in public waste containers
Administrators neglecting to remove access and file rights for employees who have left the organization
Users writing their passwords on paper and then loosing them
Risks associated with Protocols and Software

TCP/IP contains several security flaws (e.g. falsified IP addresses)
Trust relationships between one server and another
NOSs might contain back doors or security flaws
Administrators might accept the default security options after installing an operating or application
Transactions that take place between applications, such as databases and web based forms might allow interception
Risks associated with Transmission and Hardware

Network hubs broadcast traffic over the entire segment, thus making transmission more widely vulnerable to sniffing
Unused hub, switch, router, or server ports can be exploited and accessed by hackers if they are not disabled
 

An effective security policy
A security policy identifies your security goals, risks, levels of authority, designated security coordinator and team members, responsibilities for each team member, and responsibilities for each employee. In addition it specifies how to address security breaches. It should not state exactly which hardware, software, architecture, or protocols will be used to ensure security, nor how hardware or software will be installed and configured.

A security policy must address an organizations specific risks. to understand your risks, you should conduct a security audit that identifies vulnerabilities and rates both the severity of each threat and its likelihood of occurring.

Security Policy Content

Security policy content should…

Policies for each category of security
Explain to users what they can and cannot do and how these measures protect the networks security
Should define what confidential means to the organization
Response Policy

A security policy should provide for a planned response in the event of a security breach. The response policy should identify the members of a response team, all of whom should clearly understand the the security policy, risks, and measures in place.

Some of the roles concerned could include…

Dispatcher – the person on call who first notices the breach
Manager – the person who coordinates the resources necessary to solve the problem
Technical Support Specialist – the person who focuses on solving the problem
Public relations specialist – the person who acts as the official spokesperson for the organization
Physical Security
An important element in network security is restricting physical access to its components. There are various techniques for this including locking doors, security people at access points etc. You should identify the following…

Which rooms contain critical systems or data and must be secured
Through what means might intruders gain access to these rooms
How and to what extent are authorized personnel granted access to these rooms
Are authentication methods such as ID cards easy to forge
etc.
A more expensive solution involves bio-recognition access, in which a device scans an individuals unique physical characteristics such as the colour patterns in her iris, or the geometry of the hand

Security in Network Design
The optimal way to prevent external security breaches from affecting you LAN is not to connect your LAN to the outside world at all. The next best protection is to restrict access at every point where your LAN connects to the rest of the world.

Router Access List – can be used to filter or decline access to a portion of a network for certain devices.

Intrusion Detection and Prevention

While denying someone access to a section of the network is good, it is better to be able to detect when an attempt has been made and notify security personnel. This can be done using IDS (intrusion detection system) software.

One drawback of IDS software is it can detect false positives – i.e. an authorized person who has forgotten his password attempts to logon.

Firewalls

A firewall is a specialized device, or a computer installed with specialized software, that selectively filters or blocks traffic between networks. A firewall typically involves a combination of hardware and software and may reside between two interconnected private networks.

The simplest form of a firewall is a packet filtering firewall, which is a router that examines the header of every packet of data it receives to determine whether that type of packet is authorized to continue to its destination or not.

Firewalls can block traffic in and out of a LAN.

NOS (Network Operating System) Security
Regardless of the operating system, generally every network administrator can implement basic security by restricting what users are authorized to do on a network. Some of the restrictions include things related to

Logons – place, time of day, total time logged in, etc.
Passwords – length, characters used, etc.
An example of a dictionary attack is when hackers use a software program that try a combination of your user ID and every word in a dictionary to gain access to the network.

Encryption
Encryption is the use of an algorithm to scramble data into a format that can be read only by reversing the algorithm. The purpose of encryption is to keep information private. Many forms of encryption exist and new ways of cracking encryption are continually being invented.

Private Key Encryption

In private key encryption, data is encrypted using a single key that only the sender and the receiver know. Private key encryption is also known as symmetric encryption.

Public Key Infrastructure

The use of certificate authorities to associate public keys with certain users is known as Public Key Infrastructure.

Categories of Encryption

The following are some categories of encryption…

Key Encryption
PGP (Pretty Good Privacy)
SSL (Secure Sockets Layer)
SSH (Secure Shell)
SCP (Secure CoPy)
SFTP (Secure File Transfer Protocol)
IPSec (Internet Protocol Security)
For a detailed explanation on each section refer to pages 596 to 604 of textbook

Authentication Protocols
Authentication protocols are the rules that computers follow to accomplish authentication. Several types exist and the following are some of the common authentication protocols…

RADIUS and TACACS belong to a category of protocols known as AAA (Authentication, authorization and accounting)

RADIUS and TACACS
PAP (Password Authentication Protocol)
CHAP and MS-CHAP
EAP (Extensible Authentication Protocol)
802.1x (EAPoL)
Kerberos
With Kerberos, to authenticate a client, the KDC runs an authentication service which issues a ticket, which is a temporary set of credentials that a client uses to prove that its identiy has been validated (note a ticket is not the same as a key)

Wireless Network Security
Wireless transmissions are particularly susceptible to eavesdropping. The following are two wireless network security protocols

WEP – requires on to enter a network key to gain access to the network
WPA