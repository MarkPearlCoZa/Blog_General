---
layout: post
title: Encapsulating code in F# (Part 1)
tags: 
category: General
---
 

I have been looking at F# for a while now and seem a few really interesting samples and snippets on howto’s. This has been great to see the basic outline of the language and the possibilities, however a nagging question in the back of my mind has been what does an F# project look like? How do I group code in F# so that it can be modularized and brought in and out of a project easily?

My Expert F# book has an entire chapter (7) dedicated to this and after browsing the other chapters of the book I decided that this topic was something I really wanted to know more about now!

Because of my C# background I keep trying to think in F# of objects. So to try and get a clearer idea of how to do things the F# way I am first going to take a very simplified C# example and try to “translate” it.

~~~
using System;

namespace ConsoleApplication1
{
    namespace ExampleOfEncapsulationInCSharp
    {
        class Program
        {
            static void EncapsulatedVariableInAMethod()
            {
                int count = 10;
                Console.WriteLine(count);
            }

            static void Main(string[] args)
            {
                EncapsulatedVariableInAMethod();
                Console.ReadLine();
            }
        }
    }
}
~~~

From the above example the count integer is encapsulated within EncapsulatedVariableInAMethod method. You couldn’t access the count variable from outside the scope of its parent method but have full access to it within the method.

Lets look at my F# equivalent…

~~~
open System

let EncapsulatedVariableInAMethod =   
    let count = 10    
    Console.WriteLine(count)
    ()   
            
EncapsulatedVariableInAMethod
Console.ReadLine()
~~~
 

Now, when I first attempted to write the F# code I got stuck… I didn’t have the Console.WriteLine calls but had the following…

~~~
open System

let EncapsulatedVariableInAMethod =   
    let count = 10            
            
EncapsulatedVariableInAMethod
Console.ReadLine()
~~~
 

The compiler didn’t like the let before the count = 10. This is because every F# expression must evaluate to a value. If I did not want to make the Console call, I would still need to evaluate the expression to something – and for this reason the Unit Type is provided. I could have done something like….

~~~
open System

let EncapsulatedVariableInAMethod =   
    let count = 10            
    ()
            
EncapsulatedVariableInAMethod
Console.ReadLine()
~~~
 

Which the compiler would be happy with…
