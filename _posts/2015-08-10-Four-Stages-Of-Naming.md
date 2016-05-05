---
layout: post
title: Stages of Naming
tags: Code
category: General
---

<blockquote>
There are only two hard things in Computer Science: cache invalidation and naming things -- Phil Karlton
</blockquote>

I first read about the concept of different stages of naming on [J. B. Rainsberger's blog](http://www.jbrains.ca/permalink/the-four-elements-of-simple-design) in 2015. At the time I had already recognized that my brain was going through different stages when I was naming things (methods, variables, tests etc.) although ironically I hadn't been able to put specific names to each stage. 

### Moving from zero to four stages ###

Joe's original post proposed four stages of naming...

<img class="img-responsive" alt="Four Stages of Naming" src="{{ site.url }}/assets/images/Naming-Four-Stages.png">

As he explained, laziness or ignorance would push one towards the left end of the spectrum, while with diligence one could move to the right. The further right one was, the more clarity one had.

### Moving from four to six stages ###

Understanding and embracing stage based naming is a liberating experience that has a huge impact on the code I have written. In early 2016 I saw a new take on naming stages that enhanced the original four stages of naming. Instead of four stages, [Arlo Belshee](https://twitter.com/arlobelshee) proposed six stages. 

<img class="img-responsive center-block" alt="Six Stages of Naming" src="{{ site.url }}/assets/images/Naming-Six-Stages.png">

What I really like about Arlo's model is his indication of where structural refactoring starts. This aligns with my own experiences with naming:  

- While I'm trying to get something to work names typically reach the "precisely named" stage. 
- Once things are working, I then put on my refactoring hat, at which point names transition to reveal intent.  

### Naming is emergent

One aspect that I have noticed with regards to naming is that it is typically an emergent process. I would love to be able to name things immediately at the "Meaningful" or "Domain Abstraction" stage, alas, my brain does not work that way! Instead, I'm quite happy to start off with nonsense names, and then allow good names to emerge as I progress through each stage.

<img class="img-responsive" alt="Naming is emergent" src="{{ site.url }}/assets/images/Naming-Emergent.jpg">

For instance, I might start with a variable that holds a number. I might initially name the variable "n" (nonsense stage). Then realizing that "n" is a number and is representing money, I would likely rename it to "amount" (potentially honest & complete stage?). With time I may realize that the amount actually is not just any amount, but in fact it is a sum of a set of values, at that point amount gets renamed to "total" and so the meaningful name continues to emerge.

<blockquote>
n => (time to think) => value => (time to think) => total
</blockquote>

### Naming impacts design

Another aspect of naming that I have noticed is that it has a very real impact on  design. Recently I was working on a piece of code where a class was named badly. Without getting into the specifics, whenever we worked on the code using the badly named class we got tripped up. We found it hard to make insights into the design and found it hard to explain to others. If it is hard to explain to others what something is doing without going into great detail you may be suffering from a bad name.

<img class="img-responsive" alt="Naming impacts design" src="{{ site.url }}/assets/images/Naming-Design.jpg">

With this specific class, we made a conceptual breakthrough and came up with a better name for it. A simple change in the name of the class changed what we felt the intent of the class should be. This led us to do some adjustments to the class that further impacted the design - it also made it a lot easier to explain to others what the class did. 

Simply put, names of things impact design!

### To sum it up

Next time you are writing code, be aware of the names you give things. Be conscious of what stage each variable, method, class or function is currently at in terms of it's naming. As you uncover meaningful names your design and solution will be impacted for good. Happy naming!

<blockquote>
To name something correctly gives us a certain amount of power over it - M. Scott Peck (People of the Lie) 
</blockquote>

#### References ####

[Four Elements of Simple Design](http://www.jbrains.ca/permalink/the-four-elements-of-simple-design)  
[Six Stages of Naming](https://twitter.com/llewellynfalco/status/634014935706636288)  
[Two hard things](http://martinfowler.com/bliki/TwoHardThings.html)  
