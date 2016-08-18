---  
layout: post  
title: Public vs Published Interfaces
tags: Code Refactoring 
category: Misc  
---  
#### Public vs published interface

There are no issues refactoring public methods/class names/ etc, provided you know all of the consumers of refactored items. 

Don't refactor published interfaces (often we call these apis) when you do not know all the consumers of that functionality.

**With published interfaces, you never know all the consumers**  

#### References ####

[Kevlin Hennley - Solid Deconstruction]  
