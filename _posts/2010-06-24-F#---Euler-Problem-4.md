---
layout: post
title: F# - Euler Problem 4
tags: 
category: General
---
The last few days I began to play around with problem 4 of Euler. I really enjoyed this problem since it dealt with a few functions in F# that I haven’t dealt with in the past.

Problem

A palindromic number reads the same both ways. The largest palindrome made from the product of two 2-digit numbers is 9009 = 91 × 99.

Find the largest palindrome made from the product of two 3-digit numbers.

Solution

So I divided the problem up into a few functions…

reverseString simply reverses a string.

isPalindrome converts a number to a string and compares the number forwards to the number in reverse.

ProductOfNumbers is the interesting one for me – basically with my initial attempt I just generated a series of numbers and their product. The issue I was having with this approach was that it is the brute force approach, and I could not rely on the first or last palindrome to be the largest palindrome. To solve the second area of my problem I added an additional field to my solution Tuple which was the sum of x & y, because the largest sum of x & Y will result in the largest product of x & Y

~~~
let ProductOfNumbers num minnum =
    (num, num)
    |> Seq.unfold(fun(x,y)->
        match y with        
        | y when y < minnum -> None        
        | y when y = x -> Some((x*y,x,y,x+y), (num,y-1))        
        | _ -> Some((x*y,x,y,x+y), (x-1,y))
        )
    |> Seq.sortBy(fun x -> 
        let _,_,_,key = x     
        -key)
~~~

Finally in the res function I filter my results so that I only have palindromes and get the first one, which will be the largest one.

~~~
let res = 
        //
        // Generate tuple combinations
        //
        ProductOfNumbers 999 100        
        //
        // Filter out only palidromes
        //
        |> Seq.filter(fun x -> 
            let a,_,_,_ = x 
            isPalidrome a)
        //
        // Display the results
        //
        |> Seq.head
        |> fun x ->         
            let a,b,c,d = x                
            Console.WriteLine(a.ToString() + " = " + b.ToString() + " x " + c.ToString())                
~~~
 

Whole Solution

~~~
open System

let reverseString (s:string) = new string(s |> Seq.toArray |> Array.rev)
let isPalidrome (x:int) =  x.ToString() = reverseString(x.ToString())

let ProductOfNumbers num minnum =
    (num, num)
    |> Seq.unfold(fun(x,y)->
        match y with        
        | y when y < minnum -> None        
        | y when y = x -> Some((x*y,x,y,x+y), (num,y-1))        
        | _ -> Some((x*y,x,y,x+y), (x-1,y))
        )
    |> Seq.sortBy(fun x -> 
        let _,_,_,key = x     
        -key)


let res = 
        //
        // Generate tuple combinations
        //
        ProductOfNumbers 999 100        
        //
        // Filter out only palidromes
        //
        |> Seq.filter(fun x -> 
            let a,_,_,_ = x 
            isPalidrome a)
        //
        // Display the results
        //
        |> Seq.head
        |> fun x ->         
            let a,b,c,d = x                
            Console.WriteLine(a.ToString() + " = " + b.ToString() + " x " + c.ToString())                
res

Console.ReadLine()
~~~
 

Conclusion

So I am aware that this does get the correct result, however I would be interested in looking at other approaches to solving this problem in F#. Any feedback / suggestions would be much appreciated.
