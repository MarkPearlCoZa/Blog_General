---
layout: post
title: A solid example of the difference between a Functional and Iterative Language. F# style..
tags: 
category: General
---
A few months ago I had a really frustrating debate with my younger brother. He had come up to JHB to come for a visit and we decided to talk about programming. Of course I thought I would put a good pitch in for F#, but just couldn’t seem to do it any justice.

Eventually his point was as follows - “What really is the difference between declaring a functional solution vs an iterative solution. Sure, in F# you have something like the Seq.map function, but isn’t it just a shorthand for a for loop or something like that – isnt it just syntactical sugar?”

Of course he was wrong, but at the time I just battled to give him a concrete and yet simple enough example of how a functional solution is at a higher level than an iterative solution.

Then a few weeks ago I found a classic example which I think might illustrate the point a bit better. It all happened while I was looking into tail-recursive functions through reflector.

Lets say you have a recursive solution in F# that looks like the following…

let rec fooNonTail n = 
    match n with 
    | 0 -> 0 
    | _ -> 2 + fooNonTail (n-1) 
 

If you were to go and look at the equivalent C# code generated via reflector (by examining the IL code) you would see something like the following…

public static int fooNonTail(int n)
{
    switch (n)
    {
        case 0:
            return 0;
    }
    return (2 + fooNonTail(n - 1));
}
 

That pretty much makes sense… we defined a recursive function in F#, and the IL came out as a recursive function in C#…

Now it gets interesting… let’s say instead of having the original F# fooNonTail function we replaced it with a tail recursive function that looked like the following in F#…

 

let fooTailRec n = 
    let rec innerfooTailRec acc n =         
        match n with 
        | 0 when n <=0 -> acc 
        | _ -> innerfooTailRec (acc+2) (n-1) 
    innerfooTailRec 0 n 

Not to much of a difference from the fooNonTail function. We have moved things around a bit, but in essence it is still a recursive function.

This is where the fun begins… suddenly it gets interesting when we look at what has happened behind the scenes in the IL code.

Instead of getting a similar method to the first IL code we have to look around a bit more for the actual implementation, and when you find it, it looks something like the following…

public override int Invoke(int acc, int n)
{
    while (true)
    {
        switch (n)
        {
            case 0:
            {
                int num = n;
                int num2 = 0;
                if (num > num2)
                {
                    break;
                }
                return acc;
            }
        }
        n--;
        acc += 2;
    }
}
 

That’s not recursive at all??? What happened?

What has happened here is somewhere, something recognized that instead of expressing the function in IL code as recursive, it could instead convert it to a normal iterative while loop… which has several operational/performance benefits.

To me that’s amazing and is a classic example of part of the abstraction layer that a functional language has over an iterative language. It works at just a slightly higher level. In this situation, because I was “solving” the problem, instead of telling the compiler how to iterate each step to get to a solution, when the compiler came across a situation where it recognized it could reformat for optimizations, it did it behind the scenes and wala…

So while this is not a complete blog post on the power of functional languages and F# in particular, I believe it at least illustrates that F# works at a slightly higher level than C# (iteratively) and that it is well worth examining the IL code in reflector to see exactly how your F# applications are translated.

What does worry me a bit about such an example is that it is subtle… meaning the optimization could easily be missed unless you kept an eye out for it.

Well, I look forward to your comments / crits if you have anything to add… or examples to give - just keep it nice ;-)