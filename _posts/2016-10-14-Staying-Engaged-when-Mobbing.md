---
layout: post
title: Staying engaged when mobbing
tags: Mobbing Collaboration
category: Misc
---

A recent challenge we have faced as my new team begins to adopt mob programming is staying engaged during exploration phases of work. This surfaced when we started work on automating a feature into our build pipeline - as a team we see value in automation AND currently we have varying expertise with our infrastructure and automation tooling.

As the mob began the automation work, I left them for a few days to attend a local conference. On returning, the mob was not in as good a state as it had been before. At our next team retrospective it was suggested that while mobbing was great for programming, maybe it was not good for 'ops' or automation work.

This surprised me, I would have thought that with exploration work, where the team had very little and vastly varying knowledge, mobbing would do really well?

On probing, it became apparent that over the last few days, the person with the most knowledge about automation and our infrastrucutre had ended up behind the keyboard for most of the time. While they had a much better understanding of the tools we were using for automation, they also didn't have a fully understanding of the tool. He started moving really quickly trying different things. 

Up to now, rotating the driver has been relaxed - sometimes the mob will do it at a regular cadence, sometimes they will not. 

Because we had such a wide gap in understanding what was happening, the rest of the mob began to get disengaged as they understood less and less of what the person was doing. As he went down certain 'dead ends' more people would get lost - people were still 'at the mob' but were not 'in the mob'. With time they began to exercise the law of two feet and go back to their own desks.

Luckily this didn't happen for to long before it was brought up, a discussion ensued on what we should do in situations like this.

### What we changed

We decided on a few things:  

- The person with the most context should be at the keyboard the least - a technique adapted from strong pairing    
- If it feels like the entire mob is not going anywhere, and we need to do some basic tutorials on something and it is best done on ones own, time box that period and then resume the mob.    

#### Strong Pairing

The person with the most context not being at the keyboard is not a new concept - I've been familiar with it from pair programming days where it is called strong pairing. This type of approach can be a challenge for those who have not fully developed the skill of navigating and it is a useful challenge to conquer.

In this instance, as we began to implement strong pairing we noticed the following behavior. The person with the most context up to that point who had also been driving the most began to be frustrated - we were moving slower than we were before and he was battling to verbalize what he wanted the driver to do. It was also clear that the people who had been "at" the mob up to then but not really "in" the mob had some big gaps in their understanding of what had happened over the last few days. 

It took us several hours, some deep breaths and lots of joking around before we began to have some breakthroughs and gain momentum. As understanding began to spread across the whole mob people began to become engaged in the problem. All in all we came out of that session better developers.

#### Time boxed Separations

We haven't done time boxed separations yet. I'm nervous about making this a regular practice. Personally I feel if we get good at strong pairing we will not need to have time boxed separations. 

### One other thing to look out for

There is one other thing to look out for, that hasn't yet become a thing our team and that is the challenge of mobile phone.

#### Mobile phones

Mobile phones frustrate me in mobs. I once worked in a team where one member while sitting in the mob spent a large portion of his time on his mobile. 

He was often there, but not there - if that makes sense? 

It was really frustrating for the rest of the mob because when engaged he was such a good developer. His mobile phone checking would also actively impacted the flow of the mob because he would continually have to ask what we had done while he was on his phone. In some situations he would repeat questions or want to discuss things we had just discussed a minute earlier. 

I've also not blameless in this regard. I've been that person before.

Personally, I now try and leave my mobile phone at my desk and far away from the mob. This encourages me to every 30 or so minutes briefly leave the mob to check my messages, which I think is a good thing - I get to stretch my legs a bit, and take a brain breather. I would recommend this practice to mobs where mobile phones become a problem.



#### References

- [Strong Pairing in Llewellyn's World](http://llewellynfalco.blogspot.co.nz/2014/06/llewellyns-strong-style-pairing.html)
