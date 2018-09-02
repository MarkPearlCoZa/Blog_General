---
layout: post
title: Moving from Tortoise to TFS
tags: 
category: General
---
The Past

A few years ago my small software company made the jump from storing code on a shared folder to source code control. At the time we had evaluated a few of the options and settled on Tortoise SVN. The main motivation for going the SVN route was that we found a great plugin for Visual Studio that allowed us to avoid the command prompt for uploading changes (like I said we are windows programmers… command prompt bad!! Winking smile) and it was free.

Up to now we have been pretty happy with SVN as it removed many of the worries that I had about how safe my code was on a shared folder and also gave us the opportunity to safely have several developers work on the same project at the same time. The only times when we have been unhappy has been when we have had SVN hell days – which pretty much occur when you are doing something out of the norm and suddenly SVN just won’t resolve conflicts or something along those lines. This happens once every 4 or 5 months and is not necessarily a problem caused directly by SVN – but a problem augmented by SVN. When you have SVN hell days you want to curse SVN!

With that in mind I recently have been relooking at our source code control. I have explored using GIT and was very impressed by it and have also looked at TFS. From a source code control perspective I don’t want to get into a heated discussion on which one is better – but I do want to mention that I wear two hats in my organization – software developer & manager, and with the manager hat on I tend to sway the TFS route.

So when I was given a coupon to test DiscountASP.Net Team Foundation Server Service for a year, I thought it was the perfect opportunity to try TFS in a distributed environment and also make the first step towards having an integrated development management system.

Some of the things that appeal to me about DiscountASP’s offering are the following…

Basic management / planning facilities like to do lists inside Visual Studio
Daily backup of data on the server – we are developers, not IT managers and so the more of this I could outsource the better
Distributed solution – all of us work remotely and so this was a big one as well.
Registering and Setting Up with DiscountASP.NET

The whole registration process was simple and intuitive. The web interface is not the most visually impressive one, but it is functional and a few seconds after I clicked the last submit button a email was sitting in my inbox giving me my control panel username and suggesting that I read the “Getting Started” article. The getting started article was easy to read and understand so no complaints there either.

Next to set my dev environment to work. With a few references to the getting started article I had completed the whole setup process in a matter of minutes. Ten minutes after initiating the whole thing I was logged into VS2010 and creating my first TFS project. With the service that I signed up for, I have access for 5 users – which is sufficient for my internal needs. So from what I can tell, to set the rest of us up on the system I just need to supply them with their user credentials and url.

My Concerns Resolved

1) Security

So, a few concerns I had about the service. First and foremost – is it secure?

I would hate for someone to get access to our code and the whole idea of putting it up on the internet is a concern for me. Turning to the Knowledge Base on the DiscountASP website this is one of the first question I can see answered. According to them it is secure. I have extracted their comment below regarding this.

Our TFS hosting service is secure.

We only accept HTTPS connections ensuring that any client-server data transmission is encrypted.
At the network level, all of our systems are protected by multiple Juniper firewalls, Tipping Point's Intrusion Detection System (see Tipping Point's case study of our use here), and we also employ DDoS mitigation to add extra layers of security.
Additionally, physical access to the servers is tightly restricted. Please see the security section of this Knowledge Base article for further details.

2) Web Portal Access

The other big concern I have is regarding web portal access. In the ideal world I would like to be able to give my end users access to a web portal for reporting bugs etc. When I initially read through the FAQ of the site it mentioned that there was web portal access – but from what I can see this is just for “users”. Since I am limited to 5 users for the account, it would not be practical to set up external users that we could get feedback from on bugs etc. I would be interested if this is possible – and if so if someone could post it in the comments it would be much appreciated. If this isn’t possible, it is a slight let down as we rely heavily on end user feedback to get feedback and it would have been ideal to have gotten this within the service.

Other than those two items, I didn’t have any real concerns that were unresolved.

So where do I go from here?

So time passed by from the initial writing of this post and as work whirred in and out of my inbox I have still not had a proper opportunity to give the service a test run. Recently though things have began to slow down and then surprise surprise I had another SVN Hell day. With that experience I had a new found resolve to get our team on TFS and so today we are going to start to use the service as a team. I am hoping that I do not have TFS hell days – but if I do, I will be sure to write about them.

In short - the verdict is still out on whether this service is going to be invaluable to my business or whether it will create more headaches than it is worth BUT I am hopping it will be an invaluable service. I will only really be able to determine that in a few months… till then!