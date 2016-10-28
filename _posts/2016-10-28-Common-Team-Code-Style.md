---
layout: post
title: Getting a common team code standard 
tags: Mobbing
category: Unpublished
---
### Code standard discrepency

When you start mob programming you will immediately notice there is a discrepency in coding standards amongst your team. Before mob programming, team coding standards were hard. You probably had a team document outlining stylistic code prefences or a peer review process when someone in your teams compelted a feature or even pair programmed frequently, so why do you suddenly see this discrepency? I believe it boils down to two aspect that mob programming provides that other practices are not as good at:

1. Near zero latency between the code being written and people reviewing it  
2. High diversity in the feedback, multiple people giving their input leads to higher alignment  

### The challenge of near instant feedback

The challenge of near instant feedback from a group people who have never coded together before is conflict. Typically you will see conflict between individuals on stylistic preferences (turns out most programmers are passionate about the code they write - who would have thought). If the conflict continues to escalate you risk people not wanting to participate in a mob again.



If this get's out of control people 

This is natural, we all think we have a better way of doing things.

a good thing, provided a team mobs reguarly you will end up with a common team code standard.

#### Latency 

Shorter latencies are better. Code that takes a longer time to get feedback from the team have a higher chance of not having a common team style - everyone programmer has their own personal preferences.

#### Code standards documents

Code standard documents are one of t
Early on in my career I tried using a code standards documents as a mechanism to avoid 'bad' code - I started with a standards document I found off the internet (it seemed perfect, it was based on the programming language my team was using at the time and appeared to be quite comprehensive). It was a thick document that outlined all the do's and dont's of naming and structure and what to do in special circumstances. I of course made some personal adjustments based on my own stylistic preferences, it didn't take more than a few days, and asked my team to adopt these standards going forward. 

The problem I soon discovered was that code standards documents get very long very quickly. As I moved from system to system I encountered new technologies, discovered new approaches and learnt better ways of doing things. Very soon my coding standards document was getting fairly thick and the maintenance of it was becoming impractical.

To rub salt in the wound, I soon discovered that not everyone was reading and staying up to date with my standards document. It seemed that for every page I added to the document, the likelihood of people reading it dropped by an order of magnitude. When people did read it, they often understand it differently from what I had originally intended. While people thought they where compliant, often they were not.

#### Problem with code reviews

No problem, I can solve this with code reviews. I'll simply review all of my teams code and make sure they follow my standard. Turns out this can very quickly become a full time job. With just 4 developers I was doing code reviews all day and not writing any code myself. 

Let's share this this responsibility across the team I thought. Instead of me reviewing everyone's code, as someone completes a feature, they should find someone else in the team to review their code.This was an improvement to just the standards document. The code seemed to be getting better. I was however still seeing varying quality in the quality of the code and also observing some interesting people dynamics. 

For instance, certain developers preferred other developers to review their code. These "review marriages" resulted in varying standards between groups. In addition, because the reviews were only being done post the feature being written often there was a ton of code to review an

