---
layout: post
title: Expert F# – Pattern Matching with Adam and Eve
tags: 
category: General
---
So I am loving my Expert F# book. I wish I had more time with it, but the little time I get I really enjoy. However today I was completely stumped by what the book was trying to get across with regards to pattern matching.

On Page 38 – Chapter 3, it briefly describes F# option values. On this page it gives the code snippet along the code lines below and then goes on to speak briefly about pattern matching...

~~~
open System

type 'a option =
    | None
    | Some of 'a

let people = [ ("Adam", None);
               ("Eve", None);
               ("Cain", Some("Adam", "Eve"));
               ("Abel", Some("Adam", "Eve")) ]               

let showParents(name, parents) = 
    match parents with
        | Some(dad, mum) -> printfn "%s has father %s, mother %s" name dad mum
        | None -> printfn "%s has no parents!" name

Console.WriteLine(showParents("Adam", None))
~~~
 
Originally when I read this code I think I misunderstood the purpose of the example code. I for some reason thought that the showParents function would magically be parsing the people array and looking for a match of name and then showing the parents. But obviously it cannot do this since there is no reference to the people array in the showParents method. After rereading the page I realized that I had just combined the two segments of code together, possibly incorrectly, and that a better example would have been to have a code snippet like the following.

let showParents(name, parents) = 
    match parents with
        | Some(dad, mum) -> printfn "%s has father %s, mother %s" name dad mum
        | None -> printfn "%s has no parents!" name

Console.WriteLine(showParents("Adam", None))
Console.WriteLine(showParents("Cain", Some("Adam", "Eve")))
Console.ReadLine()
 

However, what if I wanted to have a function that was passed a list of people and a name would then show the parents of the name if there were any, and if not would show that they had no parents… so that doesnt seem to difficult does it… lets look at my very unoptimized noob F# code to try and achieve this…

open System

let people = [ ("Adam", None);
               ("Eve", None);
               ("Cain", Some("Adam", "Eve"));
               ("Abel", Some("Adam", "Eve")) ]               

//
// returns the name of the person
//
let showName(person : string * (string * string) option) =     
    let name = fst(person)            
    name

//
// Returns a string with the parents details or not
//
let showParents(itemData : string * (string * string) option) = 
    let name = fst(itemData)
    let parents = snd(itemData)
    match parents with
        | Some(dad, mum) ->  "Father " + dad + " and Mother " + mum
        | None -> "Has no parents!"

//
// Prints the details
//
let showDetails(person : string * (string * string) option) =             
    Console.WriteLine(showName(person))            
    Console.WriteLine(showParents(person))            
        
    
//
// Check if the name matches the first portion of person
// if so, return true, else return false
//
let nameMatch(name : string , person : string * (string * string) option) =        
    match name with
        | x when x = fst(person) -> true
        | _ -> false


//
// Searches an array of people and looks for a match of names
//
let findPerson(name : string, people : (string * (string * string) option) list) =        
    let o = Seq.tryFind(fun x -> nameMatch(name, x)) people  
    if Option.isSome o then
        o
    else
        Option.None

//
// Try and find a person, if found show their details
// else show no match
//
let FoundPerson = findPerson("Cain", people)
match FoundPerson with
    | None -> Console.WriteLine("Not found")
    | Some(x) -> showDetails(x)

Console.ReadLine()
So, my code isn’t the cleanest but it did teach me a bit more F#. The area that I learnt about was the option keyword. The challenge being, if a match of the name isn’t found – and if a name is found but the person doesn’t have parents it should react accordingly.

I’m pretty sure I can optimize this code quite a bit more and I think I may come back to it sometime in the future and relook at it, but for now at least I was able to achieve what I wanted.. and my brain has gone just that wee little bit more functional.
