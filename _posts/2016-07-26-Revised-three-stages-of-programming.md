---
layout: post
title: My revised three stages of programming
tags: Code
category: General
---

I believe Kent Beck was originally attributed with saying that when he solved programming problems he went through 3 stages:

1) Make it work,  
2) Make it right,  
3) Make it fast.  


The first time I heard this quoted was during the early days of me learning TDD. If I remember right, the person I was pairing with was explaining why I should not be worrying about performance at that particular point since I hadn't yet "made the code work". It was immensely helpful at the time.

Today I want to explain my interpretation of these three stages, with my own twist:

-------------------------------------------------------------------------------------------

#### Stage 1 - Make it work 

This is the first stage I typically go through when coding a solution. I think of it as the problem solving stage. When I'm at this stage I'm still feeling around the problem or a subset of the problem. I'm not worried about naming things right, in fact, I often purposely pick 'bad' names ([see my article on stages of naming](http://blog.markpearl.co.za/Four-Stages-Of-Naming)). I'm also not overly worried about encapsulation - I'm happy to have big chunks of code mashed together. In essence, I'm focussed on one thing - getting the "code to work".

Now don't get me wrong, that doesn't mean I write the entire application all at once as a huge mess. That would be a bad idea. I'm most probably using TDD, which means I'm still working with small subsets of the whole problem. But in that subset I'm not phased about 'breaking good design rules' a bit.

If I have done my job right, typically I have achieved my goal of "making it work" when my failing test suddenly passes. At that point I move onto stage 2.

#### Stage 2 - Make it work right

For me, this is the real design part. In stage 2 I've already got a working solution - it just may not be the most beautiful code. This is where I mercilessly refactor. At this stage I'm looking for points of abstraction and encapsulation. I'm looking at the names I've given things (classes, methods, variables, you name it). I'm looking for nested loops and multi-level if statements. I'm also mindful of patterns - yes, patterns are still useful (often a variant of a pattern will emerge).

In a nutshell, at this stage I'm focussing on making the code readable and maintainable. Once I've felt that I have accomplished this, I'm finished with stage 2. At this point I have a choice, I can stop and move on to the next problem, or I can move on to stage 3.

#### Stage 3 - Make it fast

In all honesty I rarely progress to stage 3. To understand why, you need a little context on the type of problems I typically solve. If these don't apply to you, by all means... make the code fast.

-------------------------------------------------------------------------------------------

#### Why I don't progress to Stage 3  

I work predominantly on business applications - from past experience, a small percentage of the code written in the problems I solve ends up becoming a performance bottleneck. Most of the code performs just fine without any tweaking - it may not be optimally running, but it is good enough. 

To further motivate why I rarely focus on making code 'fast' it is important to understand what I value most. When given a choice between readability and performance, I will pick readability any day of the week. Generally, I value readability over performance!

<img class="img-responsive" alt="Scale" src="{{ site.url }}/assets/images/Three-Stages-Of-Programming-Scale.jpg">

Why do I value this? What I've observed is that when I 'optimize' code I typically loose readability. For me, readability and performance sit on opposite ends of the scale. The more performant my code is, the less readable it is, and likewise, the more readable my code is, the less performant it is. 

The problems I typically solve are continually evolving, which means someone will be adjusting what I originally wrote many times in the future. This often means the CPU cycles saved by me making code performant aren't worth the expense and time it will take for the next developer to de-tangle my extremely performant code to discover what it was I intended to do. 

Now, that doesn't mean I never get to stage 3. Sometimes performant code is worth more than readable code. If I was working on a platform where the costs of writing performant code outweighed the benefits of readability I would follow through to stage 3 and I believe there are situations where this is necessary. 

-------------------------------------------------------------------------------------------

#### My revised 3 stages of programming

With that explanation I would like to propose a slight variant on the original 3 stages, it goes as follows:

1) Make it work,  
2) Make it work right,  
3) Make it adequately fast.  
