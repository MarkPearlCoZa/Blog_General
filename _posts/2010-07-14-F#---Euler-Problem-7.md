---
layout: post
title: F# - Euler Problem 7
tags: 
category: General
---
These last few days I attempted Euler Problem 7. It has been an interesting experience since it is the first real Euler problem that I initially attempted to tackle recursion for a solution but eventually bypassed as I found what I considered a simpler way to solve the problem.

In addition to recursion, it was also interesting to see performance issues occur, and how a better understanding of what some of the Seq functions does can dramatically effect the over all performance of the solution.

The Problem

By listing the first six prime numbers: 2, 3, 5, 7, 11, and 13, we can see that the 6th prime is 13.

What is the 10001st prime number?

The Solution

So I had a few hiccups with solving this solution.

First of all with my initial attempt I used trial division to try and check if a number was prime or not. This soon turned out to be impractical because of the number of comparisons I would need to perform to get to the solution. After having a look at how several other people solved this problem I did notice what I would consider to be an elegant approach to checking whether a number is prime or not.

Since I would need to check all the numbers that I came across on whether they were prime or not, it stood to reason that one way to solve the problem was to find the smallest prime, and then the next one and the next one. Since I would have all smaller primes stored, instead of using trial division, I could simply compare the candidate number with all the previously found primes, and if none of the previous primes divided perfectly into the candidate, then I would know that the candidate was also a prime.

Initially my code to achieve this looked something like the following…

let KnownPrimes = new System.Collections.Generic.List<int>()

let isInnerPrime candidate =
    match candidate with
        | candidate when candidate = 1 -> true
        | _ -> KnownPrimes
            |> Seq.filter(fun x -> x < candidate)
            |> Seq.filter(fun x -> candidate % x = 0)
            |> Seq.length = 0    
 

However, after completing the solution I soon discovered that the actual implementation was not optimized. It seemed what was happening was that my Seq.filter was filtering the entire all known primes collection, it wasn’t exiting as soon as the test case failed for a candidate which had a performance hit. Eventually I changed the code to the following, which

let isPrime candidate =    
    let isInnerPrime candidate =
        KnownPrimes |> Seq.forall(fun x -> x <> candidate && candidate % x <> 0)                
    if (isInnerPrime candidate) then
        KnownPrimes.Add(candidate)
        true
    else
        false
 

This seemed to do the trick…

In addition to the above, I also once again used lazy infinite lists. Basically I needed the system to somehow whenever the next prime number was to be found to keep incrementing candidates. Eventually I came up with what I thought looked quite elegant in the following code…

let Primes = Seq.initInfinite(fun x -> x+2) |> Seq.filter isPrime    
 

Finally I put it all together to have the following code…

open System

let KnownPrimes = new System.Collections.Generic.List<int>()

//
// Returns whether a candidate is a prime, based
// on the division of the candidate by all other
// previous known primes less than the candidate
// NB only works if all previous primes are known
//
let isPrime candidate =    
    let isInnerPrime candidate =
        KnownPrimes |> Seq.forall(fun x -> x <> candidate && candidate % x <> 0)                
    if (isInnerPrime candidate) then
        KnownPrimes.Add(candidate)
        true
    else
        false
        

let Primes = Seq.initInfinite(fun x -> x+2) |> Seq.filter isPrime    

let FindNthPrime nth =    
    if (KnownPrimes.Count > nth) then KnownPrimes.Item(nth) else
    Primes |> Seq.nth(nth)

KnownPrimes.Add(2)
printfn "%d" (FindNthPrime 10001)
Console.ReadLine()
 

One final note was that originally I decided to use basic memoization by using a dictionary. In the solution above however I adapted the dictionary to a list as I could not see any benefits of the key if it was just going to in effect be an index, but I haven’t looked up properly to see if there are any performance hits because of this or if there is a better holder for the this scenario.
