---
layout: post
title: My Optimized Adam and Eve
tags: 
category: General
---
Today I had a few minutes in the evening to go over my original Adam and Eve code… what I wanted to see tonight was if I could optimize the code any further… which I was pretty sure could be done. Ultimately what I wanted to find from the experiment was a balance between optimized code an reusable code.

On the one hand I can put everything into a single function and end up with a totally unusable function that is extremely compressed, which would have big comebacks when making modifications at a later stage. Alternatively I could have many single line functions that are extremely loosely coupled but sparsely spaced and so would almost be to fragmented to grok.

Ultimately I found with my current iteration something that I consider readable, yet compressed.

Code below…

~~~
// Learn more about F# at http://fsharp.net
open System

let people = [ ("Adam", None);
               ("Eve", None);
               ("Cain", Some("Adam", "Eve"));
               ("Abel", Some("Adam", "Eve")) ]               

//
// Prints the details
//
let showDetails(person : string * (string * string) option) =             
    let ParentsName =
        let parents = snd(person)
        match parents with
            | Some(dad, mum) ->  "Father " + dad + " and Mother " + mum
            | None -> "Has no parents!"

    let result = fst(person) + Environment.NewLine + ParentsName
    result
            
//
// Searches an array of people and looks for a match of names
//
let findPerson(name : string, people : (string * (string * string) option) list) =        
    
    // Try and find a match of the name
    let o = Seq.tryFind(fun person -> 
        match name with
            | firstName when firstName = fst(person) -> true
            | _ -> false) people              
    
    // Show the details based on the match result
    match o with
        | Option.Some(x) -> showDetails(Option.get(o))        
        | _ -> "Not Found"

        
Console.WriteLine(findPerson("Cains", people))
Console.ReadLine()
~~~