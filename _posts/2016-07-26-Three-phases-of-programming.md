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

The first time I heard this quoted was during the early days of me learning TDD. If I remember right, the person I was pairing with was explaining why I should be worrying about performance at that particular point since I hadn't yet "made" the code "work" yet. It was immensely helpful at the time.

Today I want to explain my interpretation of these three stages, with my own twist.

#### Make it work 

This is the first stage I typically go through. When I am at this stage I'm still feeling around the problem or a subset of the problem. I'm not to worried about naming things right. In fact, I often purposely pick 'bad' names (see my [article on stage of naming](http://blog.markpearl.co.za/Four-Stages-Of-Naming)). I'm also not to worried encapsulation - I'm happy to have big chunks of code mashed together. I'm solely focussed on getting the code to "work".

That doesn't mean I write the entire application all at once. I'm still breaking the problem down into smaller chunks.
