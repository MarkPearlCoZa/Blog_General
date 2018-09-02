---
layout: post
title: F# and the useful infinite Sequence (I think)
tags: 
category: General
---
So I have seen a few posts done by other F# fans on solving project Euler problems. They looked really interesting and I thought with my limited knowledge of F# I would attempt a few and the first one I had a look at was problem 5.

Which said : “2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder. What is the smallest number that is evenly divisible by all of the numbers from 1 to 20?”

So I jumped into coding it and straight away got stuck – the C# programmer in me wants to do a loop, starting at one and dividing every number by 1 to 20 to see if they all divide and once a match is found, there is your solution. Obviously not the most elegant way but a good old brute force approach. However I am pretty sure this would not be the F# way….

So after a bit of research I found the Sequences and how useful they were. Sequences seemed like the beginning of an approach to solve my problem. In my head I thought - create a sequence, and then start at the beginning of it and move through it till you find a value that is divisible by 1 to 20. Sounds reasonable?

So the question is begged - how would you create a sequence that you are sure will be large enough to hold the solution to the problem? Well… You can’t know!

Some more googling and I found what I would call infinite sequences – something that looks like this…

~~~
let nums = 1 |> Seq.unfold (fun i -> Some (i, i + 1))
~~~ 

My interpretation of this would be as follows… create a sequence, and whenever it is called add 1 to its size (I would appreciate someone helping me on wording this right functionally).

Something that I don’t understand fully yet is the forward pipe operator (|>) which I think plays a key role in this code.

With this in hand I was able to code a basic optimized solution to this problem. I’m going to go over it some more before I post the full code just in case!
