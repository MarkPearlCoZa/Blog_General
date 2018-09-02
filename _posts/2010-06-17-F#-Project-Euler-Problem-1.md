---
layout: post
title: F# Project Euler Problem 1
tags: 
category: General
---
Every now and then I give project Euler a quick browse. Since I have been playing with F# I have found it a great way to learn the basics of the language. Today I thought I would give problem 1 an attempt…

Problem 1

If we list all the natural numbers below 10 that are multiples of 3 or 5, we get 3, 5, 6 and 9. The sum of these multiples is 23.

Find the sum of all the multiples of 3 or 5 below 1000.

My F# Solution

I broke this problem into two functions… 1) be able to generate a collection of numbers that are multiples of a number but but are smaller than another number.

let GenerateMultiplesOfXbelowY X Y = 
    X |> Seq.unfold (fun i -> if (i<Y) then Some(i, i+X) else None)

I then needed something that generated collections for multiples of 3 & 5 and then removed any duplicates. Once this was done I would need to sum these all together to get a result. I found the Seq object to be extremely useful to achieve this…

let Multiples = 
    Seq.append (GenerateMultiplesOfXbelowY 3 1000) (GenerateMultiplesOfXbelowY 5 1000) 
    |> Seq.distinct 
    |> Seq.fold(fun acc a -> acc + a) 0
    |> Console.WriteLine
    |> Console.ReadLine 

My complete solution was …

open System

let GenerateMultiplesOfXbelowY X Y = 
    X |> Seq.unfold (fun i -> if (i<Y) then Some(i, i+X) else None)

let Multiples = 
    Seq.append (GenerateMultiplesOfXbelowY 3 1000) (GenerateMultiplesOfXbelowY 5 1000) 
    |> Seq.distinct 
    |> Seq.fold(fun acc a -> acc + a) 0
    |> Console.WriteLine
    |> Console.ReadLine 
 

Which seemed to generate the correct result in a relatively short period of time although I am sure I will get some comments from the experts who know of some intrinsic method to achieve all of this in one method call.
