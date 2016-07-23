---
layout: post
title: The one line method
tags: Misc, Code
category: General
---
In my new team I recently had a chance for an interesting code discussion. It is something I've been wanting to write about for a while, a practice I've been applying to my code that I find many other developers don't agree with or find strange, and being new to this team I've been reminded that this is something I want to write about. I call it the "one line method" practice.

To illustrate where I apply the one line method practice let me show some sample C# code. In the code sample we have three collections. We want to take the values of each collection and put it into 3 strings that containt concatenated comma separated values. We do it as follows...

~~~
var approvedIds = new List<string>();
var rejectedIds = new List<string>();
var unknownIds = new List<string>();

...
// Populate id's and do some work on them...
...

var approved = String.Join(",", approvedIds);
var rejected = String.Join(",", rejectedIds);
var unknown = String.Join(",", unknownIds);
~~~

Everything looks great. In terms of desired values, everything is being generated correctly. However, at this point I do a further refactoring as follows:

~~~
public static void Main(string[] args)
{
 var approvedIds = new List<string>();
 var rejectedIds = new List<string>();
 var unknownIds = new List<string>();

...
// Populate id's and do some work on them...
...

 var approved = GenerateCommaSeparatedFrom(approvedIds);
 var rejected = GenerateCommaSeparatedFrom(rejectedIds);
 var unknown = GenerateCommaSeparatedFrom(unknownIds);
}

public static string GenerateCommaSeparatedFrom(IEnumerable<string> values){
 return String.Join(",", values);
}
~~~

So why pull out the work that makes the comma separated string into another method? 

For me there are two main motivators. The overarching principle in programming systems in the business space is writing code that is maintainable. The most maintainable code is the code that is easily readable (write once, read many times). For me, pulling the "work" into a separate method increases the readability - those reading my code can see that the approved, rejected & unknown variables have comma separated values from their respective collections. There is very little processing that the brain needs to do to ascertain this.
