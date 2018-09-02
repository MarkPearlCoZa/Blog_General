---
layout: post
title: F# int |> bigint
tags: 
category: General
---
I had a bit of a no brainer yesterday… I have been using the forward pipe to convert values, and came up against the problem where the following code would work

let IntToFloat = 10 |> float
let FloatToInt = 10.0 |> int

But the equivalent bigint code would not work…

let FloatToBigint = 10.0 |> bigint

It was only after a few hours of reading up on type casting in F# and getting totally confused that I finally resulted to Stack Overflow. The answer was humbling…

The reason why FloatToBignint does not compile is because F# compiler is looking for a function called bigint that has an input of type float. Duh!

All along I was thinking that I needed to add some sort of overloading to the operator to allow bigint to accept the forward pipe and yet I had missed the obvious.

So as soon as I had the following function declared…

let bigint(x:float) = bigint(x)
 

the code…

let FloatToBigint = 10.0 |> bigint

works perfectly…

thank you Stack Overflow!
