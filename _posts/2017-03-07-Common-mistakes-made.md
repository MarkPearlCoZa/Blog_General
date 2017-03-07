---
layout: post
title: Common mistakes I've seen in .Net Projects
tags: Code
category: General
---

# Separate Domain from Presentation Logic

Keep domain classes separate from GUI classes. The larger the system, the more clear the separation should be. 

# Strucutre solution to reveal domain intent

The structure of the solution should reveal the domain that the system is used in instead of the technologies it will leverage.

# Abstract collections

If a method return's a collection, make it return the most abstract instance of the collection. 

Enumerables > ReadOnly > List 

# Remove unnecessary comments

Prefer naming things to reveal intent than using comments. Whenever there is a comment question its existance and what value it adds

# Remove regions

Regions hide complexity, avoid them

# Replace nested conditionals with guard clauses

~~~
public bool doSomething(DataStream stream)
{
    if (stream != null)
    {
        if (!stream..GetFrequency().Equals(0))
        {
            if (stream.IsInUse)
            {
                return true;
            }
        }
    }
    return false;
}
~~~

Rather flatten it to...

~~~
public bool doSomething(DataStreamDecoder decoder)
{
    if (decoder == null) return false;
    if (decoder.GetFrequency().Equals(0)) return false;
    if (!decoder.IsInUse) return false;

    return true;
}
~~~

# Avoid Large Methods

Large methods are an indication that the method is doing too much or has too many responsibilities. Large methods should be broken down into smaller more focussed methods with self-explaining names.

# Avoid Public Static Classes

* Hard to isolate from where they are being consumed
* Tight coupling
* Inhibit Polymorphism
* Cannot be defined via interfaces
* Encourage large utility classes

* Look at extension methods if it is generic, else make it an instance class and inject via constructor 
