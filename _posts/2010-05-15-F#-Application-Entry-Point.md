---
layout: post
title: F# Application Entry Point
tags: 
category: General
---
Up to now I have been looking at F# for modular solutions, but have never considered writing an end to end application. Today I was wondering how one would even start to write an end to end application and realized that I didn’t even know where the entry point is for an F# application.

After browsing MSDN a bit I got a basic example of a F# application with an entry point

~~~
[<EntryPoint>]
let main args =
    printfn "Arguments passed to function : %A" args
    // Return 0. This indicates success.
    0
~~~

Pretty simple stuff… but what happens when you have a few modules in a program – so I created a F# project with two modules and a main module as illustrated in the image below…

2010-05-15 05-04-48 PM

When I try to compile my program I get a build error…

A function labeled with the 'EntryPointAttribute' attribute must be the last declaration in the last file in the compilation sequence, and can only be used when compiling to a .exe…

What does this mean? After some more reading I discovered that the Program.fs needs to be the last file in the F# application – the order of the files in a F# solution are important. How do I move a source file up or down? I tried dragging the Program.fs file below ModuleB.fs but it wouldn’t allow me to. Then I thought to right click on a source file and got the following menu.

2010-05-15 05-08-20 PM


Wala… to move the source file to the bottom of the solution you can select the “Move Up” or “Move Down” option.

2010-05-15 05-12-18 PM

Now that I got this right I decided to put some code in ModuleA & ModuleB and I have the start of a basic application structure.

ModuleA Code

namespace MyApp
    module ModuleA =            
        let PrintModuleA =         
            printf "hello a \n"
            ()
 

ModuleB Code

namespace MyApp
    module ModuleB =            
        let PrintModuleB =         
            printf "hello b \n"
            ()
 

Program Code

// Learn more about F# at http://fsharp.net
#light
namespace MyApp
module Main =
    open System
        [<EntryPoint>]
        let main args =         
            ModuleA.PrintModuleA                                      
            let endofapp = Console.ReadKey()
            0
