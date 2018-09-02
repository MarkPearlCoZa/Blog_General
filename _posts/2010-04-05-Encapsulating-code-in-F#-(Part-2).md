---
layout: post
title: Encapsulating code in F# (Part 2)
tags: 
category: General
---
In part one of this series I showed an example of encapsulation within a local definition. This is useful to know so that you are aware of the scope of value holders etc. but what I am more interested in is encapsulation with regards to generating useful F# code libraries in .Net, this is done by using Namespaces and Modules.

Lets have a look at some C# code first…

~~~
using System;
namespace EncapsulationNS
{
    public class EncapsulationCLS
    {
        public static void TestMethod()
        {
            Console.WriteLine("Hello");
        }
    }
}
~~~

Pretty simple stuff… now the F# equivalent….

~~~
namespace EncapsulationNS
module EncapsulationMDL =
    
let TestFunction = 
    System.Console.WriteLine("Hello")
    ()
~~~
 
Even easier… lets look at some specifics about F# namespaces…

Namespaces are open. meaning you can have multiple source files and assemblies can contribute to the same namespace.
So, Namespaces are a great way to group modules together, so the question needs to be asked, what role do modules play. For me, the F# module is in many ways similar to the vb6 days of modules. In vb6 modules were separate files and simply allowed us to group certain methods together. I find it easier to visualize F# modules this way than to compare them to the C# classes. However that being said one is not restricted to one module per file – there is flexibility to have multiple modules in one code file however with my limited F# experience I would still recommend using the file as the standard level of separating modules as it is very easy to then find your way around a solution.

An important note about interop with F# and other .Net languages. I wrote a blog post a while back about a very basic F# to C# interop.

If I were to reference an F# library in a C# project (for instance ‘TestFunction’), in C# it would show this method as a static method call, meaning I would not have to instantiate an instance of the module.
