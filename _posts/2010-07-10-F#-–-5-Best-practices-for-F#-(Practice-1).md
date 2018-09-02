---
layout: post
title: F# – 5 Best practices for F# (Practice 1)
tags: 
category: General
--- 
Daniel Mohl put up a great slide presentation on the 5 best practices for F#. Since I am new to the language I thought I would go through each practice and explore it a bit as separate posts.

Best Practice 1 – Prefer Short Functions with only one primary responsibility

As Daniel points out, functions that follow this practice enable

single responsibility pattern (SRP).
function composition
I must admit that up to this point, I have never really looked formally at what the SRP or Function Composition is. So today I am!

SRP

The Single Responsibility Pattern is a design pattern.

In my mind to know if function followed the SRP try and explain what a particular function does and if you had the “and” word somewhere in the explanation, you probably went against the pattern somewhere.

The example given on Wikipedia is of a module the compiles and prints a report. Such a module could be changed for two reasons, cosmetic & substantive. Thus it would not follow SRP.

Personally I have violated this pattern in past projects and lived to regret it because it introduced week points in my code. In one project the client came back a few weeks later to ask me to change a cosmetic aspect of the project, and because the modules were not correctly designed, I broke another aspect of the program inadvertently – so in retrospect I am a strong believer in the SRP pattern.

Function Composition

Before I go any further I recommend that you read [Chris Smith’s blog on Function Composition](http://blogs.msdn.com/b/chrsmith/archive/2008/06/14/function-composition.aspx).

Like Chris, I I have really grown fond of the |> operator to chain functions which I expressed in a previous post about the forward pipe operator. I have however not really understood the difference between the |> operator and the >> operator (function composition operator) – it all at first glance seemed pretty much the same thing, however in Chris’s post he then goes on to indicate with the |> operator one needs an initial value to start the chain.

With the function composition operator the initial state/value is not needed… it is purely looking at composing a new function based on a collection of other functions combined – this changes the ball game a bit – up to now I have always tried to solve problems in one long chain, with the function composition approach I can segment the code a bit more – with base functions, and then intermediate functions etc till one comes up with the end function.

See the other best practices…

Practice 1 - Prefer small functions with only one primary responsibility.
Practice 2 - Prefer function composition over argument passing.
Practice 3 – Tail Recursive Functions.
Practice 4 – Prefer Active Patterns over Multiple When Guards.
Practice 5 - Prefer pattern matching to if/else syntax.
