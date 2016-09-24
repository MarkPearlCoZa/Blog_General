---
layout: post
title: "SOLID Deconstruction"
description: ""
tags: Code
category: Media
---

These notes are based on [Kevlin Henney](https://twitter.com/KevlinHenney) talk on "[SOLID Deconstruction](https://vimeo.com/157708450)" done at NDC London 2016.

### SOLID Principles are not quite right...  

- One of the principles has two ideas rolled into one  
- One of the principles is subordinate to the other  
- One of the principles is not even a practice at all  

### Are these even principles?

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

Looking at SOLID as a context piece of advice (pattern) is better. SOLID principles can have situations where it is contextually good, but change the context and the advice can be bad.  

Let's examine specific aspects of SOLID.  

### Single Responsibility Pattern  

> A class should have only a single responsibility (i.e. only one potential change in the software's specification should be able to affect the specification of the class)

Robert C Martin described this concept being based on the principle of cohesion, as described by [Tom Demarco](https://en.wikipedia.org/wiki/Tom_DeMarco) in his book **[Structured Analysis and System Specification](https://www.amazon.com/Structured-Analysis-System-Specification-DeMarco/dp/0138543801)**.  

Tom Demarco had a few things to say on cohesion. 

- Cohesion is a measure of the strength of association of the elements inside a module. 
- A highly cohesive module is a collection of statements and data items that should be treated as a whole because they are so closely related.

While Tom Demarco had some strong feelings on modules being cohesive, he never mentioned a specific number of responsiblities a module should have - Robert C Martin however did. In proposing a SINGLE responsibility he specifically proposed that a module should have one responsiblity. This can be contested.

#### Understanding Cohesion 

Typically in software engineering whenever someone talks about cohesion, one also talks about coupling. Coupling is generally an easy concept to understand. Cohesion on the other hand is a little more abstract and intellectual and consequently a concept that many people struggle with.  

We refer to a sound line of reasoning as coherent. The thoughts fit, they go together, they relate to each other. The reasoning is highly cohesive. This is exactly the characteristic of a class that makes it coherent: the pieces all seem to be related, they seem to belong together.

> Think of cohesion as the opposite of being adhesive. 

Adhesive is when you put two things that were not meant to be put together and stick them together. Cohesion is the opposite of adhesion.

An example of an adhesive class would typically be those classes that are called 'utility' classes. Generally utility classes are not cohesive - they just have a bunch of things put together. With that in mind, let's re-explore whether a class should have a single responsbility.

#### Should a class have a single responsibility?

Grady Booch in his book object solutions wrote the following:  

> Every class should embody only about 3-5 distinct responsibilities  

Based on Grady Booch's comments a class can still be a good class and have more than one responsibility. 

Let's look at a practical example of this. Let's look at a REPL.  

What is a single responsibility of a REPL?

By it's very definition a REPL reads, evaluates, prints & loops. It has at least 3 responsibilities!  

One could argue that the REPL's responsibility is to bind things together but that seems to be very wishy washy.

> If you push SRP to it's limits you realize it doesn't really work well at this level. Classes can have more than one responsibility.

There is a deeper irony with SRP. If you read Robert C Martin's section he wrote in 97 things every programmer should know you get another idea or thought regarding SRP. In this book he proposes that SRP is actually meant to be a single reason for change. This seems to have two ideas rolled into one. A single reason for change is not the same as single responsibility.

### Interface Segregation Pattern

The dependency should be on the interface, the whole interface and nothing but the interface. 

If you have applied SRP, you have nothing further to do - thus there would be no need for Interface Segregation?  

- SRP applied to interfaces is interface segregation.
- There is a language dependency, Ruby, Python do not have interfaces

Interface Segregation is a weak contender.

### Liskov Substitution Pattern

> Objects in a program should be replaceable with instances of their subtypes without altering the correctness of that program.

On legacy code bases inheritance is a pain in the backside and highly coupled.

**Watch Kevlin discussion on this**

(45:15)

### Open Close Pattern

> Software entities … should be open for extension, but closed for modification.  

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

### Dependency Inversion Pattern

> One should depend upon abstractions. Do not depend upon concretions

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

- [Video of talk](https://vimeo.com/157708450)  
- [Wiki on SOLID](https://en.wikipedia.org/wiki/SOLID_(object-oriented_design))  
- [Wiki on Robert C Martin](https://en.wikipedia.org/wiki/Robert_Cecil_Martin)  
- [Wiki on Tom Demarco](https://en.wikipedia.org/wiki/Tom_DeMarco)  
- [Amazon on Structured Analysis and System Specification](https://www.amazon.com/Structured-Analysis-System-Specification-DeMarco/dp/0138543801)  
