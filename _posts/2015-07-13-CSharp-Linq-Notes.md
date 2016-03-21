---
layout: post
title: CSharp Linq Notes
tags: Language
category: Tech
---

#### Simulate a for Loop ####

~~~

var n = 10;
var values = Enumerable.Range(0, n).Select(DoSomething)
 
Private static decimal DoSomething(int n)
{
                Return n * 0.1M;
}
~~~

#### Cartesian Product ####

Suppose you want to create the cartesian product of two lists (every possible combination between the two collections). This can be done as follows:

~~~
var listA = new List<int> { 1, 2, 3 };
var listB = new List<int> { 4, 5, 6 };
var cartesianLst = listA.SelectMany(a => listB.Select(b => new Tuple<int, int>(a, b)));
~~~
