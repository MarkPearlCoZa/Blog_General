---
layout: post
title: F# - The three most important commands as well as other F thoughts
tags: 
category: General
---
I recently watched “An Introduction to Microsoft F#” on Channel 9. I would say this is one of the best overviews of the F# language that I have seen and really puts things into perspective. I have been playing around with the basics of the language, but just didn’t get it… I don’t know if I am getting it now… but my mindset has changed. Do yourself a favour – if you want to see F# in action then watch this video.

There are a few things in the video that Luca demonstrated that I would like to make special note of… Firstly, in his presentation he ranked three keywords in order of importance. They were…

Let  
|> (Forward Pipe)  
Fun  

## Let

Let is the most important keyword in the F# language. Let does not mean “assign a value to a variable”. What Let means is “bind a value to a symbol”. This is important. Remember, a variable as we view it using our C# caps does not really exist – well at least not without explicitly declaring it. So we could have the following code…

let add x = x + 5;;
 

What we are saying in the code above is when we call the the symbol “add”, we take a value and add 5 to it and then assign that value to the add character…

## |> (Forward Pipe)

|> is the second most important keyword in F#. The |> in a sense is just a “function application in reverse”. When used with operators such as List.map, the |> operator allows you to perform the data transformations iterations in a forward-chaining, pipelined style.

So what does this mean? Basically, if you thought of the value on the left hand side being pushed into the first variable on the right hand side of the forward pipe – then you have a very useful way to “format” code…

Lets look at a typical C# example…

~~~
private static double Add5(double val)
{
    return val + 5;
}

private static double Mul2(double val)
{
    return val * 2;
}

static void Main(string[] args)
{
    double result = Add5(Mul2(10));
    Console.WriteLine(result);
    Console.ReadLine();
}
~~~

Pretty simple stuff, the value 10 is operated on by the Mul2 Method to be 20. The value 20 is then operated on by the Add5 Method to return a result of 25; The methods are starting from the inner most brackets and as they are evaluated, the result is moved out to the outer method.

The F# equivalent using the forward pipe is in my mind easier to read…

~~~
#light
open System

let add5 x = x + 5;;
let mul2 x = x * 2;;

let result  = 
    10 
    |> mul2
    |> add5

Console.WriteLine(result);
Console.ReadLine();
~~~
 
if we ignore the add2 & mul5, and jump to the |>, we have the value 10, we forward chain it to mul2, and then the result of that is then chained to the add5, returning the same result of 25.

## Fun

The Fun keyword is used to define a lambda expression (anonymous function). Lambda expressions are useful when you want to perform operations on data (lists) and want to avoid the extra work of defining a function. We have seen lambda expressions in C# for a while now… let’s look at a F# example.

Assume the code snippet above with the add5 and mul2 declarations. Let’s assume that we rather wanted to declare these operations inline. We could do something like this…

~~~
let result  = 
    10 
    |> fun x -> x * 2
    |> fun x -> x + 5
~~~
 
## Other F Thoughts
 
So we now have according to Luca the three most important keywords in F#. It is interesting… even with these simple three keywords the F# language is starting to look exciting. I think one of the biggest challenges is that if you really want to, you can write F# code iteratively, not declaratively – which negates many of the benefits of a functional language. I’m finding that when coding in F# you really need to think in a different way…
