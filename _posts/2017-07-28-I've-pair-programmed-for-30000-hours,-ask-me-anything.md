---
layout: post
title: I've pair programmed for 30000 hours, ask me anything
tags: 
category: Media
---
These notes are based off the talk [I've pair programmed for 30 000 hours, ask me anything](https://www.youtube.com/watch?v=RCDfBioUgts) by Joe Moore

General Q&A on pair programming:  

Getting started pairing for the very first time:  
* Be honest that you have never paired for the first time  
* Set's a tone of both of you being extra mindful of pairing etiquette (see that they are stuck, asking to help drive)  
* If you are using TDD, it goes hand in had with pairing, especially ping pong pairing
* Related to this is, what do you do if someone is driving too much? Asking to do ping pong pairing may rebalance the pair  

When do you switch pairs, how do you minamize context switching?
* I encourage you swapping pairs, but it can be painful because you have just made progress and then you have to switch  
* Having a rule like switching every day is more like a guideline instead of a hard rule (ask if there are any pairs that need to stick in your daily standup)  
* When ramping up new developers you will often have the new developer stay in a pair so they get the whole architecture  
* I've definitely seen it where pairs stick for days on end, that's usually when things have gotten out of control and should be swapped out  
* We don't let people to pair with anyone they like for as long as they like  

If you are switching every day, how do you track who is working on what  
* Some tools have support for this, i.e. pivotal tracker  
* You can do things in your git commit that you can attribute to multiple people (git duet, or git pair)  
* Some organizations it is very important for them that they track who is working on what for how long... we don't do that...   

How do you convince a manager or your boss to try something like pair programming for their teams
* This is really the big question  
* There are a lot of answers, if some people who are selling agile, if they can share what they have learn't on how to do this  
* Talk about all the benefits we've just spoken about, there are short term gains like knowledge share and bug fixes
* There are some short term gains that are harder to quantify, like making code modular
* If you are in a current team that has metrics on how things are being done, it is a great opportunity to put in pairing and do the same metrics and compare  
* That asks the question, what does done mean... if you take the rework and QA cycle, getting business requirements wrong and measure those you have reduced time to market which may show pair programming is benficial    
* The pay off is all the extra work you avoid  
* If you say it with conviction and honesty, and that you don't want to "play" with your friend all day
* You have to make a leap of faith, it boils down to trust
* Management you have to give us enough time for us to see the benefits  
* If we had 100 years of imperical evidence, it would be a lot easier to sell this stuff  
* Organizations are investing time in things that become redundant like code reviews  
* Ramp up of onboarding is reduced, orgs often generate documents, this isn't needed with pairing  
* Organizations invest times in teaching people, this is something that pairing has a benefit without it being a separate activity
* Orgs try and spread knowledge, pairing is a way of getting this knowledge shared, especially rotating people across teams  

When you pair program do you try and get to know your pair better or do you try keep a strict professional wall
* We hire for empathy, cultural fit, ability to learn  
* Pair programming generates empathy and comradrie  
* Some people I pair with I just don't click with, but I get to know where they are coming from  
* Everyone has a different line on how much they share, some people share too much, some don't share enough
* I enjoy the breaks we have while pair programming, that gives us an opportunity to get to know people better  
* It moves us from being resources to people  

Is it still pairing if you are working with someone else, but you are doing the backend and they are doing the front end
* At pivotal labs you would not see people doing this type of work
* Our personal philosophy is that we want to be full stack developers  
* Working independently is creating a knowledge silo, probably...
* It's also reintroduced some of the challenges of working on your own, the little things you get stuck on  
* I would always question why  

When you choose not to pair, are people being honest  
* There is always an excuse not to pair  
* I find that often the reason is actually the person doesn't want to pair  

Remote pairing, what happens when people are not side by side  
* I work full time doing remote pairing  
* I have some talks online about remote pairing  
* I am easily the most biased person on remote pairing  
* Remote pairing is a lot of work, making the remote pairing as seamless as possible, I want it to be like I'm right there
* It is very often that by the end of the day that people forgot that they were remote  
* Time zone differences are really hard, try and pair during the overlapping times  

During your hiring process do you have tests for empathy
* Yes, we do. During our screening process we have some screening for empathy  
* Our interview process is that by the time you get into the building you are going to work with a team for a day  
* The interview is pairing, do I know you, can I talk to you, can I work with you  
* Pair programming is not for everybody  

How are people assessed if you are primarily pairing
* We are assessed by our pairs  
* Our engineering managers are working with our pairs to get feedback  

The thing that killed pairing was their orgnanization was measuring how many lines of code they were committing and they didn't have a way of tracking pairs on a commit  

How do you motivate teams that have not paired to pair
* There are multiple ways of doing this, give freedom to your engineering teams  
* Sometimes just giving the permission will spark things  
* Make sure things are socially accepted  
* Sometimes the best technique is to keep delivering  

Pluses and Deltas  
* End of a pairing session, what worked and what could change
* Keep feedback kind, actionable and specific
* Prepare the team before you start pairing that there will be feedback at the end of the day
