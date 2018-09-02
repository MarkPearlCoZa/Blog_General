---
layout: post
title: F# Objects – Integration with the other .Net Languages – Part 2
tags: 
category: General
---
So in part one of my posting I covered the real basics of object creation. Today I will hopefully dig a little deeper…

My expert F# book brings up an interesting point – properties in F# are just syntactic sugar for method calls. This makes sense… for instance assume I had the following object with the property exposed called Firstname.

~~~
type Person(Firstname : string, Lastname : string) =     
    member v.Firstname = Firstname
~~~

I could extend the Firstname property with the following code and everything would be hunky dory…

~~~
type Person(Firstname : string, Lastname : string) =     
    member v.Firstname = 
        Console.WriteLine("Side Effect")
        Firstname
~~~
 

All that this would do is each time I use the property Firstname, I would see the side effect printed to the screen saying “Side Effect”.

Member methods have a very similar look & feel to properties, in fact the only difference really is that you declare that parameters are being passed in.

~~~
type Person(Firstname : string, Lastname : string) =     
    member v.FullName(middleName) = Firstname + " " + middleName +  " " + Lastname
~~~
 
In the code above, FullName requires the parameter middleName, and if viewed from another project in C# would show as a method and not a property.

Precomputation Optimizations

Okay, so something that is obvious once you think of it but that poses an interesting side effect of mutable value holders is pre-computation of results.

All it is, is a slight difference in code but can result in quite a huge saving in performance. Basically pre-computation means you would not need to compute a value every time a method is called – but could perform the computation at the creation of the object (I hope I have got it right). In a way I battle to differentiate this from lazy evaluation but I will show an example to explain the principle.

Let me try and show an example to illustrate the principle… assume the following F# module

~~~
namespace myNamespace
open System

module myMod =
    let Add val1 val2 =
        Console.WriteLine("Compute")
        val1 + val2

    type MathPrecompute(val1 : int, val2 : int) =     
        let precomputedsum = Add val1 val2
        member v.Sum =         
            precomputedsum
    

    type MathNormalCompute(val1 : int, val2 : int) =         
        member v.Sum = Add val1 val2
~~~

Now assume you have a C# console app that makes use of the objects with code similar to the following…

~~~
using System;
using myNamespace;

namespace CSharpTest
{
    class Program
    {
        static void Main(string[] args)
        {

            Console.WriteLine("Constructing Objects");
            var myObj1 = new myMod.MathNormalCompute(10, 11);
            var myObj2 = new myMod.MathPrecompute(10, 11);
            Console.WriteLine("");

            Console.WriteLine("Normal Compute Sum...");
            Console.WriteLine(myObj1.Sum);
            Console.WriteLine(myObj1.Sum);
            Console.WriteLine(myObj1.Sum);
            Console.WriteLine("");
            
            Console.WriteLine("Pre Compute Sum...");
            Console.WriteLine(myObj2.Sum);
            Console.WriteLine(myObj2.Sum);
            Console.WriteLine(myObj2.Sum);
            
            Console.ReadKey();
            
        }
    }
}
~~~

The output when running the console application would be as follows….

2010-04-29 06-31-03 PM

You will notice with the normal compute object that the system would call the Add function every time the method was called. With the Precompute object it only called the compute method when the object was created. Subtle, but something that could lead to major performance benefits.

So… this post has gone off in a slight tangent but still related to F# objects.
