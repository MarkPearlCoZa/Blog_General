---
layout: post
title: F# Objects – Part 3 – it’s time to overload…
tags: 
category: General
---
Okay, some basic examples of overloading in F#

Overloading Constructors

Assume you have a F# object called person…

~~~
type Person (firstname : string, lastname : string) =    
    member v.Fullname = firstname + " " + lastname    
~~~
 

This only has one constructor. To add additional constructors to the object by explicitly declaring them using the method member new.

~~~
type Person (firstname : string, lastname : string) = 
    new () = Person("Unknown", "Unknown")
    member v.Fullname = firstname + " " + lastname    
~~~
 

In the code above I added another constructor to the Person object that takes no parameters and then refers to the primary constructor. Using the same technique in the code below I have created another constructor that accepts only the firstname as a parameter to create an object.

~~~
type Person (firstname : string, lastname : string) = 
    new () = Person("Unknown", "Unknown")
    new (firstname : string) = Person(firstname, "Unknown")
    member v.Fullname = firstname + " " + lastname    
~~~
 

Overloading Operators

So, you can overload operators of objects in F# as well… let’s look at example code…

~~~
type Person(name : string) = 
    member v.name = name        
    static member (+) (person1 : Person , person2 : Person) =
        Person(person1.name + " " + person2.name)
~~~

In the code above we have overloaded the “+” operator. Whenever we add to Person objects together, it will now create a new object with the combined names…