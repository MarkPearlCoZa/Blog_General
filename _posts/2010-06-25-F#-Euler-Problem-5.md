---
layout: post
title: F# Euler Problem 5
tags: 
category: General
---
So today I tackled a Euler problem that I had originally looked into several months back when I initially started exploring F#

Problem

2520 is the smallest number that can be divided by each of the numbers from 1 to 10 without any remainder.

What is the smallest positive number that is evenly divisible by all of the numbers from 1 to 20?

Solution

I decided on the brute force approach again. I believe that I could have worked with prime factors etc to have reached the solution a lot quicker – but haven’t had time to look properly into that approach.

Once again the unfold function played a big role – now that I understand it a bit better, it doesn’t look like as much black magic as it initially looked like. I would love to get any suggestions / examples of how other people have solved this problem using F#

open System

let res =
    (21) 
    |> Seq.unfold (fun x -> Some(x,x+1))
    |> Seq.filter (fun x ->        
        x % 11 = 0
        & x % 12 = 0
        & x % 13 = 0
        & x % 14 = 0
        & x % 15 = 0
        & x % 16 = 0
        & x % 17 = 0
        & x % 18 = 0
        & x % 19 = 0
        & x % 20 = 0
        )
    |> Seq.head 
    
printfn "Lowest LCM is %d" res
Console.ReadLine()
