---
layout: post
title: C# Extension Methods
tags: 
category: General
---
This evening I thought I would look into something that I have been meaning to look into for a while, but just haven’t given the time of day. Initially I wanted to brush up on some LINQ, but after going over the definition of LINQ, I stumbled across extension methods… I have heard of them quite a bit – but never really bothered to see what they are…

So the official MSDN explanation says the following…

“Extension methods enable you to "add" methods to existing types without creating a new derived type, recompiling, or otherwise modifying the original type.”

It then goes on to explain how these are commonly used in LINQ. That’s all great, but what exactly are they… let’s take the following scenario…

Assume you have a library that you don’t have access to the source code but you want to extend it – maybe add a few methods to it. One way you can do this is by using extension methods. Take this fictitious scenario… let’s say I have the integer class, and I want to extend it to make a method that multiplies the value by some other value.

int i = (10).MyMagicNumberMultiplier();
 

Now, int does not have this method on it, so how would I call it? One way would be to use extension methods…

Simple make a namespace with your extension classes like the following…

public static class MyExtensions 
{ 
    public static int MyMagicNumberMultiplier(this int val) 
    { 
        return val * 5; 
    } 
}
 

And there you go, you will now have an method extended onto that class. So there are a few gotcha’s – first, you need to be careful when to use these – they are really meant for when you have no control over the class yourself. Also, if the class designer for some reason wrote a new method with the same name as your extension method, that class method would take priority (as explained in section below).

The Pattern to Implement Them
The pattern for implementing an extension method is quite simple. The method needs to be static & public, you would specify a normal method type, then in parameters you would just need the “this” keyword and then the type of the object that you are wanting to extend (in this case it is int), and then a value placeholder which will expose the value of the object so that you can manipulate it within the extension method.

Can you override classes using extension methods?
As MSDN says, an extension method with the same name and signature as an interface or class method will never be called. At compile time, extension methods always have lower priority than instance methods defined in the type itself. In other words, if a type has a method named Process(int i), and you have an extension method with the same signature, the compiler will always bind to the instance method. When the compiler encounters a method invocation, it first looks for a match in the type's instance methods. If no match is found, it will search for any extension methods that are defined for the type, and bind to the first extension method that it finds. The following example demonstrates how the compiler determines which extension method or instance method to bind to.

Use them sparingly
In general MSDN recommends that you implement extension methods sparingly and only when you have to. Whenever possible, client code that must extend an existing type should do so by creating a new type derived from the existing type.

When using an extension method to extend a type whose source code you cannot change, you run the risk that a change in the implementation of the type will cause your extension method to break.

Conclusion
That all being said, extension methods seem to be a method to understand so that if you ever do get in the scenario where you need something like them, at least you know that they exist and what you can do with them.