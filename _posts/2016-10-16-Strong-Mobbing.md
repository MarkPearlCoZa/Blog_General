---
layout: post
title: Strong Mobbing
tags: Mobbing Collaboration
category: General 
---

This post on "Strong Mobbing" is based on Llewellyn Falco's post on [strong-style pairing](http://llewellynfalco.blogspot.co.nz/2014/06/llewellyns-strong-style-pairing.html)  

> "For an idea to go from your head into the computer, it MUST go through someone else's hands"

This style of programming is all about increasing communication and collaboration. Verbally communicating how to solve a problem is a skill like anything else, but it is one that many people have not developed yet. Don't worry, it's pretty easy to gain and most people pick up the basics in a few hours.

There are two roles in strong mobbing, 

1. The typist
2. The rest of the mob (everyone else)

-------------------------------------------------------------------------------------------------------------------

### The typist

The person at the keyboard is the typist. It is a fairly simple role. You can "be at the keyboard" in languages and editors you are not unfamiliar with. There are two important things that are required for a happy typist experience:

1) Trust the mob  
2) Become comfortable working with incomplete understanding  

#### Trust the mob

When you are the typist trust that the rest of the mob knows what they are telling you. If you don't understand **WHAT** they are telling you ask questions. If you don't understand **WHY** they are telling you something don't worry about it until you've finished the method or section of code. The right time to discuss and challenge design decisions is after the solution is out of their heads or when you do not understand what they are asking you to do.  

#### Become comfortable working with incomplete understanding

Even if you trust the mob, members of the mob might not yet be comfortable communicating to you in this style. They might try and explain everything they have done up till then to you before they start giving you useful directions - this slows things down and depending on your knowledge of the system, can take hours or even days. Encourage them to rather start solving the problem at hand and that you will gain context as you type. You do not need a complete understand to be an effective typist. In fact, you don't need to know the language, the OS, the editor, the code, or even the problem you are working in.  

#### What if you have an idea you want to implement

You have an idea you think is worth implementing - Great! Let the mob know, ask if someone can take your place as typist while you communicate an idea. They then become the typist, and you become just part of the mob.  

-------------------------------------------------------------------------------------------------------------------

### The rest of the mob

As someone who is not the typist, but still part of the mob you have two main jobs...  

1) Help contribute to discovering what the next logical step is to solving the problem  
2) Talk in the highest level of abstraction the typist can understand

#### Discovering what the next logical step is to solving the problem

As part of the mob, essentially you are part of the problem solving team. You are looking for things the typist still needs to do. 

The key is that while you may see many angles and approaches, and should be keeping track of these in your head, you should be helping the typist to only focus on **one** thing.

#### Talk in the highest level of abstraction the typist can understand

Another very important part of your role is to talk at the highest level of abstraction that the typist is able to digest at that moment. Depending on how long you have worked with the typist, how in sync they are with what you are wanting them to do, and what their skill level is, the level of abstraction may change. 

For example, you may see a potential refactor to simplify the code by extracting a method. Asking the typist to extract the method may be a sufficient level of abstraction. If the typist looks at you you with a blank stare, go to a lower level of abstraction. Become a little more explicit - "highlight line 114 to 127 and then press ctrl+alt+m to extract method". 

Finding the appropriate level of abstraction is part of the challenge, when a mob is just starting out you typically use lower levels of abstraction, once a mob begins to get their flow you will find you are using higher levels of abstraction.

#### Communicate in a meaningful way

It is important that you communicate in a meaningful way. Don't speak above the typists understanding, and keep trying to increase the level of communication and understanding. Stay mindful of the typist, constantly adjust to their needs.

#### Embrace your humanity

Although you are brilliant intelligent person, you are going to make mistakes and make bad decisions. Embrace being human, making mistakes is part of our humanity. When you realize you have made a mistake openly admit it to the mob, but don't let mistakes hold you back from being an active contributor.

-------------------------------------------------------------------------------------------------------------------

### Final thoughts

Strong mobbing for me is normal mobbing - I'm sure there are other ways to do mob programming effectively, this seems to be the most effective way for the teams I have worked with. Whenever a mob starts there is always a bit of "storming" - that's people just being people. Treating those around you with kindness, consideration and respect is key for a mob to move from "storming" to "performing". 

It's easy to have friction over what conceptually is the right approach to a particular part of the codebase. Moving the discussion from being conceptual to being concrete by getting code on the screen often helps a mob move forward. If you have varying ideas of what the typist should be doing, go with the simplest one first - if it works, it is usually a good solution - if it doesn't work usually its flaws show quickly. 

If you think you have multiple ideas that are equally simple, go with the idea that came from the developer who has the least "experience".

#### References

[Llewellyn's strong-style pairing](http://llewellynfalco.blogspot.co.nz/2014/06/llewellyns-strong-style-pairing.html)  
