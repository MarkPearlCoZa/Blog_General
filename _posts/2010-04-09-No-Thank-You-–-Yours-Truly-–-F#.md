---
layout: post
title: No Thank You – Yours Truly – F#
tags: 
category: General
---
I am plodding along with my F# book. I have reached the part where I know enough about the syntax of the language to understand something if I read it – but not enough about the language to be productive and write something useful. A bit of a frustrating place to be.

Needless to say when you are in this state of mind – you end up paging mindlessly through chapters of my F# book with no real incentive to learn anything until you hit “Exceptions”.

Raising an exception explicitly

So lets look at raising an exception explicitly – in C# we would throw the exception, F# is a lot more polite instead of throwing the exception it raises it, …

(raise (System.InvalidOperationException("no thank you")))
quite simple…

Catching an Exception

So I would expect to be able to catch an exception as well – lets look at some C# code first…

~~~
try
{
    Console.WriteLine("Raise Exception");
    throw new InvalidOperationException("no thank you");
}
catch
{
    Console.WriteLine("Catch Exception and Carry on..");
}                    
Console.WriteLine("Carry on...");
Console.ReadLine();
~~~
 

The F# equivalent would go as follows…

~~~
open System;
try
    Console.WriteLine("Raise Exception")
    raise (System.InvalidOperationException("no thank you"))
with
    | _ -> Console.WriteLine("Catch Exception and Carry on..")

Console.WriteLine("Carry on...")
Console.ReadLine();
~~~
 

In F# there is a “try, with” and a “try finally”

Finally…

In F# there is a finally block however the “with” and “finally” can’t be combined.

~~~
open System;
try
    Console.WriteLine("Raise Exception")
    raise (System.InvalidOperationException("no thank you"))
finally    
    Console.WriteLine("Finally carry on...")
    Console.ReadLine()
~~~