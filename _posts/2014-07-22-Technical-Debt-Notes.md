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

[Shims, Jigs and Other Woodworking Concepts to Conquer Technical Debt](http://firstround.com/review/shims-jigs-and-other-woodworking-concepts-to-conquer-technical-debt/)  
