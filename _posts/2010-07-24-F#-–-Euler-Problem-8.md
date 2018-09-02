---
layout: post
title: F# – Euler Problem 8
tags: 
category: General
---
Today I had some more spare time to give Euler a go and thought I would try my luck on problem 8.

The Problem

Find the greatest product of five consecutive digits in the 1000-digit number.

73167176531330624919225119674426574742355349194934 
96983520312774506326239578318016984801869478851843 
85861560789112949495459501737958331952853208805511 
12540698747158523863050715693290963295227443043557 
66896648950445244523161731856403098711121722383113 
62229893423380308135336276614282806444486645238749 
30358907296290491560440772390713810515859307960866 
70172427121883998797908792274921901699720888093776 
65727333001053367881220235421809751254540594752243 
52584907711670556013604839586446706324415722155397 
53697817977846174064955149290862569321978468622482 
83972241375657056057490261407972968652414535100474 
82166370484403199890008895243450658541227588666881 
16427171479924442928230863465674813919123162824586 
17866458359124566529476545682848912883142607690042 
24219022671055626321111109370544217506941658960408 
07198403850962455444362981230987879927244284909188 
84580156166097919133875499200524063689912560717606 
05886116467109405077541002256983155200055935729725 
71636269561882670428252483600823257530420752963450

The Solution

I decided to make my solution a bit more generic instead of limiting it to just five consecutive digits I made this user defined. Looking at the data, I could not see a way of halting halfway through parsing it unless I reached the maximum possible x digit number, and so decided not to even worry about this occurring – instead the reality was that I would need every number and have to find the max one.

The crux of the code is in the get portion section. Basically what I do here is with the Seq.unfold method I generate a sequence of just x numbers, and then refold those into the product using the accumulator.

///
/// Gets a portion of a string and returns the product of it
///
let GetPortion (s:string, pos:int) =
    if (IsInRange(s, pos)) then      
        (s.Substring(pos),ConsNums) 
        |> Seq.unfold(fun(x,y) ->
            match (y>0) with
                | true -> Some(x.[0].ToString() |> Convert.ToInt32, (x.Substring(1),y-1))
                | false -> None)
        |> (Seq.fold(fun acc x -> acc*x) 1)
    else
        0
 

Once I had this working, to make the actual generator was really simple. Using the Seq.unfold function again, I parse every valid element in the data until I fall outside the range, and generate a sequence. The I just return the max value.

//
// Create a sequence of all the consecutive numbers
// in the data of length ConsNums
//
let SeqNumbers =
    (data,0)                 
    |> Seq.unfold(fun(x,y)->
        match IsInRange(x,y) with
            | true -> Some(GetPortion(x,y),(x,y+1))
            | false -> None)     
 

The entire solution looks like this…

open System

let data =  "73167176531330624919225119674426574742355349194934" +
            "96983520312774506326239578318016984801869478851843" +
            "85861560789112949495459501737958331952853208805511" +
            "12540698747158523863050715693290963295227443043557" +
            "66896648950445244523161731856403098711121722383113" +
            "62229893423380308135336276614282806444486645238749" +
            "30358907296290491560440772390713810515859307960866" +
            "70172427121883998797908792274921901699720888093776" +
            "65727333001053367881220235421809751254540594752243" +
            "52584907711670556013604839586446706324415722155397" +
            "53697817977846174064955149290862569321978468622482" +
            "83972241375657056057490261407972968652414535100474" +
            "82166370484403199890008895243450658541227588666881" +
            "16427171479924442928230863465674813919123162824586" +
            "17866458359124566529476545682848912883142607690042" +
            "24219022671055626321111109370544217506941658960408" +
            "07198403850962455444362981230987879927244284909188" +
            "84580156166097919133875499200524063689912560717606" +
            "05886116467109405077541002256983155200055935729725" +
            "71636269561882670428252483600823257530420752963450"


let ConsNums = 5    // The consecutive number

//
// Returns true if the position is within the range of the string
//
let IsInRange (s:string, pos:int) = pos < s.Length-ConsNums

///
/// Gets a portion of a string and returns the product of it
///
let GetPortion (s:string, pos:int) =
    if (IsInRange(s, pos)) then      
        (s.Substring(pos),ConsNums) 
        |> Seq.unfold(fun(x,y) ->
            match (y>0) with
                | true -> Some(x.[0].ToString() |> Convert.ToInt32, (x.Substring(1),y-1))
                | false -> None)
        |> (Seq.fold(fun acc x -> acc*x) 1)
    else
        0
        
//
// Create a sequence of all the consecutive numbers
// in the data of length ConsNums
//
let SeqNumbers =
    (data,0)                 
    |> Seq.unfold(fun(x,y)->
        match IsInRange(x,y) with
            | true -> Some(GetPortion(x,y),(x,y+1))
            | false -> None)     

printfn "%d" (SeqNumbers |> Seq.max)
 

Nothing to fancy, I would be interested to see other approaches, or if I could phrase this code better – any feedback from the F# community would once again be much appreciated.