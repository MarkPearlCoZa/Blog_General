---
layout: post
title: The Art of Safe Refactorings
tags: Code
category: General
---
#### An introduction to the art ####

I have just spent 3 days of my life refactoring a section of code with a good friend of mine, Janco. One of the most significant things I discovered during these sessions was Janco's constant focus on **safe refactorings**. He has brought it down to an art.

In the past when refactoring code I had the following 3 step approach:  
1. Before refactoring run the tests and make sure they pass  
2. Code the refactoring  
3. After refactoring run the tests again to make sure everything was still good  

While this approach has worked for me up to now, when sitting with Janco he pointed out that most of the time while working in step 2 of the process my solution was in a broken state. Yes, I was refactoring, but it wasn't safe - and in doing so I was missing out on valuable feedback from the code base. To use his words, I was making the **code bleed**! 

He suggested that instead of typing the refactoring code like I had in the past, we should lean heavily on our refactoring tool (Resharper) to transform the existing code in a safe way - thus the term safe refactorings.

#### What are safe refactorings ####

So what are safe refactorings? With safe refactorings the goal is to have the code in a passing state all the time with as little manual intervention as possible. To put it another way, at each step of the refactoring process the 'problem' the code is solving should still solve that problem (acceptance tests should consistently pass).  
For example, if I wanted to change a method name in my code, instead of manually making the change (by making sure that no existing methods already have that name, then locating where the method is being used and changing all usages to use the new name) I should rather use a refactoring tool to make the change - if the tool does not mess my code up then it has done the refactoring in a safe way. 

For all but the most trivial refactoring scenarios this has proved more challenging than I originally thought. Firstly, it required a deeper understanding of my refactoring tool than I previously had. Secondly, I needed to continually fight the urge to **write new** code. Lastly, there were a few instances where either the refactoring tool was not able to do a safe refactoring, or I couldn't figure out the pattern to get the tool to do it. 

In spite of these challenges, in the 3 days that Janco and I worked together, we managed to keep the code in a passing state using safe refactorings for about 90% of the time. During the same period we were able to radically transform the solutions code structure - which in my opinion was rather awesome. 

#### Safe refactoring patterns series ####

In an effort to share some of the safe refactoring patterns that we used in the 3 day refactoring bonanza, I am going to do a series of blog posts about safe refactoring patterns. The series will be Resharper dependent, but I believe these patterns transcend a particular tool and could be used with other refactoring tools.

With that, feel free to continue to the first safe refactoring pattern called ['Move Instance Method Pattern'](http://blog.markpearl.co.za/Safe-Refactorings-Pattern-Move-Method-Instance/).  
