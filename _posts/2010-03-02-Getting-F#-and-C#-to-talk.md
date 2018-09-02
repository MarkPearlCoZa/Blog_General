---
layout: post
title: Getting F# and C# to talk
tags: 
category: General
---
So… I am a C# coder at heart, but F# is starting to fascinate me. Today I thought I would try and figure out the basics of getting the two languages to talk to each other.

From what I could tell on Stack Overflow, at least for now there will not be any Windows Forms / WPF exposed to F# (it is possible, but I am lazy and like VS to do as much as possible). Which leaves me thinking, where will I use F#.

I can immediately see a use for it in the Business Layer of my applications – which would mean that I would somehow have to figure out how to get F# and C# to play nice.

First Scenario – How do I pass data between F# and C#.

So I did the following. Made one solution with two projects in it (1 C# Console – which is my startup project, and added a F# library project to the solution).

I then added the F# library project as a reference to my C# project – All pretty standard stuff.

I then wrote the following code in a F# file…

// Learn more about F# at http://fsharp.net

~~~
namespace MyFSharpLibrary

type User =
    { 
        Name:string
        Age:int
    }
~~~

Now I go to my C# Console Project and add the following code…

~~~
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using MyFSharpLibrary;

namespace ConsoleApplication1
{
    class Program
    {
        static void Main(string[] args)
        {
            var test = new User("Mark", 10);
            Console.WriteLine(test.Name);
            Console.ReadLine();
        }
    }
}
~~~

And it works! C# sees my F# type and I can create it etc. So this is the very basics… but at least it is a starting point! If you are looking for a good reference which goes a lot more in depth then check out this post by Matthew Cochran.
