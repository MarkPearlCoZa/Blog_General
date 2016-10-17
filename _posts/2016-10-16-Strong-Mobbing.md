---
layout: post
title: Strong mobbing
tags: Mobbing Collaboration
category: General 
---

This post on "Strong Mobbing" is based on Llewellyn Falco's post on [strong-style pairing](http://llewellynfalco.blogspot.co.nz/2014/06/llewellyns-strong-style-pairing.html)  

> "For an idea to go from your head into the computer, it MUST go through someone else's hands"

Strong mobbing is all about increasing communication and collaboration. Verbally communicating how to solve a problem without being at the keyboard is a skill like anything else, and it is one that many programmers have not fully developed. If you are new to strong mobbing don't worry - it's pretty easy to do and most people pick up the basics in a few hours.

There are two roles in strong mobbing, 

> 1. The typist
> 2. The rest of the mob 

-------------------------------------------------------------------------------------------------------------------

### The typist

The person at the keyboard is the typist. It is a simple role. You can be the typist in languages you are not familiar with, in editors you have never used before, on code bases you have never worked  on before. 

So what do you need to do to be the typist? You need to be able to press keys, trust the mob and be comfortable working with an incomplete understanding.

> - Press keys
> - Trust the mob  
> - Become comfortable working with an incomplete understanding  

Pressing keys on a keyboard is easy and requires little explanation. Trusting the mob and working with an incomplete understanding requires a little more explanation.

#### Trust the mob

When you are the typist trust that the rest of the mob knows what they are telling you. If you don't understand **WHAT** they are asking you to do, ask for clarification on what the next step is. If you don't understand **WHY** they are telling you something don't worry about it until you've finished the method or section of code. The right time to discuss and challenge design decisions is after the code is out of their heads and in the editor.

#### Become comfortable working with incomplete understanding

Even if you trust the mob, members of the mob might not yet be comfortable communicating to you in this style. They might try and explain everything they have done up till then to you before they start giving you useful directions - this slows things down, and depending on your knowledge of the system, can take hours or even days. 

Rather than getting a complete understanding before you start work, encourage the mob to start solving the problem at hand - you will gain context as you type. You do not need a complete understand to be an effective typist. 

#### What if you have an idea you want to implement

You have an idea you think is worth implementing - Great! Let the mob know, ask if someone can take your place as typist while you communicate the idea. The person taking the keyboard becomes the typist and you become part of the rest of the mob.  

-------------------------------------------------------------------------------------------------------------------

### The rest of the mob

As someone who is not the typist but still part of the mob you have two main jobs:

1) Help contribute to discovering what the next logical step is to solving the problem  
2) When directing the typist, talk in the highest level of abstraction the typist can understand

#### Discovering what the next logical step is to solving the problem

As part of rest of the mob, essentially you are part of the problem solving team. It's your job to look for things the typist still needs to do. 

The challenge and beauty of mob programming is that with different people in the mob there will be a certain [level of conflict](http://blog.markpearl.co.za/Levels-of-Conflict) on what approach the typist should take. When you have these situations, it's easy to have friction over what conceptually is the right approach. Moving the discussion from being conceptual to being concrete by getting code on the screen often helps a mob move forward. 

If you have varying ideas of what the typist should be doing, go with the simplest one first - if it works, it is usually a good solution - if it doesn't work its flaws usually show up quickly. If you think you have multiple ideas that are equally simple, go with the idea that came from the developer who has the least "experience".

The key is that while you may see many angles and approaches as a mob, you should be helping the typist to only focus on **one** thing.

#### Talk in the highest level of abstraction the typist can understand

Another very important part of your role is that when directing the typist you should talk at the highest level of abstraction that the typist is able to digest at that moment. Depending on how long the typist has been with the mob, how in sync they are with what the mob is wanting them to do, and what their skill level is, the level of abstraction may change. 

For example, you may see a potential refactor to simplify the code by extracting a method. Asking the typist to extract the method may be a sufficient level of abstraction. If the typist looks at you you with a blank stare, go to a lower level of abstraction. Become a little more explicit - "highlight line 114 to 127 and then press ctrl+alt+m to extract method". 

Finding the appropriate level of abstraction is part of the challenge, when a mob is just starting out it typically uses lower levels of abstraction, once a mob begins to get its flow you will find higher levels of abstraction are used.

#### Communicate in a meaningful way

It is important that you communicate in a meaningful way. Don't speak above the typists understanding, and keep trying to increase the level of communication and understanding. Stay mindful of the typist, constantly adjust to their needs.

#### Embrace your humanity

Although you are brilliant intelligent person, you are going to make mistakes and make bad decisions. Embrace being human, making mistakes is part of our humanity. When you realize you have made a mistake openly admit it to the mob, but don't let mistakes hold you back from being an active contributor.

-------------------------------------------------------------------------------------------------------------------

### Final thoughts

Strong mobbing for me is normal mobbing - I'm sure there are other ways to do mob programming effectively, this seems to be the most effective way for the teams I have worked with. Whenever a mob starts there is always a bit of "storming" - that's people just being people. Treating those around you with kindness, consideration and respect is key for a mob to move from "storming" to "performing". 


#### References

[Llewellyn's strong-style pairing](http://llewellynfalco.blogspot.co.nz/2014/06/llewellyns-strong-style-pairing.html)  
