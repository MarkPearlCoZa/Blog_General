---
layout: post
title: "SOLID Deconstruction"
description: ""
tags: Code
category: Media
---

These notes are based on [Kevlin Henney](https://twitter.com/KevlinHenney) talk on "[SOLID Deconstruction](https://vimeo.com/157708450)" done at NDC London 2016.

#### General

SOLID Principles are not quite right...
- Two ideas rolled into one  
- One is subordinate to the other  
- One is not even a practice at all  

### Are these principles?

Dictionary definitions of principle
- A fundamental truth   
- Foundation for a system of belief 
- Morally correct behavior or attitude 
- General scientific theorem or law  

A more suitable word is **pattern** - a pattern is a context specific piece of advice.

Advice is contextually good, but change the context and the advice could be bad.

Dictionary definition of pattern  
- A regular form or sequence discernible in the way in which something happens or is done  
- An example for others to follow  

> It turns out words matter, in software we use a bunch of words but we are fairly rubbish in using them.

### Single Responsibility  

Robert C Martin described this concept being based on the principle of cohesion, as described by Tom Demarco in his book **Structured Analysis and System Specification**.  

Tom Demarco had a few things to say on cohesion. 

- Cohesion is a measure of the strength of association of the elements inside a module. 
- A highly cohesive module is a collection of statements and data items that should be treated as a whole because they are so closely related.

Robert C Martin said SINGLE RESPONSIBILITY - Tom Demarco never mentioned a specific number.

#### Cohesion 

Cohesion is one of the things that people struggle with. It is a little more abstract and intellectual.

We refer to a sound line of reasoning as coherent. The thoughts fit, they go together, they relate to each other. This is exactly the characteristic of a class that makes it coherent: the pieces all seem to be related, they seem to belong together.


#### References

[Video of talk](https://vimeo.com/157708450)  
