---
layout: post
title: Understanding Coupling and Cohesion in Software Design
tags: Code 
category: Misc
---

In software most conversations regarding design have a foundation based on the concepts of coupling and cohesion. Having a deep understanding of what coupling and cohesion mean are key to having better conversations on design.

Recently I heard two great talk's that made mention of the concepts of coupling and cohesion that I would recommend everyone watch. 

The first talk was by [Kent Beck on Software Design](http://blog.markpearl.co.za/Software-Design-Why-When-How) in 2014 where he briefly explains how he understands the concept of coupling. 

The second talk was done by [Kevlin Henney on the topic of SOLID Deconstruction](http://blog.markpearl.co.za/SOLID-Deconstruction) in 2016 where Kevlin elaborates on the concept of cohesion.

In putting Kent's and Kevlin's explanations together I have used the term "segment of code". For your language paradigm of choice (Object Oriented, Functional, etc.) replace this phrase with whatever construct makes the most sense to you (class, method, module, etc.)

## What is coupling?

The concept of coupling is often confused with the concept of use. Just because one segment of code "uses" another segment of code does not mean that these two segments are "coupled".

> Two segments are only coupled if a change to one segment implies a change to another segment. 

Coupling is important because the costs of changing software are dominated by rippling changes. For highly coupled systems, a change here, requires a change somewhere else, which then causes a change in another place and so on - these are rippling changes.

Exponentially rippling changes kills you in software design. Reducing coupling takes effort - the more you try to reduce coupling, the more expensive it gets. 

## What is cohesion?

Cohesion is a little more abstract than coupling. 

We say something has a sound line of reasoning when the thoughts fit and everything said relates to each other in a coherent manner. Another way to describe this is to say that the reasoning is highly cohesive. This is exactly the characteristic of a segment of code that makes it have high cohesion: the pieces all seem to be related, they belong together.

> The pieces all seem to be related, they belong together.

Another way to understand cohesion is to understand it's opposite - adhesion. Adhesives are used to 'glue' two things together that are not meant to be together. An example of an adhesive segment of code would be one where things are stuck together that don't seem to belong together. 

#### References

- [Software Design - Why, When & How by Kent Beck](http://blog.markpearl.co.za/Software-Design-Why-When-How)  
- [SOLID Deconstruction by Kevlin Henney](http://blog.markpearl.co.za/SOLID-Deconstruction)  
