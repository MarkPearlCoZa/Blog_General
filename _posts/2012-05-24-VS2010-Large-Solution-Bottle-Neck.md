---
layout: post
title: VS2010 Large Solution Bottle Neck
tags: 
category: General
---
Recently I looked into speeding up Visual Studio builds – I found the results interesting… I decided to do a few POC’s to see where the bottleneck is with large solutions in Visual Studio.

After some searching on the net I found various tweaks that one can do to ones machine to get better performance and a few mentions that VS2010 does not handle multiple project files very well – the number mentioned several times was 10 – if you have more than 10 projects in a solution you see a noticeable decrease in build time and responsiveness.

Here were my findings…

Solution with 100 projects each with a single class

I set up a solution with 100 class projects with a single class in each project and did a clean build on the solution. The average build time per project was 00:00.2 units, leaving me with a total build time of 00:16.0 units. Not terrible, but remember these projects are about as small as they can get – this is the best case with this scenario.

Solution with one project and 100 classes in a single namespace

The next step was to establish where the load was on the build, would I get similar results with a solution with one project with 100 classes? Again I set up a solution with one project with 100 classes (exact same content in the classes) – total build time 0:00.17 units, significantly faster.

Solution with one project and 100 classes in separate namespaces

Still not sure if possibly I would see a difference if I had multiple namespaces in one solution, I made another solution with one single project and a 100 different classes – each in their own unique namespace.. nada, still getting performance around 0:00.17 units, significantly faster than one solution with 100 projects with one class per project.

Graphically shown it tells its own story

Build Times

Conclusion

Keep as few projects as possible in a solution. It is nice to have projects as a physical separation of units of code, but if you plan on keeping them in the same solution you are opening yourself up to build time pain. 

I would suggest rather using as few projects as possible in a solution – approach A would be if you can separate the solution into multiple solutions (keeping your project count as low as possible). If you don’t like the multiple solution idea you can always take approach B and have a one solution strategy with multiple namespaces within the single solution to isolate things and show the boundary line of what goes where.

With approach B it will require some discipline by and team consensus with your developers, but I am sure they would prefer this than losing hours of their day building a solution. And that’s my take on things – by all means do the hardware tweaks of setting up ram drives etc. – but fundamentally rather avoid the problem totally – If I have missed something obvious or you know of an awesome way to get past this problem, please leave a comment!

If you would like to do your own investigation you can download the test solutions from here and run your own scenarios.