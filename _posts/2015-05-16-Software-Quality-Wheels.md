---
layout: post
title: Software Quality Wheels
tags: Code
category: General
---
I recently read Jessica Kerr's blog post on the [quality wheel](http://blog.jessitron.com/2015/04/the-quality-wheel.html). In general, I loved her idea of being able to use it to further refine specific aspects of quality software systems. One aspect of her wheel that I didn't agree with was putting beautiful code as the center item to the quality wheel. I don't believe that beautiful code is the generalization of quality software systems. For instance, while beautiful code is important - I have found poor quality systems that have had beautiful code.  That said, her wheel prompted me to try and create my own 'quality' wheel.

My first attempt at a revised wheel didn't go well. Specific attributes of a genralized quality software system ended up being pie in the sky. For instance, quality attributes that are important to a client application don't necessarily apply to a consumer based website and vice versa. Being able to catagorically say that one generic attribute is important for all systems seemed impossible - context matters. After several minutes of no inspiration I ended deciding that the only thing I could easily change was the 'beautiful code'. I replaced it with quality software systems.

<img class="img-responsive" alt="Quality Software Systems Original Diagram" src="{{ site.url }}/assets/images/Quality-Software-System-Original.png">

### Separating Internal vs Exterval views on Quality Software Systems ###

Two days later I made a second attempt at defining my quality software system wheel. Instead of thinking of quality in a generic sense, I changed my approach and thought of it in terms of a specific project I was working on. In this instance I thought about [MaxCut](www.MaxCut.co.za) - a system I have been involved with for a few years. Coming up with quality aspects for MaxCut was a lot easier. While trying to identify different attributes I noticed that some of the attributes I was listing were important to me as a software engineer (for instance the simplicity of the code) and had an internal viewpoint.

<img class="img-responsive" alt="Internal Attributes of Quality Software Systems" src="{{ site.url }}/assets/images/Quality-Software-Internal-Attributes.png">

Other attributes were important were important to an end user and could be good even if the internal workings weren't great (i.e. how easy features were to discover and use - this has nothing to do with code, but is still an important quality attribute for this system). 

<img class="img-responsive" alt="External Attributes of Quality Software Systems" src="{{ site.url }}/assets/images/Quality-Software-External-Attributes.png">

This led me to splitting my quality wheel into two wheels - one specifically focussing on external quality attributes and one specifically focussing on internal quality attributes. Taking this idea further, there are possibly a number of additional wheels of quality we could have identified.

### Why is this useful? ###

When we have words that mean different things for different people and these people interact - misunderstandings can occur. Clarifying these words can be useful. 




