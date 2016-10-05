---
layout: post
title: Understanding Coupling and Cohesion in Software Design
tags: Code 
category: Misc
---

In software design, most conversations regarding design have a foundation based on coupling and cohesion. Having a deep understanding of what coupling and cohesion mean can be key to effective conversatins regarding software design.

## What is coupling?

The concept of coupling is often confused with the concept of use. Just because one segment of code "uses" another segment of code does not mean that these two segments are 'coupled'.

> The two segments are only coupled if a change to one segment implies a change to another segment. 

Coupling is important because the costs of changing software are dominated by rippling changes -which means one section of code is coupled to another section.

Exponetially rippling changes kills you in software design. 

Reducing coupling takes effort - the more you try to reduce coupling, the more expensive it gets. 

## What is cohesion?

Cohesion is a little more abstract than coupling. 

We refer to a sound line of reasoning as coherent - the thoughts fit, they go together, they relate to each other. The reasoning is highly cohesive.

This is exactly the characteristic of a segment of code that makes it coherent: the pieces all seem to be related, they seem to belong together.

Another way to understand cohesion is to understand it's opposite - adhesion. 

Adhesives are used to 'glue' two things together that are not meant to be together. 

An example of an adhesive segment of code would be one where things are stuck together that don't seem to belong together. 


#### References

- [Software Design - Why, When & How by Kent Beck](http://blog.markpearl.co.za/Software-Design-Why-When-How)  
- [SOLID Deconstruction by Kevlin Henney](http://blog.markpearl.co.za/SOLID-Deconstruction)  
