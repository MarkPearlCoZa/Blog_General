---
layout: post
title: A real world example of how not to develop software and how InRule can save the day.
tags: 
category: General
---
A friend of mine works for a large bank… about a year and a half ago they needed a new system developed for their division. They went through the normal process of using one of the recommended service providers to develop the system and this was their experience, which is still typical with most institutions I know…

For the first few months development of the system seemed to be progressing along fine. They had meetings, business analysts put things on paper and the developers nodded their heads and promised that everything they asked for could be done.

The service provider developing the system used the classical waterfall approach and had documented everything upfront and got it signed off. There was a fair amount of time from initial documentation till they produced anything that could be tested by the bank and by the time the service provider got the first version installed on the banks machines, business rules for the bank had changed and the system could not be used ;-(

When the bank pointed out that what they had now was not usable the service provider brought out the specification document that was well over 6 months old and said they had met those requirements and any modification to the system would need to be paid for as they could not help it if the business had changed. They then charged a premium rate to retro fit the new business rules.

Because the system initially developed was brittle, it took quite a while to make the changes needed and to check that they had not broken anything. The changes needed to be done by a developer and so cost a premium rate. When these changes had been properly implemented, once again they rolled out a test for the bank and once again the business rules for the bank had changed and the system could not be used.

This is how it has gone on and up to the point of writing this document they still do not have a system that works properly. The bank has spent a lot of time and money in getting what they have but is quickly losing its patience.

At some point it is inevitable that they will give up on the system, realize that they will never get the solution working with their current methods and either scrap the whole thing or try another service provider.

For me, this highlights the major challenge of developing software for business. Because most businesses are changing continually, the systems they want need to be developed in such a way that they can change continually as well. As developers and solution providers we need to implement processes and use technology that meets these challenges head on.

Where did they go wrong?
The question dares to be asked, where did the service provider go wrong?

Was it because they used the waterfall approach?

Should they have been using Scrum of an agile methodology?

Was it how they wrote the software, or the platform they used?

Now, before I go on an agile promo I need to state that I think the waterfall approach has a place (a very small and specific place) in software development, and while they would have benefited from having a more agile approach (probably scrum in this case), I do not believe it would have solved the root cause of the problem. In my opinion, all that agile would have done is highlight what the root cause was quickly, and in this instance it is the thing that so often stings us developers, and that is BUSINESS RULES CHANGE. The business was changing far too rapidly to allow for a static system and a static rules engine. 

Where was change occurring?
While a lot of focus is put on developers designing systems that can handle a technology change, from my experience, the majority of changes for business applications are not at a technology level.

It is very rare for a business to call me up and tell me they would like me to change the underlying database or the base framework of the system. This does not mean that I don’t develop system to accommodate technology changes. I do, but they are few and far apart.

In this instance the change was occurring at a business level. All the changes after the initial release were happening at a business rules level, yet because these business rules had been tightly coupled with code, it caused the system to become brittle and expensive to modify. Those developing the system and failed to realize this and so had not incorporated change adequately in the solution.

With change in business rules inevitable, as developers we need to develop systems that inherently handle change. I like to call this the OC principle at a systems level. 

My take on the OC Principle at a systems level
For those of you familiar with object oriented software methodologies, you should be familiar with the Open/Closed (OC) principle (part of SOLID). It states…

“Software entities should be open for extension, but closed for modification.”

While the open / closed principle can be applied at a code level, it can also be applied at a system level. Ideally we want to develop systems that are easy to extend, but closed to modification.

For me a good system for business should not require a developer to have to come and make code modifications every time there was some sort of change in business process. The better the system, the less you should need to see the developers.

Microsoft’s designing products that support the OC Principle
In recent years I have seen this concept of allowing to add extensibility to applications emerge through the ranks of Microsoft.

MEF (Managed Extensibility Framework) is one way of providing technology that can assist in extending an application without seeing its guts (yes, you see code, but not the applications code).
Another solution would be Windows Workflow which had a poor start initially, but a technology that I am seeing more and more in the wild.
While I see value in these technologies, one major issue I still have is that they are developer centric. So, while they walk you down the path of designing OC systems, when you do want to extend the application, you still need a developer and usually Visual Studio to get anywhere.

Now, I am not advocating removing developers from the equation totally… since I am a developer it would be stupid for me to promote such a thought, but as a developer I like to deal with challenging problems, I do not like maintenance work.

The majority of business rule changes I see are maintenance work. It is making slight tweaks here or there to allow for an exception or a slight change to business rules that will add value to business. These changes I would be more than happy to hand over to someone who is less technical and more involved in the business on a day to day basis. 

Have you ever looked at InRule for Business Rules?
Recently I had a look at a product called InRule which I believe offers a compelling solution and something that helps address the OC principle for business systems. If you are someone who develops .Net applications and are tired of “maintenance work” that keeps you away from the real problems then it is something worth looking into.

In a future blog post I will add my own obligatory “Hello World” example of InRule focussed at developers - for a more detailed list of examples I would recommend you download a trial of the product from their site as they will give you temporary access to a ton of online help materials and samples.

I have also seen a range of blogs on the product in circulation including ones by James Hare & Bill Osuch.

But more important than looking at my HelloWorld post is grasping the concept that many of the business rules in InRule can be formulated and maintained by business users, not developers.

This to me is where the real value is achieved from InRule and is where InRule could have saved the day for the service provider at the bank. If the service provider had used InRule, they could have developed the system to handle the changing business rules in a dynamic nature.

Conclusion
In hind sight, there were a number of things I think the service provider did wrong, that has caused the project to fail.

A different project management approach would have been one of the obvious solutions.

Also, the fact that it took several months to change business rules in code already smells of tightly coupled code and bad OO design.

In addition, abstracting the business rules engine out to be externally managed by someone other than a developer would have also been a plus.