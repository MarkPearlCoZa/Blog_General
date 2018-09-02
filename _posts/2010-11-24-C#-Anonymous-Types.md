---
layout: post
title: C# Anonymous Types
tags: 
category: General
---
Another nifty little feature in C# is anonymous types. Anonymous types allow a “short cut” in creating an object with a set of properties. They seem to be used mainly in LINQ, however we will make up a scenario here.

Assume you have a situation where you want to group a whole bunch of information, but you don’t want to go to the effort of defining a class or a structure. You can get around this by declaring an anonymous type.

Lets have a look at some code…

var person = new { Name = "Mark", Surname = "Pearl" };
 

What you have done above is create an object of type (unknown) that has two properties, Name and Surname. You don’t even need to explicitly declare the property names, the following code will create objects with the same names, because if you do not include the explicit name declaration, the property takes on the name of the variable being passed in. For instance…

string name = "Mark";
string surname = "Pearl";
var person2 = new { name, surname};            
 

To read more about anonymous types follow the MSDN link.