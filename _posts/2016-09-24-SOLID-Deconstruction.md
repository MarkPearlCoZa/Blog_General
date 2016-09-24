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

If you look at the dictionary definitions of a 'principle' you get...  

- a fundamental truth  
- foundation for a system of belief  
- morally correct behavior or attitude  
- general scientific theorem or law   

> It turns out words matter, in software we use a bunch of words but we are fairly rubbish in using them - Kevlin Henney

If we look at SOLID, it is not a set of principles. A more suitable word to describe SOLID is that it is a **collection of patterns**.  

What is a pattern?  

If you look at the dictionary definition of a 'pattern' you get...
  
- a regular form or sequence discernible in the way in which something happens or is done  
- a example for others to follow  
- a context specific piece of advice  

Looking at SOLID as a context piece of advice (pattern) is better. 

That makes the advice that SOLID gives can be contextually good, but change the context and the advice could be bad.  

Let's examine specific aspects of SOLID.  

### Single Responsibility  

> A class should have only a single responsibility (i.e. only one potential change in the software's specification should be able to affect the specification of the class)

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

Betrand Meyer in Object-oriented Software Construction book said about Open & Closed...

> Closed, because clients need the module's services to proceed with their own development, and once they have settled on a version of the module should not be affected by the introduction of new services they do not need.  

We are not going to get very far if we cannot change code. We do not want our module structure to be closed - we want to be able to refactor things. There are pieces of code that we can change easily, and there are pieces that we can't.

If the code is yours, and you know the dependencies you can change it. If you do not know the dependencies then you should not change it.  

> Open, because there is no guarantee that we will include right from the start every service potentially useful to some client.  

This is a non problem when we have version control. When Meyer speaks about a open module construction he is meaning you should use inheritance. This is going to create the kind of pain you are going to experience in a legacy code base. Avoid this.

Back to R C. Martin's explanation of OCP it says...

"Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification."

Betrand Meyer's book was a language design principle - he was talking about how to design a language - not how to design a program.

The lesson we can learn from all this is **Don't Publish Interfaces Prematurely** - refactoring book.  

### Dependency Inversion

- Relatively few gripes with except for the name in object oriented programming  

The principle states:  
- high level modules should not depend on low level modules  

This is good design.

If we look at the words used in the naming of the principle...

Dictionary definition of Inversion

- the action of inverting the state of being inverted  
- reversal of the normal order

Dependency Inversion is not the **inversion** of the normal order, it is now the normal order.

#### Keywords to look at  

- Subsumption  

#### References

[Video of talk](https://vimeo.com/157708450)  
[Wiki on SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))  
