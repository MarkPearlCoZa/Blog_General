---
layout: post
title: INotifyPropertyChanged in the Domain
tags: Style
category: Tech
---
#### The Post that triggered this response from Janco ####

[Should the Domain Model implement INotifyPropertyChanged?](http://blog.alner.net/archive/2010/02/26/should-the-domain-model-implement-inotifypropertychanged.aspx)

#### What Janco had to say about it ####

I don't have the context you're coming from, and that would probably influence some design decisions.

The fact that INPC isn't contained in a "UI specific namespace" doesn't do much to get away from the original intention of it - which was UI binding. It purely focuses on properties of objects. This works well for CRUD approaches because that's what it is: Updating properties. Therefore, just by using this interface and mechanism it encourages a CRUD approach. If all you want is CRUD, then you probably have DTO's rather than behavioural domain objects anyway. In which case it's probably a valid use case.  

The use of INPC is a giveaway of querying being done through the domain model. I've worked on projects like this in the past - and the approach causes pain. I would rather prefer to use CQRS and not mix behaviour modeling and querying in the same domain model. Also, in DDD the interesting thing is the behaviour of the domain, not just which properties get changed.  

With regards to implementation, I've seen two approaches to handling cross cutting INPC concerns: (1) Using a base class for all entities (and then ending up with a bag of arbitrary properties on the base), and (2) Using AOP. Both approaches have their own uglies and leaky ways, which results in the hands of the implementers being tied in some way.  

I'm assuming the ultimate goal here is for UI binding? If that's the case, isn't that what ViewModels are for?  
