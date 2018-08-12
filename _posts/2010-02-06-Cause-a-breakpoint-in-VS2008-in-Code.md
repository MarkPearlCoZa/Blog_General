---
layout: post
title: Cause a breakpoint in VS2008 in Code
tags: 
category: General
---
So I found an interesting code snippet for debugging. If you put the following code in your project, the compiler causes a breakpoint when it executes the line of code.  

~~~
System.Diagnostics.Debugger.Break();
~~~
