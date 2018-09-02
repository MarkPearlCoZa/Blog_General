---
layout: post
title: F# Euler Problem 16
tags: 
category: General
---
Well after a hectic week of work and studying I eventually had some me time… today I thought I would attempt Euler Problem 16.

The Problem

215 = 32768 and the sum of its digits is 3 + 2 + 7 + 6 + 8 = 26.

What is the sum of the digits of the number 21000?

The Solution

So I thought I would get to concerned about length of code, but rather focus on implementing several practices that I have learnt in the last couple of weeks, namely tail recursive functions and composite functions…

I initially broke the solution up into two parts, a function that calculated the power and then a function that parsed that result and added the numbers together (sum them).

let PowerN n:bigint =
    let rec innerPowerN(n:bigint, act:bigint) =
        match n with
        | v when v<1I -> act
        | _ -> innerPowerN((n-1I), act*2I)
    innerPowerN (n, 1I)
When I came to summing the digits, I hit a bit of a road block, but then saw a nice implementation of Stack Overflow for converting a character to an value.

///
/// Converts a value to a bigint digit
///
let Value c =  
    let table = [ 
        '1', 1I ; '2', 2I ; '3', 3I
        '4', 4I ; '5', 5I ; '6', 6I 
        '7', 7I ; '8', 8I ; '9', 9I 
        '0', 0I ] 
    let dictionary = dict table 

    match dictionary.TryGetValue(c) with 
    | true, v -> v 
    | _ -> failwith (sprintf "letter '%c' was not in lookup table" c) 

//
// Sum all the digits in a bigint
//
let SumDigits(x:bigint) =            
    x.ToString().ToCharArray() |> Seq.sumBy Value
 

Finally using composite functions I put it all together…

let Euler16 = PowerN >> SumDigits

The entire code looked like the following…

///
/// Converts a value to a bigint digit
///
let Value c =  
    let table = [ 
        '1', 1I ; '2', 2I ; '3', 3I
        '4', 4I ; '5', 5I ; '6', 6I 
        '7', 7I ; '8', 8I ; '9', 9I 
        '0', 0I ] 
    let dictionary = dict table 

    match dictionary.TryGetValue(c) with 
    | true, v -> v 
    | _ -> failwith (sprintf "letter '%c' was not in lookup table" c) 

//
// Sum all the digits in a bigint
//
let SumDigits(x:bigint) =            
    x.ToString().ToCharArray() |> Seq.sumBy Value
        
let PowerN n:bigint =
    let rec innerPowerN(n:bigint, act:bigint) =
        match n with
        | v when v<1I -> act
        | _ -> innerPowerN((n-1I), act*2I)
    innerPowerN (n, 1I)

let Euler16 = PowerN >> SumDigits
 

While I am pretty sure there is a nicer way to implement “Value”, other than that I am pretty happy with the solution although I am sure this can be solved in a one liner as well…