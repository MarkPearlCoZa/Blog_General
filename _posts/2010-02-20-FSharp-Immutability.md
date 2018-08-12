---
layout: post
title: F# Immutability
tags: 
category: General
---
I was reading a blog post by [Chris Smith](http://blogs.msdn.com/chrsmith/archive/2008/05/09/f-in-20-minutes-part-ii.aspx) on F#. Firstly, a really good blog post and well worth a read if you are interested in learning the basics of F# as I am.

The first thing that struck me about F# and Chris’s blog was his explanation that in F# there typically wasn’t such a thing as a variable – because of the immutability of the “value” holders.

That doesn’t mean that we don’t get mutable value holders – they are available, but they need to be explicitly declared.

Have a look at the F# code below…

~~~
let x = "the original value";
printfn "x's value is '%s'" x;
~~~
 
If I were to try and change the value holder x, doing something like this…

~~~
x <- "the new one.";
~~~

I would get an error stating that the value was not mutable. To get a mutable value, I would need to declare it explicitly like this…

~~~
let mutable x = "the original value";
~~~
 
And then the value would be allowed to be changed.

After this simple explanation of a really basic principle of F#, I am beginning to get excited to learn what other differences there are in this language!
