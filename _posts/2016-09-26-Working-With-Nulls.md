---
layout: post
title: Working with Nulls
tags: Code 
category: Misc
---
Today I would like to spend some time on nulls. Before you can understand nulls and where they can be used, you first need to understand the difference between reference type variables and value type variables. I'm going to assume you already have this understanding.

### Prefer nulls to magic values/numbers 

Magic number variables are variables that have specific values that represent a state. The first time I was introduced to this concept was back in my vb6 days. 

Occaisonally we would use magic numbers to represent a specific state. For example, it was not uncommon for me to set the variable age a value of -1 if I wanted to represent age not having been set yet.

I would advise to avoid this practice in languages where you have the option to choose null.

Using magic numbers increases the opportunities for subtle errors and makes it more difficult for the program to be adapted and extended in future.


### Passing Nulls around for Errors

### Null Object Pattern

#### References

[Pluralsight Working with Nulls](https://app.pluralsight.com/library/courses/csharp-nulls-working)  
[Wiki on Magic Numbers](https://en.wikipedia.org/wiki/Magic_number_(programming)#Unnamed_numerical_constants)  
