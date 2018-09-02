---
layout: post
title: F# – 5 Best practices for F# (Practice 3)
tags: 
category: General
---
In line with Daniel Mohl’s presentation, the third best practice for F# is Tail Recursive Functions. I must admit, while I did go over recursion several years ago, I never heard (or possibly ignored) any mention of tail recursive functions… so what exactly is a tail recursive function?

I posed the question on Stack Overflow and got some great examples and responses…

Possibly the best explanation came from a post done by [Chris Smith entitled Understanding Tail Recursion](http://blogs.msdn.com/b/chrsmith/archive/2008/08/07/understanding-tail-recursion.aspx).

Basically, non tail recursive functions are exposed to the chances of running of of stack space. This is due to the stack being utilized to store the entry/return point in a function when a call is made to another function… so when you make a call from one function to another, if there is code following the call within the scope of the function, an entry is made on the stack so that when the child call is complete, the system can continue where it left off in the current stack.

Now, normally running out of stack space is not an issue with iterative coding as most programming solutions do not go to deep into sub calls, and so the size of the stack space is more than adequate. However with recursive calls where the very nature of a recursive call is to call itself possibly thousands of times, running out of stack space becomes a very real reality.

Try for instance the following code snippet…

let rec infLoop() =  1 + infLoop()

Within seconds one gets an error…

System.StackOverflowException was unhandled 
Message: An unhandled exception of type 'System.StackOverflowException' occurred in …

This is because the function is non-tail recursive and is very quickly using up the stack space to store return points...

Take another example given on Stack Overflow by Batibix…

let rec fooNonTail n = 
    match n with 
    | 0 -> 0 
    | _ -> 2 + fooNonTail (n-1) 

At first glance the code all seems fine, until you start trying larger numbers… for instance 60 000. Then suddenly the function crashes with the stack overflow error. Why? Because it is non tail recursive and so does not have sufficient space to store all the return points on the stack.

Interestingly, we can make a minor/subtle adaption to the function that will return the same result without the overflow error… we do this simply by passing an accumulator through the recursive function (which removes the necessity of storing the return point on the stack).

let fooTailRec n = 
    let rec innerfooTailRec acc n =         
        match n with 
        | 0 when n <=0 -> acc 
        | _ -> innerfooTailRec (acc+2) (n-1) 
    innerfooTailRec 0 n
 

Basically, because of this subtle change in code the function is now tail recursive – which then removes the stack overflow limit (or at least expands the range to the bounds of the primitive data type).

While I find tail recursion an interesting aspect of recursion and functional languages, and especially of F#, I can’t but help worrying that such a subtle difference in code can have such a dramatic effect, and that in an era where there are more and more developers, and the entry point to writing commercial software is lowered, the possibility of encountering this error in code could become widespread.

It would be nice if there was an easy way to identify such potential pitfalls, i.e. a compiler warning or something along those lines?
