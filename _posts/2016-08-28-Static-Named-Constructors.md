---
layout: post
title: Static Named Constructors
tags: Design Code
category: 
---

#### Constructor Overloads  

~~~
var a = new TimeSpan(5);  
var b = new TimeSpan(0, 0, 5);  
var c = new TimeSpan(0, 5, 0);  
var d = new TimeSpan(0, 0, 0, 5);  
~~~

#### Achieving the same thing with static named constructors  

~~~
var a = TimeSpan.FromTicks(5);  
var b = TimeSpan.FromSeconds(5);  
var c = TimeSpan.FromMinutes(5);  
var d = TimeSpan.FromHours(5);  
~~~

#### Key Components 

- Factory method must be public, static and return an instance of the class in which it is defined  
- Giving Static Named Constructors meaningful names removes the ambiguity that we see with normal constructor overloads  

#### References

[Cleaner Code with Static Factory Methods](http://stackify.com/static-factory-methods/)  
