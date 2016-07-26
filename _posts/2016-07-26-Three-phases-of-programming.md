---
layout: post
title: Make it work, make it work right, make it work adequately fast
tags: Code
category: General
---

I believe Kent Beck was originally attributed with saying that when he solved programming problems he went through 3 stages:

1) Make it work,  
2) Make it right,  
3) Make it fast.  


The first time I heard this quoted was during the early days of me learning TDD. If I remember right, the person I was pairing with was explaining why I should be worrying about performance at that particular point since I hadn't yet "made the code work" yet. It was immensely helpful at the time.

Today I want to explain my interpretation of these three stages, with my own twist.

#### Stage 1 - Make it work 

This is the first stage I typically go through when coding a solution. When I am at this stage I'm still feeling around the problem or a subset of the problem. I'm not worried about naming things right. In fact, I often purposely pick 'bad' names ([see my article on stage of naming](http://blog.markpearl.co.za/Four-Stages-Of-Naming)). I'm also not worried too much about encapsulation - I'm happy to have big chunks of code mashed together. In essence, I'm focussed on getting the "code to work".

Now don't get me wrong, that doesn't mean I write the entire application all at once as a huge mess. I'm most probably using TDD, which means I'm still working with small subsets of the problem. But in that subset I'm not phased about 'breaking the rules' a bit.

If I have done my job right, typically I have achieved my goal of "making it work" when my failing test suddenly passes. At that point I move onto stage 2.

#### Stage 2 - Make it work right

Stage 2 is for me the design part. In stage 2 I've already got a working solution - it just may not be the most beautiful code. This is where I mercilessly refactor. At this stage I'm looking for points of abstraction and encapsulation. I'm looking at the names I've given things (classes, methods, variables, you name it). I'm looking for nested loops and multi-level if statements. I'm mindful of patterns - yes, patterns are still useful (often a variant of a pattern will emerge).

In a nutshell, at this stage I'm focussing on making the code readable and maintainable. Once I've felt that I have accomplished stage 2 I have a choice, I can stop or I can move on to stage 3.

#### Stage 3 - Make it fast

So, in all honesty I rarely progress to stage 3. To understand why, you need a little context on the type of problems I typically solve. I work predominantly in the business application domain space - from my experience, a small percentage of the code written in this space ends up being a performance bottleneck. Most of the code written performs just fine without any tweaking. In addition, 
