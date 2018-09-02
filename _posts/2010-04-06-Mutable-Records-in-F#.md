---
layout: post
title: Mutable Records in F#
tags: 
category: General
---
I’m loving my expert F# book – today I thought I would give a post on using mutable records as covered in Chapter 4 of Expert F#.

So as they explain the simplest mutable data structures in F# are mutable records. The whole concept of things by default being immutable is a new one for me from my C# background. Anyhow… lets look at some C# code first.

~~~
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;

namespace MutableRecords
{
    public class DiscreteEventCounter
    {
        public int Total { get; set; }
        public int Positive { get; set; }
        public string Name { get; private set; }

        public DiscreteEventCounter(string name)
        {
            Name = name;
        }
    }

    class Program
    {
        private static void recordEvent(DiscreteEventCounter s, bool isPositive)
        {
            s.Total += 1;
            if (isPositive) s.Positive += 1;
        }

        private static void reportStatus (DiscreteEventCounter s)
        {
            Console.WriteLine("We have {0} {1} out of {2}", s.Positive, s.Name, s.Total);
        }


        static void Main(string[] args)
        {
            var longCounter = new DiscreteEventCounter("My Discrete Counter");
            recordEvent(longCounter, true);
            recordEvent(longCounter, true);
            reportStatus(longCounter);
            Console.ReadLine();
        }
    }
}
~~~

Quite simple, we have a class that has a few values. We instantiate an instance of the class and perform increments etc on the instance. Now lets look at an equivalent F# sample.

~~~
namespace EncapsulationNS
module Module1 =
open System

type DiscreteEventCounter =
    { 
        mutable Total : int
        mutable Positive : int
        Name : string
    }

let recordEvent (s: DiscreteEventCounter) isPositive =
    s.Total <- s.Total+1
    if isPositive then s.Positive <- s.Positive+1

let reportStatus (s: DiscreteEventCounter) =
    printfn "We have %d %s out of %d" s.Positive s.Name s.Total

let newCounter nm = 
    {
        Total = 0;
        Positive = 0;
        Name = nm
    }

//
// Using it...
//
let longCounter = newCounter "My Discrete Counter"
recordEvent longCounter (true)
recordEvent longCounter (true)
reportStatus longCounter
System.Console.ReadLine()
~~~

Notice in the type declaration of the DiscreteEventCounter we had to explicitly declare that the total and positive value holders were mutable.

And that’s it – a very simple example of mutable types.