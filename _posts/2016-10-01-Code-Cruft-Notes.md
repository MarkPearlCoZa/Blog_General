---
layout: post
title: Code Cruft Notes
tags: Quality 
category: Misc
---

### What is code cruft?

<img class="img-responsive" alt="Cruft Definition" src="{{ site.url }}/assets/images/Technical-Debt-Cruft-Definition.png">

Code cruft is redundant, old, or improperly written code!

### Where does it come from?

> Bad code often feels faster in the same way hurrying feels faster  		

### Don't confuse cruft with technical debt

Code cruft is not technical debt. Dirty code was never intended to be included in the technical debt metaphor. It makes writing dirty code seem to be a strategic decision, when it isn't.

### How to avoid cruft

Label it, creating a rating system and building code in a modular way		

Encode your standards into a linter or other static analyzer. Start with an almost empty set of rules, and then slowly add as you agree upon standards for your code.  		
 		
### Framework Shifts		
 		
For engineering teams, half-completed framework shifts are one of the most common causes of confusing technical debt. Does introducing the new framework bring enough advantages? If so, should we move everything instead of having a foot in each camp?   		
 		
### Rating System - Rate things across 3 spectrums  		
 		
1) Security - are there security concerns associated with this code?  		
2) Prevalence - how widespread is the code?  		
3) Fequency - how often do you come into contact with the code?  		
 		
### A Jig		
 		
A jig is any code with the primary purpose of enabling better code, not being shipped into production and used itself. 		
 		
Examples of Jigs:  		
- Test Code  		
- Component Library (Twitter Bootstrap)  		
- Golden Master  		

[Shims, Jigs and Other Woodworking Concepts to Conquer Technical Debt](http://firstround.com/review/shims-jigs-and-other-woodworking-concepts-to-conquer-technical-debt/)  
