---
layout: post
title: F# – order of code execution, values and functions again…
tags: 
category: General
---
I had the following code snippet…

~~~
#light

open System

let ExeC =
    printfn "c"
    3

let ExeB b = 
    printfn "b"
    2

let ExeA = 
    printfn "a"
    1

printfn "Example %d " ExeA
printfn "Example %d " (ExeB 1)
printfn "Example %d " ExeC


Console.ReadLine()
~~~

With the output as follows…

c 
a 
Example 1 
b 
Example 2 
Example 3

Initially the execution of the code seemed unusual… up to now I would have expected ExeC, ExeB & ExeA to all be functions, but a previous comment from Brian indicated that there was a difference.

StackOverflow to the rescue and I got some feedback from Tim Robinson explaining that ExeA & ExeC were not functions, but single values (with side effects). This would make sense. Tim went on to suggest that if I wanted ExeA & ExeC to be functions I should declare them slightly differently… like this…

#light
open System

let ExeC () =
    printfn "c"
    3

let ExeB b = 
    printfn "b"
    2

let ExeA () = 
    printfn "a"
    1

printfn "Example %d " (ExeA ())
printfn "Example %d " (ExeB 1)
printfn "Example %d " (ExeC ())

Which would give the following output, which is what I originally expected…

a 
Example 1 
b 
Example 2 
c 
Example 3

To be honest, it seems like such a minute change in code to achieve such a different result. Ironically up to today I realize that ExeA & ExeC were value holders – even though I had read it in several places, because of the side effects, which seemed misleading.

If I now understand what is going on, then the following code…

#light
open System

let ExeC = lazy(printfn "c"; 3)
let ExeB (b) = lazy(printfn "b"; 2)
let ExeA = lazy(printfn "a"; 1)    

printfn "Example %d " (ExeA ).Value
printfn "Example %d " (ExeB (1)).Value
printfn "Example %d " (ExeC ).Value

would be equivalent to what Tim showed me.
