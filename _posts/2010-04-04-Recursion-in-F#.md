---
layout: post
title: Recursion in F#
tags: 
category: General
---
Things are slowly coming together – I was able to look at a bit of F# code and intuitively know what it was going to do (yay)… So today I saw a blog post by Bob Palmer on Fibonacci numbers in F# which inspired me to look at bit into recursion.

First the C# example…

~~~
class Program
{
    public static void CountDown(int n)
    {
        switch (n)
        {
            case 0: Console.WriteLine("End of Count");
                    break;

            default:
                    Console.WriteLine(n);
                    CountDown(n-1);
                break;
        }
    }

    static void Main(string[] args)
    {
        CountDown(10);
        Console.ReadLine();
    }
}
~~~ 

In F#, the equivalent would look something like this…

~~~
open System

let rec CountDown n =
    match n with
        | 0 -> Console.WriteLine("End of Count");
        | n -> Console.WriteLine(n); CountDown (n-1);
                    
CountDown 10
Console.ReadLine()
~~~

Pretty simple stuff. With F# you when making recursive calls you need to explicitly declare that the function is recursive with the “rec” keyword. Otherwise the code is pretty easy to read and self explanatory.