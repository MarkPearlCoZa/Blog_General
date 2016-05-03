---
layout: post
title: Stages of Naming
tags: Code
category: General
---

<blockquote>
There are only two hard things in Computer Science: cache invalidation and naming things -- Phil Karlton
</blockquote>

I first read about the concept of different stages of naming on [J. B. Rainsberger's blog](http://www.jbrains.ca/permalink/the-four-elements-of-simple-design) in 2015. At the time I had already recognized that my brain was going through different stages when I was naming things (methods, variables, tests etc.) although ironically I hadn't yet been able to put specific names to each stage yet. 

### Moving from zero to four stages ###

Joe's original proposed four stages of naming...

<img class="img-responsive" alt="Four Stages of Naming" src="{{ site.url }}/assets/images/Naming-Four-Stages.png">

As he explained, laziness or ignorance would push one towards the left end of the spectrum, while with diligence one could move to the right. The further right one was, the more clarity one had.

### Moving from four to six stages ###

Understanding and embracing stage based naming is a liberating experience that has had a huge impact on the code I write. In early 2016 I saw a new take on naming stages that took things to the next level. Instead of four stages, [Arlo Belshee](https://twitter.com/arlobelshee) proposed six stages. 

<img class="img-responsive center-block" alt="Six Stages of Naming" src="{{ site.url }}/assets/images/Naming-Six-Stages.png">

One aspect I really like about Arlo's model is the indication that refactoring starts at the "does the right thing" stage. My own experiences lead me to believe that while I'm trying to get something to work names typically sit in the "precisely named" or "honest & complete" stages. Once things are working, I then itypically put on my refactoring hat, and at that point names transition to reveal intent and meaning.

### Naming is emergent

Another attribute that I have noticed with naming is that it is an emergent process. I would love to be able to name things immediately at the "Meaningful" or "Domain Abstraction" stage. Alas, my brain does not work that way. Instead, I'm quite happy to start off with nonsense names, and then allow the names to progess through each stage.

<img class="img-responsive" alt="Naming is emergent" src="{{ site.url }}/assets/images/Naming-Emergent.jpg">

For instance, I might start with a variable that holds a number. I might initially name the variable "x" (nonsense stage). Then realizing that "n" is a number and is representing money, I would probably rename it to "amount" (potentially honest & complete?). With time I may realize that the amount acutally is not just any amount, but in fact it is a sum of a set of values, at that point amount gets renamed to "total" and so the name continues to emerge as it progresses through each stage.

<blockquote>
x => (time to think) => value => (time to think) => total
</blockquote>

### Naming impacts design

Another aspect of naming that I have noticed is that names impact design. Recently I was working on a piece of code where a class was named badly. Without getting into the specifics, whenever we were worked on code impacted by that class we semmed to get tripped up. A good indication of a bad name is that it is hard to explain what the thing is doing to others.

<img class="img-responsive" alt="Naming impacts design" src="{{ site.url }}/assets/images/Naming-Design.jpg">

After a while we had some insights into a better name for that class. A simple change in the name of the class changed what we felt the intent of the class should be. It also made it easier to explain to others. This led us to do some adjustments to the class that further impacted the design.

After further discussion with business users we discovered that we had misunderstood the business process. The class was doing the wrong thing. Identifying a better name for the process led to a better name for the class. This led to further adjustments that ultimately helped us make design breakthroughs. 

Names of things impact design!

### To sum it up

Next time you are writing code, be aware of the names you give to things. Be conscious of what stage each thing is currently at in terms of it's name. You will be surprised at how as you uncover the more meaningful names your design and solution is impacted. Happy naming!

<blockquote>
To name something correctly gives us a certain amount of power over it - M. Scott Peck (People of the Lie) 
</blockquote>

#### References ####

[Four Elements of Simple Design](http://www.jbrains.ca/permalink/the-four-elements-of-simple-design)  
[Six Stages of Naming](https://twitter.com/llewellynfalco/status/634014935706636288)  
[Two hard things](http://martinfowler.com/bliki/TwoHardThings.html)  
