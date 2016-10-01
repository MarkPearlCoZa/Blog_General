---
layout: post
title: The Technical Debt Trap
tags: 
category: Media
---

These notes are based on [Doc Norton's](https://twitter.com/DocOnDev) talk on "[The Technical Debt Trap](https://vimeo.com/97507576)" done at NDC 2014.

### Overview

Technical Debt has become a catch-all phrase for any code that needs to be re-worked. Much like Refactoring has become a catch-all phrase for any activity that involves changing code. These fundamental misunderstandings and comfortable yet mis-applied metaphors have resulted in a plethora of poor decisions. 

- What is technical debt?   
- What is not technical debt?   
- Why should we care?   
- What is the cost of misunderstanding?   
- What do we do about it?   

Doc discusses the origins of the metaphor, what it means today, and how we properly identify and manage technical debt.

### Where did the term originate from?

[Ward Cunningham](https://en.wikipedia.org/wiki/Ward_Cunningham) coined the phrase "Technical Debt". The first written record was a paper from [OOPSLA '92](http://www.oopsla.org/oopsla-history/)

> Shipping first time code is like going into debt, a little debt speeds development so long as it is paid back promptly with a rewrite - Ward Cunningham

The reason Ward Cunningham used the metaphor 'debt' was that before the OOPSLA conference he had used almost the same words in an email he sent to a client who was in the financial industry. He was trying to explain to his client why the team needed to go back and redo work.

> The danger occurs when the debt is not repaid. Every minute spent on not-quite-right code counts as interest on that debt - Ward Cunninga

#### Technical Debt is a Metaphor  

Metaphors are analogies of the thing, Technical Debt is a Metaphor. 
The challenge we have with metaphors is we confuse them and begin to act as if the metaphor is the actual thing we are referring to.
Metaphors can go wrong, over the course of time because we called Technical Debt, we started talking more and more about debt, not the thing we were comparing it to.  

### Exploring technical debt 

#### Is technical debt good or bad?

Technical debt is good:   

- It is a strategic design decision  
- Indication of learning  

#### Requirements for it to be considered technical debt

> Many have explained the debt metaphor and confused it with the idea that you can write code poorly with the intention of doing a good job later... The ability to pay back the debt ... depends upon you writing code that is clean enough to be able to refactor as you come to understand your problem - Ward Cunningham

- Clean, well tested code that can be easily refactored is a pre-requisite for technical debt

> Dirty code is to technical debt as the pawn broker is to financial debt. Don't think you are ever going to get your 'code' back - Ward Cunningham  

#### How do you know if it qualifies for technical debt?

It should tick all of the below requirements...  

- Is the code clean?  
- Is the code tested?  
- Is there a learning objective or event?  
- Is there a plan for payback?  
- Is the business truly informed?

**If you say no to any of the above items, you don't have technical debt.i**

#### Does it really matter what the definition of technical debt is?

> If we agree technical debt is good, and we agree that 'quick and dirty' is technical debt, then we agree that 'quick and dirty' is good!
> I just can't abide by that, I've seen the pain that quick and dirty causes - Doc Norton

### Technical debt quadrants

[Martin Fowler](https://en.wikipedia.org/wiki/Martin_Fowler) continued to explore the metaphor of Technical Debt, however it wasn't the same thing Ward Cunningham originally meant. 

<img class="img-responsive" alt="Martin Fowler Technical Debt Quadrants" src="{{ site.url }}/assets/images/Technical-Debt-Quadrants-Original-Martin-Fowler.png">

#### Issues with top right quadrant

"We must ship now and deal with consequences" - that is deliberate, but what part of that is prudent. Suggest we change it to "Let's deploy and gather information".

#### Issues with top & bottom left quadrants

Is "Technical" Debt appropriate in other industries

If we applied this metaphor to other professions we may end up with things like the following...

- "We incurred structural debt to make the deadline and built the windows skew" - Reckless and deliberate  
- "We incurred mechanical debt to stay on budget and made the vehicle dangerous" - Reckless and deliberate  
- "We incurred health debt during the surgery and left the scissors in him" - Reckless and inadvertant  

Are these appropriate actions? Reckless and deliberate in the quadrant is irresponsible and is not technical debt.

<img class="img-responsive" alt="Technical Debt Quadrants Adjusted" src="{{ site.url }}/assets/images/Technical-Debt-Quadrants-Adjusted-Doc-Norton.jpg">

### If it is not technical debt, what is it?

If you have bad code, and it doesn't meet these requirements, what is it? Cruft?

<img class="img-responsive" alt="Cruft Definition" src="{{ site.url }}/assets/images/Technical-Debt-Cruft-Definition.png">

Redundant, old, or improperly written code - Cruft!

#### Cruft is a bad decision every time, but sometimes it is made inadvertantly

- You are a professional developer    
- You're going to create unintentional cruft  
- You are going to have to clean it up once you know it exists  

Do not make more work for yourself by intentionally putting cruft in your code.

#### Cruft begats cruft

- Precedent for speed over quality  
- Expectation of increased velocity  
- Cruft slows you down  
- Must write more cruft to keep you up  
- Ask permission to do your job correctly 

#### Avoid hardening sprints - they don't help

- Hardening sprints that "clean up the code" are not sustainable
- Code bases by general over time have a higher cost of change.
- Never ask permission to do your job correctly

> Instead of hardening sprints avoid the trap in the first place, clean constantly

### Monitoring Technical Debt

Appropriate things to monitor include... 

- Code Coverage  
- Code Complexity  
- Coupling  
- Maintainability  

#### References  

- [Slide on Talk](http://www.slideshare.net/DocOnDev/the-technical-debt-trap)  
- [Technical Debt Metaphor Explained by Ward Cunningham](https://www.youtube.com/watch?v=pqeJFYwnkjE)  
- [Ward Cunningham](https://en.wikipedia.org/wiki/Ward_Cunningham)   
