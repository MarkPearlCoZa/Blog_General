---
layout: post
title: SSL Certificate Notes
tags: Web
category: Tech
---
#### Different types of classes ####

- Class 1 for individuals, intended for email.  
- Class 2 for organizations, for which proof of identity is required.  
- Class 3 for servers and software signing, for which independent verification and checking of identity and authority is done by the issuing certificate authority.  
- Class 4 for online business transactions between companies.  
- Class 5 for private organizations or governmental security.  

--------------------------------------------------------------------------------------------------

#### Commentary on Classes ####

Vendor defined classes

VeriSign uses the concept of classes for different types of digital certificates [3]:  

- Class 1 for individuals, intended for email. 
- Class 2 for organizations, for which proof of identity is required.  
- Class 3 for servers and software signing, for which independent verification and checking of identity and authority is done by the issuing certificate authority.  
- Class 4 for online business transactions between companies.  
- Class 5 for private organizations or governmental security.  

Other vendors may choose to use different classes or no classes at all as this is not specified in the SSL protocol, though, most do opt to use classes in some form.  

This is new(ish). They used to actually verify all requests to make sure you were who you said you were. This has gone by the wayside so you can get a cert in a few minutes instead of a few days.

[See original post](http://serverfault.com/questions/365846/ssl-certificate-class-2-vs-class-3-vs-class-4)  

#### Wildcard Certificates ####

If a wildcard certificate is compromised anywhere on any of the services you use, the information on all your services is at risk. You also have to replace the certificate everywhere it's used.

[Read More](https://en.wikipedia.org/wiki/Wildcard_certificate)  

#### SHA-2 vs SHA-1 ####

[Read More](https://support.dnsimple.com/articles/sha-2-ssl-certificates/#sha-2-ssl-certificate-compatibility)  

--------------------------------------------------------------------------------------------------

#### Setting up your browser with ssl for authentication ####

With StartCom you will have a P12 File.

To import the file as a certificate into Google Chrome, do the following:  

Chrome > Settings > Advanced > HTTPS / TLS > Manage Certificates > Personal  

Import the certificate  

Clean cookies in the browser and restart it

Certificate should take effect  
