---
layout: post
title: SSL Certificate Notes
tags: SSL
category: Tech
---
#### Different types of classes ####

Class 1 for individuals, intended for email.  

Class 2 for organizations, for which proof of identity is required.  

Class 3 for servers and software signing, for which independent verification and checking of identity and authority is done by the issuing certificate authority.  

Class 4 for online business transactions between companies.  

Class 5 for private organizations or governmental security.  

#### Commentary on Classes ####

Vendor defined classes

VeriSign uses the concept of classes for different types of digital certificates [3]:  

Class 1 for individuals, intended for email.  
Class 2 for organizations, for which proof of identity is required.  
Class 3 for servers and software signing, for which independent verification and checking of identity and authority is done by the issuing certificate authority.  
Class 4 for online business transactions between companies.  
Class 5 for private organizations or governmental security.  
Other vendors may choose to use different classes or no classes at all as this is not specified in the SSL protocol, though, most do opt to use classes in some form.  

This is new(ish). They used to actually verify all requests to make sure you were who you said you were. This has gone by the wayside so you can get a cert in a few minutes instead of a few days.

[See original post](http://serverfault.com/questions/365846/ssl-certificate-class-2-vs-class-3-vs-class-4)  
