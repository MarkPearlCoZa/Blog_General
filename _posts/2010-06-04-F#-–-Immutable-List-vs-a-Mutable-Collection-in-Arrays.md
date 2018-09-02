---
layout: post
title: F# – Immutable List vs a Mutable Collection in Arrays
tags: 
category: General
---
Another day gone by looking into F#. Today I thought I would ramble on about lists and arrays in F#. Coming from a C# background I barely ever use arrays now days in my C# code – why you may ask – because I find lists generally handle most of the business scenario’s that I come across.

So it has been an interesting experience with me keep bumping into Array’s & Lists in F# and I wondered why the frequency of coming across arrays was so much more in this language than in C#.

Take for instance the code I stumbled across today.

~~~
let rng = new Random()
let shuffle (array : 'a array) = 
    let n = array.Length
    for x in 1..n do
        let i = n-x
        let j = rng.Next(i+1)
        let tmp = array.[i]
        array.[i] <- array.[j]
        array.[j] <- tmp
    array
~~~ 

Quite simply its purpose is to “shuffle” an array of items. So I thought, why does it have the “a’ array'” explicitly declared? What if I changed it to a list? Well… as I was about to find out there are some subtle differences between array’s & lists in F# that do not exist in C#. Namely, mutability.

A list in F# is an ordered, immutable series of elements of the same type, while an array is a fixed-size zero based, mutable collection of consecutive data elements that are all of the same type.

For me the keyword is immutable vs mutable collection. That’s why I could not simply swap the ‘a array with ‘a list in my function header because then later on in the code the syntax would not be valid where I “swap” item positions.

i.e. array.[i] <- array.[j] would be invalid because if it was a list, it would be immutable and so couldn’t change by its very definition..

So where does that leave me? It’s to early days to say. I don’t know what the balance will be in future code – will I typically always use lists or arrays or even have a balance, but time will tell.