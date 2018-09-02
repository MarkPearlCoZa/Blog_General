---
layout: post
title: F# FizzBuzz
tags: 
category: General
---
As per the post I decided to do a F# attempt at FizzBuzz. It took a few seconds…

Using FizzBuzz to Find Developers who Grok Coding..

~~~
let FizzBuzz =
    seq {1..100}
    |> Seq.iter (fun x ->
        match x with
           | x when x % 5 = 0 && x % 3 = 0 -> printfn "FizzBuzz"
           | x when x % 3 = 0 -> printfn "Fizz"
           | x when x % 5 = 0 -> printfn "Buzz"           
           | _ -> printfn "%d" x)
~~~