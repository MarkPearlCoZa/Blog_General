---
layout: post
title: Understanding Coupling and Cohesion in Software Design
tags: Code 
category: Misc
---

## What is coupling?

The concept of coupling is often confused with the concept of use. Just because one segment of code "uses" another segment of code does not mean that these two segments are 'coupled'.

> The two segments are only coupled if a change to one segment implies a change to another segment. 

Coupling is important because the costs of changing software are dominated by rippling changes -which means one section of code is coupled to another section.

Exponetially rippling changes kills you in software design. 

Reducing coupling takes effort - the more you try to reduce coupling, the more expensive it gets. There is a trade off curve between effort and coupling.

## What is cohesion?

#### References

- [Software Design - Why, When & How by Kent Beck](http://blog.markpearl.co.za/Software-Design-Why-When-How)  
