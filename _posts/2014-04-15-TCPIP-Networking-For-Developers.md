---
layout: post
title: TCP/IP Networking for Developers
tags: Useful
category: Tech
---
Great [pluralsight course on networking for developers](http://pluralsight.com/training/courses/TableOfContents?courseName=tcp-ip-networking-for-devs). I always forget this stuff.

## Concepts ##

### DHCP ###

DHCP forms the basis of the functionality that allows your machine to automatically get and ip address and subnet mask.

DHCP stands for Dynamic Host Configuration Protocol.  

DHCP has different messages that it can send, these include:
- DHCPDISCOVER  
- DHCPOFFER  
- DHCPREQUEST  
- DHCPACK  
- DHCPNAK  
- DHCPDECLINE  
- DHCPINFORM  
- DHCPRELEASE  

### DNS Nameservers ###

Domain Name System (DNS) is a hierarchical distributed naming system for computers, services, or any resource connected to the Internet or a private network.

It is the service that when you ping www.google.com translates that address into an ip address.  

### Subnets ###

#### Host Files ####

You can overwrite dns by customizing your host file.

The host file is located at...

>  
> C:\Windows\System32\drivers\etc  
>  

Changing the host file will clear the local cache and cause it to be repopulated with the settings in the host file.

[What is DHCP and how it works](http://www.thegeekstuff.com/2013/03/dhcp-basics/)

-------------------------------------------------------------------------------------------------

## Tools ##

### ping ###

-------------------------------------------------------------------------------------------------

### ipconfig ###

Display all the cached records on your local machine including the time till that cached record expires.  

>
> ipconfig /displaydns
>

-------------------------------------------------------------------------------------------------

### dig ###

Short for Domain Information Groper, dig is a network administration tool for querying DNS name servers.  

- Powerful  
- Lots of functions  

Simple query 

> dig markpearl.co.za  

Querying a specific name server

> dig @ns1.dnsimple.com markpearl.co.za

Tracing to make iterative queries  

> dig +trace markpearl.co.za  

[see more about dig](https://newsletter.dnsimple.com/how-to-dig/)  

-------------------------------------------------------------------------------------------------

### host ### 

host is used for converting domain names to ip addresses and the other way around. 

- Simple & quick  
- Doesn't have a lot of functions  

> host markpearl.co.za  

-------------------------------------------------------------------------------------------------

### nslookup ###

Allows you to get dns responses from the command line.

- One of the oldest tools for DNS lookup  
- Does not use the local resolver provided by the OS, uses its own internal resolver to make DNS queries  
- Sometimes produces confusing or inconsistent results  

>  
> e.g. nslookup markpearl.co.za  
> returns 192.168.0.1  
>  

You can compare dns server responses using this tool.
You can specify a specific dns server to query by doing the following:

>  
> nslookup  
> server xxx.xxx.xxx.xxx  
>  
  
Going forward any nslookup queries will be done against the dns server at ip address xxx.xxx.xxx.xxx

nslookup by default returns a-record types, this can be changed by...

>  
> nslookup  
> set type=NS  
>  

There are different types inclusing MX, NS, CNAME, AAAA, etc 




