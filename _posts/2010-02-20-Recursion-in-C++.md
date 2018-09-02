---
layout: post
title: Recursion in C++
tags: 
category: General
---
The process of solving a problem by reducing it into smaller versions of itself is called recursion. This problem solving technique can be a very powerful way to solve certain types of problems that would be very verbose and lengthy using other techniques such as an iterative approach.

When implementing a recursive solution one usually has at least two cases:

Base Case
General Case
For a function/method to be called recursive, it usually has a call to itself within its code in the general case, with a smaller case being passed through.

A typical example to illustrate a recursive function is the factorial function (i.e 5!)

~~~
//************************************ 
// Returns the factorial of a number 
//************************************ 
int fact(int num) 
{ 
    if(num <= 0) 
        return 1;                            // Base Case 
   else 
        return num * fact(num-1);    // General Case - also note it calls itself 
}
~~~

Things to know about Recursion

Direct Recursion – a function that calls itself within its block.

Indirect Recursion – a function that calls another function and eventually returns in the original function.

Infinite Recursion – when the recursive function never returns to the base case but continually calls the general case. This is one of the big pitfalls of recursion, and one should be careful to ensure that the base case will always be met so that the system can exit the call loop.

To design a recursive function one should do the following:

Understand the problem requirements
Determine the limiting conditions
Identify the base case and provide a direct solution to each base case
Identify the general cases and provide a solution to each general case in terms of smaller versions of itself
Some problems that can be solved elegantly using recursion are listed below…

Find the largest element in an array
Print a Linked List in Reverse Order
Fibonacci Number
Tower of Hanoi
Converting a Number from Decimal to Binary
etc
Recursion or Iteration – Does Azure change our approach?

Typically there are two ways to solve a problem, recursively or using iteration. Iterative approaches use a looping structure such as while, fore, or do…while, to repeat a set of statements.

In some instances implementing an iterative solution is simpler than a recursive solution, in other instances it is almost impossible – or extremely complicated to implement an iterative solution to a particular problem domain so it is important that you know the pro’s and con’s of each general approach.

The iterative approach typically uses less memory as it does not have to create multiple instances of each variable declared, and this could be seen as an efficiency benefit over the recursive approach – however the recursive approach generally is simpler to read / understand and thus is easier to modify if changes are needed at a later stage.

What I find interesting is up to recently the costs of a developers time vs the costs of a processors cycles always skewed towards the developers time as no real additional cost could be placed towards processor cycles, however with technologies like azure popping up where a very real charge is placed on processor cycles – the ball game has changed a bit and a company may be willing to invest more money in a iterative approach rather than a recursive approach because of the long term savings of charges due to additional processing on the cloud.