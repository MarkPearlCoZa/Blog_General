---
layout: post
title: The one line method
tags: Misc, Code
category: General
---
In my new team I recently had a chance for an interesting code discussion. It is something I've been wanting to write about for a while now, a practice I've been applying to my code that I find many other developers don't agree with or find strange. Being in a new team reminded me that I do this. I like to call it the "one line method".

To illustrate where I apply the one line method practice let me show some sample C# code. In the code sample we have three collections. We want to take the values of each collection and put it into a concatenated comma separated string. We do it as follows...

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
...
~~~
