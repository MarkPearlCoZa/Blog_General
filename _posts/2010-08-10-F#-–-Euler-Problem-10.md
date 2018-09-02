---
layout: post
title: F# – Euler Problem 10
tags: 
category: General
---
So today I had the pleasure of attempting Euler Problem 10… the problem goes as follows…

The Problem

The sum of the primes below 10 is 2 + 3 + 5 + 7 = 17.

Find the sum of all the primes below two million.

The Solution

What I enjoyed about this problem is that if you have done the previous Euler problems, then this problem is really just a focus on pure performance as the other aspects of the problem have in essence been solved before. Not that I have found an optimal solution, in fact I was very disappointed about the end performance of my code, but while attempting to solve the problem it was impossible not to look at performance.

I decided to approach the problem by using the same strategy I used in previous problems about prime numbers with Euler – that being that if one started at 1 and calculated every prime number sequentially, then the next prime number would not be divisible any of the primes prior to it. My reasoning on this was that there would be relatively few prime numbers in comparison to other numbers and so I would get better performance than if I were to use something like trial division.

My initial Prime calculation looked as follows…

 

let KnownPrimes = new System.Collections.Generic.List<int64>()


let isPrime(candidate:int64) =            
    let isInnerPrime candidate =          
        KnownPrimes 
        |> Seq.filter(fun x -> x <= int64(Math.Sqrt(float(candidate))))
        |> Seq.forall(fun x -> (candidate % x <> 0L))
    if (isInnerPrime candidate = true) then            
        KnownPrimes.Add(candidate)        
        true                                                                                                            
    else
        false            

Everything seemed great until I ran the program… it was slow, especially when I started calculating primes over 10 000. A second glance at my isPrime function and I immediately thought that the Math.Sqrt operation expensive. After a bit more examination I realized that I could possibly implement a bit of precomputation so that the Math.Sqrt would only be called once for every iteration of the isPrime call. This made my code look like the following…

let isPrime(candidate:int64) =        
    let UpperBoundFilter = int64(Math.Sqrt(float(candidate)))
    let isInnerPrime candidate =          
        KnownPrimes 
        |> Seq.filter(fun x -> x <= UpperBoundFilter)
        |> Seq.forall(fun x -> (candidate % x <> 0L))
    if (isInnerPrime candidate = true) then            
        KnownPrimes.Add(candidate)        
        true                                                                                                            
    else
        false            

That being done, I could already see about a 20% increase in speed when calculations were in the 10 000 range. Assuming that I wasn’t going to optimize my isPrime function any further, I then moved on to the GetSumOfSequence function. My initial attempt looked like this…

let GetSumOfSequence (n:int64) =     
    let result n = 
        seq{1L..n}                
        |> Seq.filter (fun x -> isPrime x)
        |> Seq.sum
    result n + 2L

Once again, not as great a performance as I hoped… things were still chuggy. Some more examination of the code hinted at a minor improvement I could do where instead of generating a sequence including all even numbers, I could only generate a sequence of odd numbers (2 is the only even prime number I have ever heard of). With this adjustment the code looked as follows.

let GetSumOfSequence (n:int64) =     
    let result n = 
        seq{3L..2L..n}                
        |> Seq.filter (fun x -> isPrime x)
        |> Seq.sum
    result n + 2L
Again, it seemed faster, but when I ran the whole thing together it still took several minutes to calculate the correct solution. My entire solution was as follows…

open System

let KnownPrimes = new System.Collections.Generic.List<int64>()
//
// Returns whether a candidate is a prime, based
// on the division of the candidate by all other
// previous known primes less than the candidate
// NB only works if all previous primes are known
//
let isPrime(candidate:int64) =        
    let UpperBoundFilter = int64(Math.Sqrt(float(candidate)))
    let isInnerPrime candidate =          
        KnownPrimes 
        |> Seq.filter(fun x -> x <= UpperBoundFilter)
        |> Seq.forall(fun x -> (candidate % x <> 0L))
    if (isInnerPrime candidate = true) then            
        KnownPrimes.Add(candidate)        
        true                                                                                                            
    else
        false            

       
let GetSumOfSequence (n:int64) =     
    let result n = 
        seq{3L..2L..n}                
        |> Seq.filter (fun x -> isPrime x)
        |> Seq.sum
    result n + 2L


KnownPrimes.Add(2L)
let Res = GetSumOfSequence(2000000L)
 

So, it calculates the correct result, but still not as fast as I would like it to. I considered looking at parallel extensions, in particular possibly replacing some of the Seq with PSeq functions, but for some reason could not seem to be able to get that to work, so for now I have had to resort to the above solution.

If anyone has suggestions on how I can optimize this code further, or if another approach would be better, I would appreciate any feedback.