---
layout: post
title: Software Design - Why, When & How Notes
tags: Design
category: Misc
---

These notes are based on Kent Beck's talk on "[Software Design: Why, When & How](https://vimeo.com/105771493)" done at JavaZone in September 2014.

The **What** of Software Design is well established.We have a pretty good idea of "what" good software is.

For instance, we have design patterns which have been around for well over a decade. 

Somehow in focussing so long, so effectively on what, we have forgotten to talk about the why.

When do you know when code should be tidied up?  
When do you apply a specific pattern or approach? 
Why would you apply that approach?  

Without talking about why we do software design, we don't have an opportunity to be able to apply the right "what".

## When does design matter? ##

Software as its sits doesn't care how it is designed - it just runs. 
Software design is not software. Software design is about change - it is only when we want to change software does design play a role.

## Why ##

The first driver for software design is economics. We get paid to write programs. When we write programs, somebody expects to make money somehow, sometime.  

Economics has a good vocabulary for talking about timing.
There are two topics in economics we should consider.

1. Net Present Value  
2. Options Value of Software  

### Net Present Value ###

The first economic topic is NPV (Net Present Value). In essence, NPV says a dollar today is worth more than a dolar tomorrow. This means we should earn money sooner and spend money later, all other things being equal.

Doing all design upfront flies in the face of NPV. When doing all design upfront, we are spending all the money today, and only earning it later.

### Options Value of Software ###


