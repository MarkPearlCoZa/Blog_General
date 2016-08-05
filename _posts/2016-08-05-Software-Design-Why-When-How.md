---
layout: post
title: Software Design - Why, When & How Notes
tags: Design
category: Misc
---

These notes are based on Kent Beck's talk on "[Software Design: Why, When & How](https://vimeo.com/105771493)" done at JavaZone in September 2014.

## Intro ##

The **What** of Software Design is well established. We have a pretty good idea of "what" good software is. For instance, we have design patterns which have been around for well over a decade. 

Somehow in focussing so long, so effectively on what, we have forgotten to talk about the why.

When do you know when code should be tidied up?  
When do you apply a specific pattern or approach? 
Why would you apply that approach?  

Without talking about why we do software design, we don't have an opportunity to be able to apply the right "what".

## When does design matter? ##

Software as its sits doesn't care how it is designed - it just runs. 
Software design is not software. Software design is about change - it is only when we want to change software does design play a role.

## Drivers of software design? ##

The first driver for software design is economics. We get paid to write programs. When we write programs, somebody expects to make money somehow, sometime.  

### Economic drivers of design ###

Economics has a good vocabulary for talking about timing.
There are two topics in economics we should consider.

1. Net Present Value  
2. Opportunity Cost
3. Options Value of Software  

#### Net Present Value ####

The first economic topic is NPV (Net Present Value). In essence, NPV says a dollar today is worth more than a dollar tomorrow. 

**This means we should earn money sooner and spend money later, all other things being equal.**  

Doing all design upfront flies in the face of NPV. When doing all design upfront, we are spending all the money today, and only earning money from that spend later.

#### Opportunity Cost ####

Opportunity cost is everything else you can be doing instead of what you are doing. 

If you look at the time you will put into software design at a point in time, what else can you be doing at that point in time?

#### Options Value of Software ####

If I have software and I can only make one kind of change to it, that software is **less** valuable than if I have the same software and can change it in 3 different ways. The future is unpredictable and we don't know which of those 3 ways will be most valuable. 

**If I have multiple options for change, I have more valuable software.**  

#### NPV vs. Options Value ####

Looking at NPV and Options Value, we have two competing forces. We would like to defer work, because we want to defer investment AND we want options, which requires us to do more work. NPV & Options Value of Software are economic drivers of Software Design.

### Human drivers of design ###

We also cannot forget than people make software. 

#### Humans like challenges ####

Part of the satisfaction of creating software is the sense of satisfaction one gets from doing a good piece of design. 

As software engineers, we like the challenge of taming software - of finding better design.

#### Humans like helping the next generation ####

As humans, we generally have a desire to help the next generation. We might have a section of code that does not require immediate design improvements, but as a sense of compassion for the next developer working on the system, we will work on improving the design.

### When to do software design? ###

Should you design now, or should you design later?  

To determine when to do software design is tricky. Economically, the ideal point when software should be defined for change is the instant before it needs to be changed however we often do not have enough information at the point of time when a design decision is made to make the right decision. 

#### Forces pushing us to do design later... ####

NPV pushes us to do design later.
Opportunity cost of software often pushes design later.
Lack of knowledge pushes design later.

#### Forces pushing us to do software design sooner... ####

Options value of software pushes design sooner.  
Batching effect pushes design sooner.  
Humans aspects pushes design sooner.

#### So when to do software design? ####

There are a set of forces that are different depending on who, when and what you are designing. There is no easy answer to this.  

### How to do software design? ###

If only the answer to the how was as simple as "Big changes in small steps". While this is usually the case, it is not always the case.  

Let's say that you have software that is such a tangled mess that it would take an incredible amount of time to clean up. Small safe steps can be expensive in time.  



## Misc ##

#### Coupling ####

Coupling, two elements are coupled if a change to one element implies a change to another element.
Coupling is important to software design becuase the costs of changing software are dominated by rippling changes (which means one section of code is coupled to another section). The exponetially rippling changes kills you in software design. Reducing coupling takes effort. The more you try to reduce coupling, the more expensive it gets. There is a trade off curve between effort and coupling.

#### Premature Abstraction ####

Premature abstraction makes it hard to get the right type of abstraction. When you abstract, you fix certain aspects while allowing other aspects to change. If you don't have enough types to look at, you may fix the wrong things.

#### Simplistic Rules ####

Software design does not lend itself to simplistic rules.

#### Batching Effect ####

There are economies of scale to doing design sooner provided you have the design right. (Shared context can be expensive to recreate later).
