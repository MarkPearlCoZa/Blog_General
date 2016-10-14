---
layout: post
title: Staying engaged when mobbing
tags: Mobbing Collaboration
category: Misc
---

A recent challenge we have faced as my new team begins to adopt mob programming is staying engaged during exploration phases of work. This surfaced when we started work on automating a feature into our build pipeline - as a team we see value in automation AND we have varying expertise across the team with our infrastructure and automation tooling.

As the mob began the automation work, I left them for a few days to attend a local conference. On returning, the mob was not in as good a state as they had been before. At our next team retrospective it was suggested that while mobbing was great for programming, maybe it was not good for 'ops' or automation work.

This surprised me, I would have thought that with exploration work, where the team had very little and vastly varying knowledge, mobbing would do really well?

On probing, it became apparent that over the last few days the person with the most knowledge about infrastructure and automation tooling had ended up behind the keyboard for most of the time. In trying to get things working, he started moving very quickly trying different things. Up to now rotating the person behind the keyboard had been relaxed - sometimes the mob had rotated regularly, sometimes they had gone for long periods of time without any rotation. 

Because there was such a wide gap in understanding on this part of our system, as people got lost with what the 'driver' was doing they began to get disengaged which resulted in them understanding less and less of what was going on. This vicious cycle resulted in the majority of the mob invoking the 'law of two feet', ending back at their own desks looking for other things to do.

Luckily we had our fortnightly team retrospective the same day I returned - the concern was brought up and a discussion ensued on whether this was something mobbing was not suitable for; or if it was, what we should change in how we mob to get value from the practice.

### Is mobbing good for exploratory work?

In my experience, mobbing has been really good for exploratory work. Fundamentally, you have a bunch of people with different insights looking at the same problem at different angles - this doesn't seem any different from mobbing on normal programming work. The only difference I could see was in this situation there was no consensus on the direction to go - and in having the person who was best equipped behind the keyboard we exacerbated the issue.

In principle, mobbing still seemed like a good fit.

### Adjustments to our process

We decided to continue mobbing on work like this but with a few adjustments to our process.

- We strictly rotate the person behind the keyboard at a set time interval (we currently work on 10 minute rotations).  
- The person behind the keyboard is at the mercy of the mob - they cannot 'try' their own idea - if they want to do that, they need to give the keyboard to someone else - a practice we call strong mobbing.  
- If it feels like the entire mob is not going anywhere and that we need to work on our own to figure something out, we time box being on our own and resume the mob as soon as the time box has run out.  

### Strong Mobbing 

The practice of strong mobbing is not a new one - for me it's fundamental to making mobbing work in areas where there is high uncertainty on what the next step a mob should take. At it's essence, for an idea to be expressed it has to first go through some one not at the keyboard. This has it's roots in 'strong pairing'. For those who have not fully developed the skill of navigating in these situations it can prove to be a challenge and it is a useful skill to develop. 

In the ensuing day as we began to implement strong mobbing we noticed that the person who up to now had the most context on our infrastructure and automation tooling began to be frustrated - we were moving slower than we were before and he was battling to verbalize what he wanted us to do. 

It was also clear that the people who had been "at" the mob up to then but not really "in" the mob had some big gaps in their understanding of what had happened over the last few days. 

It took us several hours, some deep breaths and lots of joking around before we began to have some breakthroughs and gain momentum. As understanding began to spread across the whole mob people began to become engaged in the problem. All in all we came out of that session better developers - having a deeper understanding of how a section of our system that very few of us had understood up to now.

### Time boxed separations

We haven't done time boxed separations yet. I'm nervous about making this a regular practice. Personally I feel if we get good at strong mobbing we will not need to have time boxed separations and there is some security in saying we are not going to be dogmatic about a particular approach to tackling work.

### Avoid distracting mobile phones

There is one other thing that hasn't yet become a thing in our team, but has been a challenge in the past that I would like to mention - excessive mobile phone context switching.

Over use of mobile phones is a danger in a mob. I once worked in a team where one member while sitting in the mob spent a large portion of his time on his mobile. He was often there, but not there - if that makes sense? 

It was really frustrating for the rest of the mob because when engaged he was such a good developer. His mobile phone checking actively impacted the flow of the mob because he would continually have to ask what we had done while he was on his phone. In some situations he would repeat questions or want to discuss things we had just discussed a minute earlier. It got to a point where individuals in the mob each had a quite chat with the person expressing their frustration. While we sorted it out, it's easier to avoid the situation from day one.

I'm also not blameless in this regard. There have been days when I've been THAT person.

To avoid this going forward, I leave my mobile phone at my desk and far away from the mob. This encourages me to every 30 or so minutes briefly leave the mob to check my messages. I think this is a good thing - I get to stretch my legs a bit, and take a brain breather and while in the mob I can give my full attention. I would recommend this technique any mob.


#### References

- [Strong Pairing in Llewellyn's World](http://llewellynfalco.blogspot.co.nz/2014/06/llewellyns-strong-style-pairing.html)
