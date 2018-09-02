---
layout: post
title: F# - Euler Problem 9
tags: 
category: General
--- 
Another day flown by… another Euler problem to tease me… today I attempted problem 9.

The Problem

A Pythagorean triplet is a set of three natural numbers, a < b < c, for which a^2 + b^2 = c^2

For example, 3^2 + 4^2 = 9 +16 = 25 = 5^2.

There exists exactly one Pythagorean triplet for which a + b + c = 1000. 
Find the product abc.

The Solution

Initially I thought I would try and tackle this problem by setting up 3DArrays in F#, thus my question on StackOverflow regarding 2D Array.

However, if I used the arrays I would not be able to use the handy Seq methods. After some more thinking, I decided to use tuples instead and generate the permutations using the Seq.unfold method.

let generatePossibleCandidates =  
          (1,1) 
          |> Seq.unfold(fun (x,y) ->                                
                let z = TargetResult - (x+y)
                let xyz = x*y*z
                if (y>TargetResult) then None                
                else if (x>=y-1) then Some((Square(x),Square(y),Square(z),xyz), (1,y+1))
                else Some((Square(x),Square(y),Square(z),xyz), (x+1,y))                
          )
 

I must be honest I am not to happy with the formatting of this code… it looks a bit clunky and messy… but it did the trick for now. Once I had all possible permutations generated, filtering the result was relatively simple.

let FilterCandidates data = 
    data |> Seq.filter(fun (x,y,z,r) -> (x+y=z))    
         |> Seq.filter(fun (x,y,z,r) -> (x<y) && (y<z))    
         |> Seq.iter(fun x -> 
            let (a,b,c,d) = x            
            printfn "%f" (Math.Sqrt(a|>float)) 
            printfn "%f" (Math.Sqrt(b|>float))
            printfn "%f" (Math.Sqrt(c|>float))
            printfn "%d" d
            ()
          )

The entire solution looked like this…

open System

let TargetResult = 1000
let Square x = x*x

///
/// Generate all permutations, by producing squares of x & y with z being the 
/// targetresult - the sum of x & y
///
let generatePossibleCandidates =  
          (1,1) 
          |> Seq.unfold(fun (x,y) ->                                
                let z = TargetResult - (x+y)
                let xyz = x*y*z
                if (y>TargetResult) then None                
                else if (x>=y-1) then Some((Square(x),Square(y),Square(z),xyz), (1,y+1))
                else Some((Square(x),Square(y),Square(z),xyz), (x+1,y))                
          )

///
/// Filter permutation by reducing the collection by the
/// problem criteria.
///
let FilterCandidates data = 
    data |> Seq.filter(fun (x,y,z,r) -> (x+y=z))    
         |> Seq.filter(fun (x,y,z,r) -> (x<y) && (y<z))    
         |> Seq.iter(fun x -> 
            let (a,b,c,d) = x            
            printfn "%f" (Math.Sqrt(a|>float)) 
            printfn "%f" (Math.Sqrt(b|>float))
            printfn "%f" (Math.Sqrt(c|>float))
            printfn "%d" d
            ()
          )

FilterCandidates generatePossibleCandidates

I understand that there are some algebraic approaches to solving this problem, but I found the brute force approach to be performant enough for me not to worry about it any further….
