---
layout: post
title: Stored Procedures
tags: Useful
category: Tech
---

####  General Notes ####

Stored proceudres can offer huge performance advantages for huge architectural costs. You may avoid streaming thousands of rows to a client application, but you have also bound your application code to this database. The decision to use stored procedures should not be arrived at lightly.

The fear of stored procedures being used is mainly due to the fear of vendor lock in. Different RDMS systems offered proprietry offerings which if utilized would bind the system to that particular platform. When looking at where logic should be stored, be cognisent of what lockin you are incurring.

#### References ####
[It's time to get over that stored procedure aversion you have](http://rob.conery.io/2015/02/21/its-time-to-get-over-that-stored-procedure-aversion-you-have/)  
