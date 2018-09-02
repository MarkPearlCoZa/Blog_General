---
layout: post
title: F# Euler Problem 6
tags: 
category: General
---
Today I had a quick bash at problem 6. To me this has been the easiest of the problems so far. It is the first time though that I got to use the Seq.Fold function which was good to get exposure to. I am not to happy with my code though, I can’t explain it, but it just seems a bit messy…

Anyhow, I look forward to feedback from everyone in the F# community on their approaches.

Problem

The sum of the squares of the first ten natural numbers is,

12 + 22 + ... + 102 = 385 
The square of the sum of the first ten natural numbers is,

(1 + 2 + ... + 10)2 = 552 = 3025 
Hence the difference between the sum of the squares of the first ten natural numbers and the square of the sum is 3025  385 = 2640.

Find the difference between the sum of the squares of the first one hundred natural numbers and the square of the sum.

My Solution

let Square n = n*n

let Problem6 n = 
    let myseq = seq{1..n}
    let SumOfSquares n = myseq |> Seq.fold(fun acc x -> acc+(Square x)) 0
    let SquareOfSums n = Square(myseq |> Seq.sum)
    SquareOfSums(n) - SumOfSquares(n)