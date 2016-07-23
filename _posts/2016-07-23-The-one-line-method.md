---
layout: post
title: The one line method
tags: Misc, Code
category: General
---
I recently had a chance for an interesting code discussion. It is something I've been wanting to write about for a while, a practice I've been applying to my code that I find many other developers find strange, and being new a team I've been reminded that this is something I want to write about. I call it the "one line method" practice.

To illustrate where I apply the one line method practice let me show some sample C# code. In the code sample we have three collections. We want to take the values of each collection and put it into 3 strings that contains concatenated comma separated values.  

We do it as follows...

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

Everything looks great. In terms of desired values, everything is being generated correctly.   

At this point I do a further refactoring as follows:  

~~~
public static DoSomeWork()
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

For me there are two main motivators. 

1) My overarching principle in programming systems in the business space is writing code that is maintainable. The most maintainable code for me is code that is easily readable (write once, read many times). For me (and I understand this may not be for everyone), pulling the "work" of generating a comma separated string into a separate method increases the readability of the "DoSomeWork" method. Those reading my code can read that the approved, rejected & unknown variables have comma separated values from their respective collections without processing what String.Join(",", ...) does.

2) In this instance, I'm sensing some re-use. It is likely that if I decide to change how I format the approved variable, the rejected and unknown variable values will also likely change. By extracting a method with this work in it, it makes it easier to adjust all 3 values.

-------------------------------------------------------------------------------------------------

#### Advantages of this approach

- Readability is increased provided methods are named to reveal intent
- Patterns become easier to detect
- Less processing when people are "scanning" the code

#### Disadvantages of this approach

- Without a refactoring tool this creates extra work
- You could argue that String.Join("," ... ) in your brain tells you straight away that it is generating a comma separated string
- Code becomes longer to read in its entirety

#### What do you think?

At this point I would like to get feedback from the greater developer community on what they think of this practice. Is this something you would cry out in pain if you saw, or something you feel is an appropriate refactoring?
