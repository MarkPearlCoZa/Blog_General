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

> It turns out words matter, in software we use a bunch of words but we are fairly rubbish in using them.

A more suitable word is **pattern** - a pattern is a context specific piece of advice.

Advice is contextually good, but change the context and the advice could be bad.

Dictionary definition of pattern  
- A regular form or sequence discernible in the way in which something happens or is done  
- An example for others to follow  

### Single Responsibility  

Robert C Martin described this concept being based on the principle of cohesion, as described by Tom Demarco in his book **Structured Analysis and System Specification**.  

Tom Demarco had a few things to say on cohesion. 

- Cohesion is a measure of the strength of association of the elements inside a module. 
- A highly cohesive module is a collection of statements and data items that should be treated as a whole because they are so closely related.

Tom Demarco never mentioned a specific number - Robert C Martin said SINGLE RESPONSIBILITY  

#### Cohesion 

Cohesion is one of the things that people struggle with. It is a little more abstract and intellectual.

We refer to a sound line of reasoning as coherent. The thoughts fit, they go together, they relate to each other. This is exactly the characteristic of a class that makes it coherent: the pieces all seem to be related, they seem to belong together.

Think of cohesion as the opposite of being adhesive. Adhesive is when you put two things that were not meant to be put together and stick them together.

An example would be a class that is called 'Utility' is probably not cohesive. Another example would be a 'Library'.

#### Should a class have a single responsibility?

Grady Booch in his book object solutions wrote the following:  

> Every class should embody only about 3-5 distinct responsibilities  

What is a single responsibility of a REPL?

- It has at least 3 responsibilities!  
- The REPL's responsibility is to bind things together?  

If you push SRP you realize it doesn't really work well at this level.

#### Deeper Irony

If you read Robert C Martin section he wrote in 97 things every programmer should know you get another idea of what Robert C Martin meant.

Single reason for change is not the same as single responsibility.

Two ideas rolled into one.

### Interface Segregation

The dependency should be on the interface, the whole interface and nothing but the interface. 

If you have applied SRP, you have nothing further to do - thus there would be no need for Interface Segregation?  

- SRP applied to interfaces is interface segregation.
- There is a language dependency, Ruby, Python do not have interfaces

Interface Segregation is a weak contender.

### Liskov Substitution

On legacy code bases inheritance is a pain in the backside and highly coupled.

**Watch Kevlin discussion on this**

(45:15)

### Open Close Principle

The principle stated that a good module structure should be both open and closed.  

Betrand Meyer says...

> Closed, because clients need the module's services to proceed with their own development, and once they have settled on a version of the module should not be affected by the introduction of new services they do not need.  

We are not going to get very far if we cannot change code. We do not want our module structure to be closed - we want to be able to refactor things. There are pieces of code that we can change easily, and there are pieces that we can't.

Martin Fowler used a better term. If the code is yours, and you know the dependencies you can change it. If you do not know the dependencies then you should not change it.  

> Open, because there is no guarantee that we will include right from the start every service potentially useful to some client.  

#### References

[Video of talk](https://vimeo.com/157708450)  
