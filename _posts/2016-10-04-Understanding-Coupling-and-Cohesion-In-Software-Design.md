---
layout: post
title: Understanding Coupling and Cohesion in Software Design
tags: Code 
category: Misc
---

In software design, most conversations regarding design have a foundation based on the concepts of coupling and cohesion. Having a deep understanding of what coupling and cohesion mean are key to having an effective conversations regarding good software design.

In my explanations below I have used the term "segment of code". For your language paradigm of choice replace this phrase with whatever construct makes the most sense to your language (class, method, module, etc.)

## What is coupling?

The concept of coupling is often confused with the concept of use. Just because one segment of code "uses" another segment of code does not mean that these two segments are 'coupled'.

> The two segments are only coupled if a change to one segment implies a change to another segment. 

Coupling is important because the costs of changing software is dominated by rippling changes. When you see rippling changes in a code, it is an indication that these segments are coupled to each other.

Exponentially rippling changes kills you in software design. 

Reducing coupling takes effort - the more you try to reduce coupling, the more expensive it gets. 

## What is cohesion?

Cohesion is a little more abstract than coupling. 

We refer to a sound line of reasoning - the thoughts fit, they relate to each other in a coherent manner, the reasoning is highly cohesive. This is exactly the characteristic of a segment of code that makes it coherent: the pieces all seem to be related, they belong together.

Another way to understand cohesion is to understand it's opposite - adhesion. 

> Think of cohesion as the opposite of being adhesive.

Adhesives are used to 'glue' two things together that are not meant to be together. 

An example of an adhesive segment of code would be one where things are stuck together that don't seem to belong together. 

#### References

- [Software Design - Why, When & How by Kent Beck](http://blog.markpearl.co.za/Software-Design-Why-When-How)  
- [SOLID Deconstruction by Kevlin Henney](http://blog.markpearl.co.za/SOLID-Deconstruction)  
