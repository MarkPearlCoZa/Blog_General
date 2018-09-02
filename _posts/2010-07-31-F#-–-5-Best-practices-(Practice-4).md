---
layout: post
title: F# – 5 Best practices (Practice 4)
tags: 
category: General
---
“prefer active patterns over multiple when guards”

In line with my previous posts on 5 best practices for F# from Daniel Mohl’s slideshow, over the last few days I have been learning about active patterns. The exact best practice is to prefer active patterns over multiple “when” guards during pattern matching and in this post I am going to try and compare the two techniques and then also explain some of the basics of active patterns and why it is called active.

Now before I go any further, let me just state once again… what I am loving about F# is at every turn of the corner there is something new that I have not heard about and once again I find myself scratching my head while going through these best practices asking myself what on earth is pattern matching, and what is an active pattern?

Pattern Matching Syntax

Before we go into the specific types of active patterns, lets look at the general syntax for pattern matching…

match expr with
    | pat1 -> result1
    | pat2 -> result2
    | _ -> defaultResult
 

each “|” defines a condition. (We call the | a banana clip)
-> means if the condition is true, return the value
_ is default and matches anything
The following code illustrates this syntax…

let Greeting name = 
    match name with
    | "Joe" | "Bob" | "Ray" -> "Hello"
    | "Miguel" | "Jose" -> "Hola"
    | _ -> "Don't know what to say"

Active Patterns

With active patterns I had an initial look at MSDN to help shed a bit of light on the subject…

Active patterns enable you to define named partitions that subdivide input data, so that you can use these names in a pattern matching expression just as you would for a discriminated union. You can use active patterns to decompose data in a customized manner for each partition.

Okay, so MSDN explains what active patterns are technically and even gives one or two examples… but does not explain why an active pattern would be a better approach than when guards, so I decided to take the example on MSDN and illustrate it both ways, first using when guards, and then using active patterns, to see if I could see any reason for the best practice…

Comparing When Guard Code to Pattern Matching

When Guard Example…

let TestNumberWG input =
   match input with
   | var1 when var1 % 2 = 0 -> printfn "%d is even" input
   | _ -> printfn "%d is odd" input
 

Now the above example is quite simple, given a number “input”, it prints to the console whether the number is odd or even… as far as I am concerned, using the when guard is acceptable, but not the easiest read, especially if there where multiple constraints… now lets compare the above approach to the active pattern approach as illustrated in MSDN…

Active Pattern Matching Example…

let (|Even|Odd|) input = if input % 2 = 0 then Even else Odd

let TestNumberAP input =
   match input with
   | Even -> printfn "%d is even" input
   | Odd -> printfn "%d is odd" input

So not to different from the when guard example, but definitely easier to read. By using the active pattern the match statement is definitely clearer, and more componentized. But is well formatted and clean syntax the only benefit of active patterns? No, it goes further than that.

In Don Syme’s “Expert F#” book he explains that Active Patterns is also a way of converting the same data to many views.

Let’s look at another example, let’s say we have a numerical value that we want to view as a written string… i.e. 1 would be “one”. Using active patterns we could do the following…

let (|ToNumber|) x = 
    match x with
    | "one"   -> 1
    | "two"   -> 2    
    | _       -> -1
let (ToNumber myNumber) = "one"
 

The initial pattern matching has already been shown and should be relatively easy to understand, but the code below the pattern matching is surprising.

let (ToNumber myNumber) = "one"

In effect what we have said here is create a value holder myNumber that has the value 1 but we never explicitly said it should be one – instead we used the active pattern ToNumber to convert the “one” view to the actual “1” value. Very cool…

Why is it called “Active”

The concept of pattern matching is not to new to me. In many ways it reminds me of the Switch Case statement from C#. Where I feel F# has one up on the C# switch statement is the “active” word.

In C# the following code would be acceptable…

private static string TestSwitch()
{
    string input = Console.ReadLine();

    switch (input)
    {
        case "1": return "One";                
        default: return "Unknown";
    }
}

However, as soon as you tried the following in C# you would get an error…

private static string TestSwitch()
{
    string input = Console.ReadLine();

    switch (input)
    {
        case "1".ToUpper(): return "One";                
        default: return "Unknown";
    }
}
 

That’s because it is expecting a constant value from “1”, and a method call is not guaranteed to be constant, besides the fact that in this instance we know it will be constant.

F# on the other hand does not have an issue with handling something like this because it can apply an “active” pattern.

let (|Upper|) (x:string) = x.ToUpper()
 let TesString (input:string) = 
    match input with
        | Upper "1" -> "One"
        | _ -> "Unknown"
 

When F# needs to match values against patterns, it doesn’t look at the contents of the values directly, but instead runs a function as part of pattern matching. Thus it is active pattern matching.

Different Categories of Pattern Matching

After looking at the examples on MSDN, I came across Chris Smith’s site which had a great blog post on the subject. It pretty much covered all the basics with some code examples of each type of active pattern matching…

In Chris’s post he outlines 4 active patterns…

Single Case
Multi-Case
Partial
Parameterized
At first I didn’t want to repeat Chris’s content, but since this blog post is primarily for me to learn I tried my own code examples of each pattern just to learn and understand them better…

Single Case Active Pattern

With the single case active pattern all we are trying to do is convert the input into something different. I am going to use a fairly obtuse example, but try and explain it further so it makes sense…

let (|Square|) (x:int) =  x*x

let IsSquareOf9 input = match input with
    | Square 9 -> true    
    | _ -> false

In the above code snippet I have declared an active pattern that returns the square of “x”. 
In the IsSquareOf9 function, I am matching the square of the “input” value with the value 9. It is a bit of a swap around in the order of reading, at first glance I would have thought that what the code was doing was comparing the “input” value with the Square of 9, but it is not. What it is really doing is squaring value “input” and then checking to see if it equals 9… make sense?

So, up to this point while the single case active pattern is interesting, I could have made equivalent with when guards with no real visible advantage…

let ConvertToNumber x =
    match x with 
        | var when var = "one" -> 1
        | var when var = "two" -> 2
        | _ -> -1

let myNumber = (ConvertToNumber "one")
 

Let’ss now look at a similar example to the one given in MSDN for odd and even using Multi-Case Active Patterns.

Multi-Case Active Patterns

So I can see a use for multi case ap’s. First of all, I think they make the code more readable…. lets look at an example…

let (|NoLetters|ShorterThan5Letters|LongerThan5Letters|) (x:string) =
    if (x.Length = 0) then NoLetters
    elif (x.Length > 5) then LongerThan5Letters    
    else ShorterThan5Letters

let HowLongIsText x:string =
    match x with
        | LongerThan5Letters -> "Long Text"
        | ShorterThan5Letters -> "Short Text"
        | NoLetters -> "Empty Text"

This above sample in my opinion definitely beats the when guards equivalent in terms of readability…

Now something important to note about multi-case ap’s… they cannot go over 7 possibilities – as you as you go over 7 it wont compile.

If you are going to go over the magic number 7 you need to approach the problem in a different way. One way is to use partial active patterns…

Partial Active Patterns

Partial Active Patterns have a slightly different format… take the following code sample…

let (|Empty|_|) (x:string) =
    if (x.Length = 0) then Some()
    else None
 

With this type of active pattern it either matches the pattern or is “something else”… if it is a match, it returns Some(), if it is not a match, it returns None.

By using partial active patterns  you can have more than 7 alternatives.. while in the code snippet below I am only showing 3 comparisons, I could extend it almost indefinitely.

let (|Empty|_|) (x:string) =
    if (x.Length = 0) then Some()    
    else None

let (|Fiver|_|) (x:string) =
    if (x.Length = 5) then Some()    
    else None

let (|Tener|_|) (x:string) =
    if (x.Length = 10) then Some()    
    else None    

let CompareString input:string =
    match input with    
        | Empty -> "Empty"
        | Fiver -> "Five Letters"
        | Tener -> "Ten Letters"
        | _ -> "No Match"
 

Once again I can definitely see the use for partial active patterns. I could extend the above example by using the boolean operations like the and operator to do something like this…

let (|Upper|_|) (x:string) =
    if (x = x.ToUpper()) then Some()    
    else None    

let CompareString input:string =
    match input with    
        | Empty         -> "Empty"
        | Fiver & Upper -> "Five Upper Letters"
        | Fiver         -> "Five Letters"        
        | Tener         -> "Ten Letters"
        | _ -> "No Match"

Parameterized Active Patterns

Finally, there are Parameterized Active Patterns… as Chris explains, a Parameterized Active Pattern is simply an active pattern that takes additional parameters. In the above partial active pattern example, I had declared a Fiver & a Tener, this could be shortened to a single parameterized active pattern.

let (|IsXLeters|_|) x (input:string) = 
    if input.Length = x then Some() 
    else None

let CompareString x =
    match x with
        | IsXLeters 0 -> "Empty"
        | IsXLeters 5 -> "Five Letters"
        | IsXLeters 10 -> "Ten Letters"
        | _ -> "No Match"
 

Conclusion

So, this blog post has covered the basics of active patterns and why they are possibly better than when guards. Initially I thought active patterns were just switch statements, but after examining the code examples it is obvious that active patterns offer a lot more power than just a simple comparison. Obviously I am still very new to this language so I may have missed out some aspects of active patterns, but if there is something, or if I have got something wrong, please add a comment so I can increase my knowledge base.
