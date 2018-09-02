---
layout: post
title: Lazy Evaluation – Why being lazy in F# blows my mind!
tags: 
category: General
---
First of all – shout out to Peter Adams – from the feedback I have gotten from him on the last few posts of F# that I have done – my mind has just been expanded.

I did a blog post a few days ago about infinite sequences – I didn’t really understand what was going on with it, and I still don’t really get it – but I am getting closer.

In Peter’s last comment he made mention of Lazy Evaluation. I am ashamed to say that up till then I had never heard about lazy evaluation – how can evaluation be lazy? I mean, I know about lazy loading and that makes sense… but surely something is either evaluated or not! Well… a bit of reading today and I have been enlightened to a point – if you do know of any good articles explaining lazy evaluation please send them to me.

So what is lazy evaluation and why is it useful?

Lazy evaluation is a process whereby the system only computes the values needed and “ignores” the computations not needed. I’m going out on a limb here, but with this explanation in hand, imagine the following C# code…

~~~
public int CalculatedVal()
{
    int Val1 = 0;
    int Val2 = 0;

    for (int Count = 0; Count < 1000000; Count++)
    {
        Val1++;
    }
    return Val2;
}
~~~ 

Normally, even though Val1 is never needed, the system would loop 1000000 times and add 1 to the current value of Val1. Imagine if the system realized this and so just skipped this segment of code and instead did the following….

~~~
public int CalculatedVal()
{
    int Val1 = 0;
    return Val2;
}
~~~ 

A massive saving in computation and wasted effort. Now I am pretty sure it isn’t as simple as this but I think this is the basic idea. For a more detailed explanation of lazy evaluation in c#, Pedram Rezei has a wonderful post on lazy evaluation and makes some C# comparisons. I am not going to take any thunder from him by repeating everything he said since I think he did such a good job of explaining it himself.

What I am interested in though is how in F# do you tell something to have lazy evalution, and how do you know if something will be eager or lazy by looking at it.

I found this post was useful.

From reading around F# by default uses eager evaluation unless explicitly told to use lazy evaluation. One exception to this is sequences, which are lazy by default.

Now reading about lazy evaluation has helped me understand more about F# coding…

From my understanding of F# because of its declarative nature, most of the actual code you are declaring properties and rules – very little code is actually saying do this right now - but when it comes to a “do this” code section, it then evaluates and optimizes code and applies the rules.

So props to lazy evaluation and its optimizations…