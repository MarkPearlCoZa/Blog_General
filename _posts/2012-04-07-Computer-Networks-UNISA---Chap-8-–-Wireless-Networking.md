---
layout: post
title: Computer Networks UNISA - Chap 8 – Wireless Networking
tags: 
category: University
---
After reading this section you should be able to
Explain how nodes exchange wireless signals
Identify potential obstacles to successful transmission and their repercussions, such as interference and reflection
Understand WLAN architecture
Specify the characteristics of popular WLAN transmission methods including 802.11 a/b/g/n
Install and configure wireless access points and their clients
Describe wireless MAN and WAN technologies, including 802.16 and satellite communications
The Wireless Spectrum
All wireless signals are carried through the air by electromagnetic waves. The wireless spectrum is a continuum of the electromagnetic waves used for data and voice communication.

The wireless spectrum falls between 9KHZ and 300 GHZ.

Characteristics of Wireless Transmission
Antennas

Each type of wireless service requires an antenna specifically designed for that service. The service’s specification determine the antenna’s power output, frequency, and radiation pattern.

A directional antenna issues wireless signals along a single direction.
An omnidirectional antenna issues and receives wireless signals with equal strength and clarity in all directions
The geographical area that an antenna or wireless system can reach is known as its range
Signal Propagation

LOS (line of sight) uses the least amount of energy and results in the reception of the clearest possible signal. When there is an obstacle in the way, the signal may… pass through the object or be obsrobed by the object or may be subject to reflection, diffraction or scattering.

Reflection – waves encounter an object and bounces off it.
Diffraction – signal splits into secondary waves when it encounters an obstruction
Scattering – is the diffusion or the reflection in multiple different directions of a signal
Signal Degradation

Fading occurs as a signal hits various objects. Because of fading, the strength of the signal that reaches the receiver is lower than the transmitted signal strength.

The further a signal moves from its source, the weaker it gets (this is called attenuation)

Signals are also affected by noise – the electromagnetic interference)

Interference can distort and weaken a wireless signal in the same way that noise distorts and weakens a wired signal.

Frequency Ranges

Older wireless devices used the 2.4 GHZ band to send and receive signals. This had 11 communication channels that are unlicensed.

Newer wireless devices can also use the 5 GHZ band which has 24 unlicensed bands

Narrowband, Broadband, and Spread Spectrum Signals

Narrowband – a transmitter concentrates the signal energy at a single frequency or in a very small range of frequencies
Broadband – uses a relatively wide band of the wireless spectrum and offers higher throughputs than narrowband technologies
The use of multiple frequencies to transmit a signal is known as spread-spectrum technology. In other words a signal never stays continuously within one frequency range during its transmission.

One specific implementation of spread spectrum is FHSS (frequency hoping spread spectrum). Another type is known as DSS (direct sequence spread spectrum)

Fixed vs. Mobile

Each type of wireless communication falls into one of two categories

Fixed – the location of the transmitted and receiver do not move (results in energy saved because weaker signal strength is possible with directional antennas)
Mobile – the location can change
WLAN (Wireless LAN) Architecture
There are two main types of arrangements

Adhoc – data is sent directly between devices – good for small local devices
Infrastructure mode – a wireless access point is placed centrally, that all devices connect with
802.11 WLANs
The most popular wireless standards used on contemporary LANs are those developed by IEEE’s 802.11 committee.

Over the years several distinct standards related to wireless networking have been released.

Four of the best known standards are also referred to as Wi-Fi. They are….

802.11b
802.11a
802.11g
802.11n
These four standards share many characteristics. i.e.

All 4 use half duplex signalling
Follow the same access method
Access Method

802.11 standards specify the use of CSMA/CA (Carrier Sense Multiple Access with Collision Avoidance) to access a shared medium. Using CSMA/CA before a station begins to send data on an 802.11 network, it checks for existing wireless transmissions. If the source node detects no transmission activity on the network, it waits a brief period of time and then sends its transmission. If the source does detect activity, it waits a brief period of time before checking again.

The destination node receives the transmission and, after verifying its accuracy, issues an acknowledgement (ACT) packet to the source. If the source receives the ACK it assumes the transmission was successful, – if it does not receive an ACK it assumes the transmission failed and sends it again.

Association

Two types of scanning…

Active – station transmits a special frame, known as a prove, on all available channels within its frequency range. When an access point finds the probe frame, it issues a probe response.
Passive – wireless station listens on all channels within its frequency range for a special signal, known as a beacon frame, issued from an access point – the beacon frame contains information necessary to connect to the point.
Re-association occurs when a mobile user moves out of one access point’s range and into the range of another.

Frames

Read page 378 – 381 about frames and specific 802.11 protocols

Bluetooth Networks
Sony Ericson originally invented the Bluetooth technology in the early 1990s. In 1998 other manufacturers joined Ericsson in the Special Interest Group (SIG) whose aim was to refine and standardize the technology.

It was designed to carry voice, video and data signals over the same communications channels
It uses FHSS (Frequency hopping spread spectrum) RF signalling in the 2.4 GHZ band'
It has been codified by the IEEE in their 802.15.1 standard
Bluetooth was designed to be used on small networks composed of personal communications devices. It has become popular wireless technology for communicating among cellular telephones, phone headsets, etc.

Implementing WLANS
For organizations it is important to perform a site survey to assess client requirements, facility characteristics, and coverage areas to determine an access point arrangement that will ensure reliable wireless connectivity within a given area.

Things included in the site survey will be…

Study building blueprints to help identify potential obstacles and clarify the distances your network needs to span on each floor
Measure signal coverage and strength from other WLANs
Testing proposed access point locations
Reveal unforeseen obstacles such as EMI issued from lights or heavy machinery
Identify optimal quantity and location of access points
Wireless WANs and Internet Access
Refer to pages 396 – 402 of the textbook for details.

802.16 (WiMAX) Internet Access

WiMAX stands for Worldwide Interoperability for Microwave Access

Satellite Internet Access

In a dial return arrangement, a subscriber receives data from the Internet via a satellite downlink transmission, but sends data to the satellite via an analogue modem.

Dial return service providers advertise downstream throughputs of 400 – 500 Kbps though in practice they may be as high as 1Mbps but upload speeds are limited to the speed of the modem, thus dial return services are asymmetrical technology.

In a satellite return arrangement, a subscriber sends and receives data to and from the Internet using a satellite uplink and downlink. This is a symmetrical technology, in which both upstream and downstream throughputs are advertised to reach 400-500 Kbps.