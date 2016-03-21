---
layout: post
title: Software Quality Notes
tags: Notes
category: Soft
---
 
#### Technical Debt ####

Ward Cunningham coined the term Technical Debt:
"Shipping first time code is like going into debt. A little debt speeds development so long as it is paid back promptly with a rewrite. Objects make the cost of this transaction tolerable. The danger occurs when the debt is not repaid. Every minute spent on not-quite-right code counts as interest on that debt. Entire engineering organizations can be brought to a stand-still under the debt load of an unconsolidated implementation, object- oriented or otherwise."
 
Here's further clarification [from the man himself](https://www.youtube.com/watch?v=pqeJFYwnkjE)
He makes an important point right at the end:
"In other words, the whole debt metaphor, let's say, the ability to pay back debt, and make the debt metaphor work for your advantage depends upon your writing code that is clean enough to be able to refactor as you come to understand your problem."
 
#### Technical Debt vs Messy Code ####

Some people make a distinction between messy code and technical debt. Robert Martin expands on this idea here: [https://sites.google.com/site/unclebobconsultingllc/a-mess-is-not-a-technical-debt]
Michael Norton also attempts to [clear up the confusion here](http://www.docondev.com/2009/08/messy-code-is-not-technical-debt.html)
 
#### Software Defect ####

From Wikipedia:
A software [bug is an error](http://en.wikipedia.org/wiki/Software_defect), flaw, failure, or fault in a computer program or system that causes it to produce an incorrect or unexpected result, or to behave in unintended ways.  
 
#### Defect Cost Increase (DCI) ####
The following is from Extreme Programming Explained by Kent Beck (*The* original XP bible, and a must read for all software developers!)
Defect Cost Increase (DCI) is the second principle applied in XP to increase the cost-effectiveness of testing. DCI is one of the few empirically verified truths about software development: the sooner you find a defect, the cheaper it is to fix. If you find a defect after a decade of deployment you'll have to reconstruct a lot of history and context to figure out what the code was supposed to do in the first place, which of those assumptions are in error, and what should be fixed so the rest of the (presumably correct) program remains undisturbed. Catch the same defect the minute it is created and the cost to fix it will be minimal.
 
#### Failure Demand ####
From Wikipedia:
Failure demand is a systems concept used in service organisations first discovered and articulated by Professor John Seddon as 'demand caused by a failure to do something or do something right for the customer'. Seddon makes the distinction between 'failure demand' and 'value demand', which is what the service exists to provide. Failure demand represents a common type of waste found in service organizations. [see wiki](http://en.wikipedia.org/wiki/Failure_demand)
 
#### Gold Plating ####
From Wikipedia:
Gold plating in software engineering or Project Management (or time management in general) refers to continuing to work on a project or task well past the point where the extra effort is worth the value it adds (if any). After having met the requirements, the developer works on further enhancing the product, thinking the customer would be delighted to see additional or more polished features, rather than what was asked for or expected. [see wiki gold plating](http://en.wikipedia.org/wiki/Gold_plating_software_engineering)

#### References ####

[Janco Wolmarans notes to Keyblade Team](https://twitter.com/jancowol)
