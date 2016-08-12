---
layout: post
title: Transformation Priority Premise
tags: Design
category: Programming
---
#### General Notes ####

*Refactorings* have counterparts called *Transformations*  

Refactorings are simple operations that change the structure of the code without changing its behaviour.  
Transformations are simple operatins that change the behavior of the code.  

Transformations have a priority or prefered order. TDD has an approach of transforming a solution from "specific" to "generic". Below are a list of kown transformations.

#### List of Transformation ####

~~~
{} -> Nil
Nil -> Constant
Constant -> Constant+
Constant -> Scalar
Statement -> Statements
Unconditional -> If
Scalar -> Array
Array -> Container
Statement -> Recursion
If -> While
Expression -> Function
Variable -> Assignment
~~~

The priority premise says transformations on the top of the list should be preferred to those that are lower down.

To read up about Uncle Bob's notes on the concept [view here](http://blog.8thlight.com/uncle-bob/2013/05/27/TheTransformationPriorityPremise.html).
