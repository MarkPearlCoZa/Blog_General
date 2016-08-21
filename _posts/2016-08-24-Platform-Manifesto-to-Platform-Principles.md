---
layout: post
title: From Platform Manifesto to Platform Principles  
tags: Design
category: General
---
We are in the process of moving from a product centered development approach to a platform centered development approach. This not only changes how we make things, it also means we need to change our mindset.

To help us along this transition we have adopted a 'platform manifesto' - it's something we have on pretty much every wall in our development space - it's in our face all the time. It goes as follows:  

### The Platform Manifesto

~~~
- Medium term thinking over short term thinking  
- Existing experiences over different variations  
- Capabilities as services over monolith extensions  
- Existing assets over new development  
- Nurture the platform over feature delivery  
- Automation over manual repetition  
- Asynchronous interactions over synchronous coupling  
- Stable technologies over the unproven  
- The greater good over individual objectives
~~~

#### What we have learnt from the manifesto so far...

The great thing about a manifesto is that it is a public declaration to the rest of the world and ourselves about our how we do things as software engineers. Several times in design discussions a colleague has challenged a particular approach, quoting a section of the manifesto to motivate why we should or should not do something. This is a good thing and why we adopted the manifesto in the first place.

While the manifesto has been a great start, we've also noticed some interesting side effects with how it is phrased. It's worded in such a way that it leaves the door open for people to 'not change' while thinking they have. 

One way to explain it is by using the model of **Espoused Theory vs Theory in Use**. Nobody in our development space would say at a particular moment that they have 'short term thinking' - we all espouse to have medium or long term thinking however the reality is that in many situations our theory in use is definitely short term. In that sense the platform manifesto while a great start, still leaves the door open for behaviors and approaches we should not be taking.

### From Platform Manifesto to Platform Principles

Having a platform manifesto was a step in the right direction. It helped highlight what mindsets and approaches we needed to change. We are however moving on to a more strongly positioned stance called our platform principles. 

Right now it goes as follows...

~~~
- Always build functionality as independent re-usable services, accessible via an API
- Always re-use or consume services via their API's  
- Always design services to support asynchronous interactions  
- Everything that is repeated is automated  
- Everything must be built secure  
- Everything must be tested  
- Everything is built to be centrally monitored and audited  
- Everything is logged to a central service  
~~~

### What's changed?

You will notice that we have moved from fairly open and neutral wording to quite strong wording - **Always** & **Everything** are very strong words indeed. From a perspective change we don't just see value in doing things a certain way, this is the de facto way we do it.

### Where to from here?

It's still early days. As the Platform Principles begin to become adopted we will gain further insights into it's strengths and weaknesses. In general I've already seen the benefits of us having the Platform Manifesto. Keeping things at an abstract and principled level allows us to interpret the implementation to our specific problem domain.

### What does your organization do?

I'm interested in finding out how your organization does it? Do you have something similar. Are your overarching principles clear as an engineering team? What have you tried? Please add your comments / insights below.
