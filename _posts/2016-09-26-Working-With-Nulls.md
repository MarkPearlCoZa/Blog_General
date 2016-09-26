---
layout: post
title: Working with Nulls
tags: Code 
category: Misc
---
Today I would like to spend some time on nulls. Before you go through tackle nulls you should first understand the difference between reference type variables and value type variables. I'm going to assume you already have this understanding - if you don't read this [this](http://stackoverflow.com/questions/5057267/what-is-the-difference-between-a-reference-type-and-value-type-in-c).  

### Before there were nulls there were magic numbers

Magic number variables are variables that have specific values that represent a state. The first time I was introduced to this concept was back in my Visual Basic 6 days. 

Back then it was not uncommon for me to use magic numbers to represent a specific state. For example, if I had a variable age and I wanted to represent it as 'unset' I would give 'age' a value of -1. This made perfect sense, when would you ever come across someone with a negative age?

The problem with magic numbers is you begin to litter your code with if statements. Also, every time you perform some sort of calculation on the value you first have to check if it is in one of your magic states. If you don't you can introduce subtle bugs - like the one below...

~~~
var discount = (age < 20) ? 0.5 : 1.0;  
// what happens if we don't check for age to be unset!!
~~~

I would advise to avoid this practice in languages where you have the option to choose null.

Using magic numbers increases the opportunities for subtle errors and makes it more difficult for the program to be adapted and extended in future.


### Passing Nulls around for Errors

### Null Object Pattern

#### References

[Pluralsight Working with Nulls](https://app.pluralsight.com/library/courses/csharp-nulls-working)  
[Wiki on Magic Numbers](https://en.wikipedia.org/wiki/Magic_number_(programming)#Unnamed_numerical_constants)  
