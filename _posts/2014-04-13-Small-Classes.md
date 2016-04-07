---
layout: post
title: "Small Classes"
description: "Small Classes"
category: General
tags: Design
---
For the last few years I have been an advocate of [SOLID principles](http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod) and trying to keep classes to a level where they have a [single responsibility](http://butunclebob.com/ArticleS.UncleBob.PrinciplesOfOod). In learning how to apply the Single Responsibility Principle I have found my classes have become small, focussed and reusable. The better I apply this principle, the more my classes possess these attributes. This was not always the case. There was a time when my classes were large and cumbersome. In looking back I can see there were several reasons why I fell into the trap of large classes - today I am going to explain two of them.

#### Reason One - Modelling classes to real world objects ####

The first reason why I had large classes was because of how I was taught object orientation. When I was first introduced to the concept of object orientation it was under the umbrella of general software design. I was told that good design was the process of breaking systems into components and then breaking those components into smaller components and so on. Object orientation was explained as one of the tools used to break a component into smaller components.

For example - if I wanted a sausage dog class I would need to form an inheritance chain. A sausage dog class inherits from a dog class which inherits from an animal class and so on. This lead to a massive misunderstanding on my side of what OO programming was and where its value was. Fundamentally it came down to this - I saw the need to model my classes as real world objects.

Experience has shown me that classes do not have a one to one with mapping the real world. When I model objects with a one to one mapping I find it impossible to indentify a single responsibility. Without identifying a single responsibility it is hard to keep my classes small. For instance, how does one identify the single responsibility of the poodle dog class? Bark, Walk, Wag Tail?

Having moved past the mindset of "objects" and towards a "responsibility" oriented view of classes it suddenly became possible to reduce the "size" of the classes dramatically. Having made the conceptual breakthrough I still found it extremely hard to implement, mainly because of my second reason for large classes.

#### Reason Two - Classes as a grouping mechanism ####

The second reason why I had large classes was because I was not comfortable navigating large code bases with many files. At some point early on in my programming career I saw classes as a convenient place to organize and locate procedures. For want of a better word, I was treating classes as I would typically treat "modules" in my old VB6 days. Looking back at those classes, they would end with words like "helper" or "manager". What at first was meant to help me apply the DRY principle soon fought against it.

Locating functionality for reuse is important. I predominantly work in the .Net space, so my experience is heavily effected by the toolset available to .Net programmers. In the early days of .Net programming I was not equipped to navigate solutions with lots and lots of classes.

For me the aha moment came when I joined [Driven Software](http://www.drivensoftware.com/). Our main client was using a solution that had many many small classes. I joined the project at a mature stage and could not avoid all those classes. Instead I had to learn how to live with them. In learning to live with them I was introduced to [ReSharper](http://www.jetbrains.com/resharper/). 

ReSharper's symbol search feature allowed me to easily navigate to classes without having to know exactly where in the solution the class is located. There are productivity enhancement tools in most IDE's that provide the same feature. If you don't know of one in your IDE of choice, find it now! By leveraging symbol search it became possible to navigate between small classes very efficiently. In doing so I was no longer held back from finding small classes and reusing them. 

#### What types of classes do I have now days? ####

When you are empowered to make classes smaller often one of two things happen - in becomming smaller they either become more generalized and reuse increases, or they become more specialized to the specifc business problem you are solving. Both these characteristics are good things. 

Classes that become more generalized become more abstract. This often means I have opportunities of reusing these classes elsewhere. Classes that become small and specialized also help reuse because the rest of the code is not "coupled" to it. These small specialized classes also become easier to unit test, which is a good thing.

#### How small should classes be? ####

So how small should a class be? It depends. I have found that I cannot make the interface of a class much smaller than a single well named public method. When I have reached a single public method I find the responsbility of the class is clear.

I don't always have a single public method. Sometimes I might have two or three public methods. At times like that I am aware that there might be some further design breakthroughs that will occur at a later stage. More than a couple public methods and I put on my refactoring hat to identify the responsbilities that have yet been discovered.

I have also found that at the point where the system connects with the outside world (typically the user interface) things get a bit messier than I would prefer. For now I am living with this, but I look forward to the day when this isn't a problem.
