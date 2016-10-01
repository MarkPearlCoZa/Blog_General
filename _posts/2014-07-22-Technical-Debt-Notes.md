---
layout: post
title: Technical Debt Notes
tags: Quality
category: Process
---
### What is technical debt?

The metaphor "Technical Debt" was first coined by Ward Cunningham.

> Shipping first time code is like going into debt. A little debt speeds development so long as it is paid back promptly with a rewrite. Objects make the cost of this transaction tolerable. The danger occurs when the debt is not repaid. Every minute spent on not-quite-right code counts as interest on that debt. Entire engineering organizations can be brought to a stand-still under the debt load of an unconsolidated implementation, object- oriented or otherwise.  

Because the definition of technical debt got so mixed up Ward Cunningham further [clarified what he meant by technical debt](https://www.youtube.com/watch?v=pqeJFYwnkjE) on YouTube in 2009.

#### It's only a metaphor

Sometimes technical debt can be a clumsy metaphor - there may be other metaphors that could better illustrate what we are trying to explain.

> A better metaphor may be technical wealth - Martin Cronje

### What technical debt is not

Many people confuse technical debt with other things like bugs, messy code, or bad design. 

#### Bugs are not technical debt

The key feature of technical debt is that its something we incur by choice. We choose to make architectural, design or implementation decisions that we expect will cause us issues later in order to achieve specific objectives sooner. A bug is not something we choose to have in our code - so de-facto its not technical debt

#### Messy code is not technical debt

Some people blur the distinction between messy code and technical debt. Messy code is not technical debt. Robert Martin [expands on this idea](https://sites.google.com/site/unclebobconsultingllc/a-mess-is-not-a-technical-debt).

> "In other words, the whole debt metaphor, let's say, the ability to pay back debt, and make the debt metaphor work for your advantage depends upon your writing code that is clean enough to be able to refactor as you come to understand your problem." - Ward Cunningham

### Clean, refactorable code is not optional

Writing clean, refactorable code is not optional. Put another way, writing dirty code is not inline with the technical debt metaphor.  

For instance, when you order your food at a restaurant, you don't get a menu option to pay for the dishes to be washed - this is just something expected and part of the process. Likewise, writing clean refactorable code is expected and part of the process.

> The stigma around debt — technical or otherwise — is that it’s a sign of weakness or leads to overreliance, when in fact it merely represents a trade-off, giving more time or resources at a cost  

Encode your standards into a linter or other static analyzer. Start with an almost empty set of rules, and then slowly add as you agree upon standards for your code.  

> Bad code often feels faster in the same way hurrying feels faster  

Label it, creating a rating system and building code in a modular way

### Can you calculate the cost of technical debt?

Doc Norton suggested 5 things you can measure to calculate the cost of technical debt.

- Code Coverage
- Code Complexity
- Coupling
- Maintainability

#### Code Coverage

#### Code Complexity

#### Coupling

#### Maintainability

Everything (security, scalability, etc.) is a feature except for maintainability.

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


#### References ####

[A mess is not technical debt](https://sites.google.com/site/unclebobconsultingllc/a-mess-is-not-a-technical-debt)  
[Ward Cunningham explaining Debt Metaphor on YouTube](https://www.youtube.com/watch?v=pqeJFYwnkjE)  
[Shims, Jigs and Other Woodworking Concepts to Conquer Technical Debt](http://firstround.com/review/shims-jigs-and-other-woodworking-concepts-to-conquer-technical-debt/)  
[Are bugs technical debt](http://programmers.stackexchange.com/questions/207060/are-bugs-part-of-technical-debt)  
[The Technical Debt Trap by Doc Martin](http://blog.markpearl.co.za/The-Technical-Debt-Trap)  
