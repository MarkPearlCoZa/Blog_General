---
layout: post
title: Technical Debt Notes
tags: Quality
category: Process
---
> The stigma around debt — technical or otherwise — is that it’s a sign of weakness or leads to overreliance, when in fact it merely represents a trade-off, giving more time or resources at a cost  

Encode your standards into a linter or other static analyzer. Start with an almost empty set of rules, and then slowly add as you agree upon standards for your code.  

> Bad code often feels faster in the same way hurrying feels faster  

Label it, creating a rating system and building code in a modular way

### What is the definition of technical debt

Ward Cunningham first coined the term Technical Debt:

> Shipping first time code is like going into debt. A little debt speeds development so long as it is paid back promptly with a rewrite. Objects make the cost of this transaction tolerable. The danger occurs when the debt is not repaid. Every minute spent on not-quite-right code counts as interest on that debt. Entire engineering organizations can be brought to a stand-still under the debt load of an unconsolidated implementation, object- oriented or otherwise.  

#### It's only a metaphor

Sometimes technical debt can be a clumsy metaphor - there may be other metaphors that could better illustrate what we are trying to explain.

A better metaphor may be technical wealth

### Everything is a feature except for maintainability  

Maintainability is the only thing you "don't" put on the box - security, scalability, etc. are all features.

### Bugs are not technical debt

The key feature of technical debt is that its something we incur by choice. We choose to make architectural, design or implementation decisions that we expect will cause us issues later in order to achieve specific objectives sooner. A bug is not something we choose to have in our code - so de-facto its not technical debt

### Messy code is not technical debt

Some people make a distinction between messy code and technical debt. Robert Martin expands on this idea here: [https://sites.google.com/site/unclebobconsultingllc/a-mess-is-not-a-technical-debt] Michael Norton also attempts to clear up the confusion here

### How do you calculate the cost of technical debt - can you quantify it?

### Sayings to illustrate why you should avoid technical debt

- When you order your food at a restaurant, you don't get a menu option to pay for the dishes to be washed - this is just something expected.  

### Framework Shifts

For engineering teams, half-completed framework shifts are one of the most common causes of confusing technical debt. Does introducing the new framework bring enough advantages? If so, should we move everything instead of having a foot in each camp?   

### Rating System - Rate things across 3 spectrums  

1) Security - are there security concerns associated with this code?  
2) Prevalence - how widespread is the code?  
3) Fequency - how often do you come into contact with the code?  2) Prevalence - how widespread is the code?  

### A Jig

> A jig is any code with the primary purpose of enabling better code, not being shipped into production and used itself. 

Examples of Jigs:  
- Test Code  
- Component Library (Twitter Bootstrap)  
- Golden Master  


#### Technical Debt Notes ####

5 Types
- Code
- Architectural
- Test
- Knowledge
- Technology

#### Technical Debt Quadrants ####

#### References ####

[A mess is not technical debt](https://sites.google.com/site/unclebobconsultingllc/a-mess-is-not-a-technical-debt)  
[Ward Cunningham explaining Debt Metaphor on YouTube](https://www.youtube.com/watch?v=pqeJFYwnkjE)  
[Shims, Jigs and Other Woodworking Concepts to Conquer Technical Debt](http://firstround.com/review/shims-jigs-and-other-woodworking-concepts-to-conquer-technical-debt/)  
[Are bugs technical debt](http://programmers.stackexchange.com/questions/207060/are-bugs-part-of-technical-debt)  
