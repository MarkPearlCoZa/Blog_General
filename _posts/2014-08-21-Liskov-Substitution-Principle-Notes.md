---
layout: post
title: "Liskov Substitution Principle Notes"
description: "Liskon Substitution Principle Notes"
tags: [Notes, SOLID]
category: Programming
---
#### General Ramblings ####

*Uncle Bob*
Does the set of all sets that doesn't contain itself contain itself?

This statement is fale (logical loop)

Solution, restrict the types of a thing.  
What is a type?  

All that matters is the operations that can be performed on a type.  

Bag of operations (outside in) < Same as class?  

1988 - Barbara Liskov formal definition - subtypes can be used as their parent types  

The representation rule - represetatives do not share the relationship of the things they represent.  

E.g. Rect (height, width, area)  
Square (height, width, area) are height and widths sides??  

definition undefined behaviours = crash and burn  

