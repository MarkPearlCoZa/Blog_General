---
layout: post
title: F# – Put that in your pipe and smoke it |>
tags: 
category: General
---
So I must admit, the first time I saw it I scratched my head and thought to myself, why will I ever use that? Several months since then and now I love the Forward Pipe (FP) in F#.

Why?

For me, the the FP makes me think of a problem in a different way. In C# when I attempt to solve I problem I typically break it down in steps, once I have reached the end result I have my smallest step, and then I work my methods backwards so that I can get back to the original input… in a very real way it makes me look and think of a problem in a bottom up approach… whereas I often think as humans we solve problems from a top down approach.

Now.. I am no psychologist, but how often when you ask directions from someone do they start by giving you the end destination and then give you directions from there back to where you are? It would be extremely hard to find the place… Yet in many ways that’s how I have solved problems in the past with C# and other languages and it almost seems like the languages write the solution in that way as well.

For instance, take my very contrived C# example for solving the following problem…

Take the value 10, get the square root of it and then round it off…

Math.Round(Math.Sqrt(10)); 

Now look at how the syntax was written – it seems to be out of sequence to how the problem was originally written in English… Take the same problem and using the |> operator in F# you see it is expressed in a totally different sequence of declaring it… almost identical to how the problem was phrased in English

10 |> float |> Math.Sqrt |> Math.Round
 

So what prompted this post? I have been hating type casting of numbers in F# up to now… it just seemed messy? Take for example the following code used to get the upper bound of a prime number…

let upperBound n:int =
    let f = float(n)
    let ln x = Math.Log x
    int(f*(ln f) + f*(ln (ln f)))

With the forward pipe this seems to read in my mind at least as more natural

let upperBound n:int =
    let f = n |> float
    let ln x = Math.Log x
    f*(ln f) + f*(ln (ln f)) |> int
 

So, I love the forward pipe! Absolutely love it!
