---
layout: post
title: Nails vs Screws - C# List vs Dictionary
tags: 
category: General
---
# General

This may sound like a typical noob statement, but I’m finding out in a very real way that just because you have a solution to a problem, doesn’t necessarily mean it is the best solution. This was reiterated to me when a friend of mine suggested I look at using Dictionaries instead of Lists for a particular problem – he was right, I have always just assumed that because lists solved my problem I did not need to look elsewhere. So my new manifesto to counter this ageless problem is as follows…

Look for a solution that will logically work
Once you have a solution look for possible alternatives
Decide why your current solution is the best approach compared to the alternatives
If it is.. use it till something better comes along, if it isnt…. change
What’s the difference between Lists & Dictionaries

Both lists and dictionaries are used to store collections of data. Assume we had the following declarations…

~~~
var dic = new Dictionary<string, long>();
var lst = new List<long>();
long data;
~~~
 

With a list, you simply add the item to the list and it will add the item to the end of the list.

~~~
lst.Add(data);
~~~

With a dictionary, you need to specify some sort of key and the data you want to add so that it can be uniquely identified.

~~~
dic.Add(uniquekey, data);
~~~
 

Because with a dictionary you now have unique identifier, in the background they provide all sort’s of optimized algorithms to find your associated data. What this means is that if you are wanting to access your data it is a lot faster than a List.

So when is it appropriate to use either class?

For me, if I can guarantee that each item in my collection will have a unique identifier, then I will use Dictionaries instead of Lists as there is a considerable performance benefit when accessing each data item. If I cannot make this sort of guarantee, then by default I will use a list.

I know this is all really basic, and I hope I haven’t missed some fundamental principle… If anyone would like to add their 2 cents, please feel free to do so…