---
layout: post
title: F# Project Euler Problem 3
tags: 
category: General
---
So this weekend I made an attempt at problem 3 of Project Euler.

Problem 3

The prime factors of 13195 are 5, 7, 13 and 29.

What is the largest prime factor of the number 600851475143 ?

My Solution

 

~~~
//
// Checks whether a number is prime or not using the Trial Division approach
// To improve performance I have only pass through odd numbers greater than 2 and do not check for this case
//
let isPrime (number : bigint) =
    match number with        
        | _ -> seq { bigint(2) .. bigint(1) .. bigint (Math.Sqrt (float number))}    
                |> Seq.exists (fun x -> if (number % x = bigint(0)) then true else false)      
                |> not        


//
// Returns a sequence of prime numbers up to number x
//
let primenumbersOf (number : bigint) =    
    let oddPrimes = seq { bigint(3).. bigint(2) .. number} |> Seq.filter(fun x -> isPrime x)                
    Seq.append [bigint(2)] oddPrimes


//
// Returns a sequence of prime factors of a specific number x
//
let primefactornumbersOf (number : bigint) =
    primenumbersOf (number / bigint(Math.Sqrt(float(number))))    
    |> Seq.filter(fun x -> number % x = bigint(0))
    

primefactornumbersOf(bigint(600851475143.0)) |> Seq.iter (fun x -> Console.WriteLine(x))
Console.WriteLine("Finished")
Console.ReadLine()
~~~

It works fine except it is not the most performant approach. I would appreciate any feedback from people that could maybe help me look at a different approach that would return a quicker result.