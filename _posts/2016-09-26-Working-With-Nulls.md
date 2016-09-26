---
layout: post
title: Working with Nulls
tags: Code 
category: Misc
---
I would like to spend some time on nulls. Before you tackle nulls you should first understand the difference between reference type variables and value type variables. I'm going to assume you already have this understanding - if you don't read [this](http://stackoverflow.com/questions/5057267/what-is-the-difference-between-a-reference-type-and-value-type-in-c).  

### Before there were nulls there were magic numbers

Before nulls there were magic number variables. Magic number variables are variables that have a specific value that represents a contextual state. The first time I was introduced to this concept was back in my Visual Basic 6 days. 

Back then it was not uncommon for me to use magic numbers to represent a specific state. For example, if I had a variable age and I wanted to represent it as 'unset' I would give 'age' a value of -1. Back in the days this made perfect sense, when would you ever come across someone with a negative age?

The problem with magic numbers is you begin to litter your code with if statements. Also, every time you perform some sort of calculation on the value you first have to check if it is in one of your magic states. If you don't you can introduce subtle bugs - like the one below...

~~~
var discount = (age < 20) ? 0.5 : 1.0;  
// what happens if we don't check for age to be unset!!
~~~

> The rule of thumb is avoid magic number values to represent unset variables if you can rather set the variable to null

Ultimately using magic numbers increases the opportunities for subtle errors and makes it difficult for the program to be adapted and extended in future. Things we want to avoid.

### Passing Nulls around for Errors

### Null Object Pattern

#### References

[Pluralsight Working with Nulls](https://app.pluralsight.com/library/courses/csharp-nulls-working)  
[Wiki on Magic Numbers](https://en.wikipedia.org/wiki/Magic_number_(programming)#Unnamed_numerical_constants)  
