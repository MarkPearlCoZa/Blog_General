---
layout: post
title: Rest Notes
tags: Web
category: Tech
---

REST stands for REpresentational State Transer. It is currently the de facto architecture of web applications. It is a guideline for mapping resources to URLs and interacting with them using CRUD verbs (Post, Get, Put and Delete).

# Anemic REST Antipattern

Failure to properly model the domain as a set of resources, naively developing services that simply expose static, hierarchical data models via templated URL's.

[Read Thoughtworks Info on Antipattern](https://www.thoughtworks.com/radar/techniques/anemic-rest)  

# Rest & Long Running Jobs

Return a 202 Accepted Response

[Rest and long running jobs](http://farazdagi.com/blog/2014/rest-long-running-jobs/)  
