---
layout: post
title: F# Hello World
tags: 
category: General
---
An interesting paradigm

So today I got to play around with F# for the very first time. I must admit, it was very different to what I am used to, but I am keen to learn more.

Because I was using VS2008, before I could do anything in F# I needed to download and install the SDK.

Once installed it was pretty easy getting started. I tried the following Hello World example.

My thoughts on F# right now are not well formed. I can see the benefit of having a functional language in the .NET framework, but I still don’t know enough about functional languages to know in what scenarios it would be viable to use vs. C#.

Well… in the next few months I am going to try get into it a lot more… so we shall see!

Here is the code snippet…

~~~
open System

printfn "hello world";

let name = Console.ReadLine() 
~~~
