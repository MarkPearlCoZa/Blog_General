---
layout: post
title: F# Objects – Integrating with the other .Net Languages – Part 1
tags: 
category: General
---
 

In the next few blog posts I am going to explore objects in F#.

Up to now, my dabbling in F# has really been a few liners and while I haven’t reached the point where F# is my language of preference – I am already seeing the benefits of the language when solving certain types of programming problems.

For me I believe that the F# language will be used in a silo like architecture and that the real benefit of having F# under your belt is so that you can solve problems that F# lends itself towards and then interact with other .Net languages in doing the rest. When I was still very new to the F# language I did the following post covering how to get F# & C# to talk to each other. Today I am going to use a similar approach to demonstrate the structure of F# objects when inter-operating with other languages.

Lets start with an empty F# class …

~~~
type Person() = 
    class               
    end
~~~
 

Very simple, and all we really have done is declared an object that has nothing in it. We could if we wanted to make an object that takes a constructor with parameters… the code for this would look something like this…

~~~
type Person = 
    { 
        Firstname : string 
        Lastname : string 
    } 
~~~

What’s interesting about this syntax is when you try and interop with this object from another .Net language like C# - you would see the following…

 

2010-04-22 06-32-05 PM

Not only has a constructor been created that accepts two parameters, but Firstname and Lastname are also exposed on the object. Now it’s important to keep in mind that value holders in F# are immutable by default, so you would not be able to change the value of Firstname after the construction of the object – in C# terms it has been set to readonly.

One could however explicitly state that the value holders were mutable, which would then allow you to change the values after the actual creation of the object.

~~~
type Person =
    {
        mutable Firstname : string
        mutable Lastname : string
    }
~~~
 
Something that bugged me for a while was what if I wanted to have an F# object that requires values in its constructor, but does not expose them as part of the object. After bashing my head for a few moments I came up with the following syntax – which achieves this result.

~~~
type Person(Firstname : string, Lastname : string) =     
    member v.Fullname = Firstname + " " + Lastname
~~~

What I haven’t figured out yet is what is the difference between the () & {} brackets when declaring an object.
