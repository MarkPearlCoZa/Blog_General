---
layout: post
title: SQL Source Control – Why buy the DB products and go through their Webinar
tags: 
category: Tech
---
Before I go into the contents of this post I would like to give a quick disclaimer – I have been asked to give review of the SQL Source Control webinar, my payment of the review is a free license of SQL Source Control from Red Gate. It’s great to have the license but I have no need for it as my company has already purchased a license of SQL Toolbelt from Red Gate which includes SQL Source Control. I might come across as a bit of a Red Gate fan boy, but it is because their tools have saved my bacon a few times instead of me getting the free license…

Why SQL DB Products from Red Gate
We had a mini disaster a few months ago when we rolled something out to production and a core component of the system just didn’t work. We ended up having 3 senior developers huddled around a monitor trying to determine the cause of the issue – we had already burned an hour or two on trying to debug the issue but could see what was wrong. We had a hunch that it had something to do with one of our SQL update scripts not working correctly against our production schema as the system worked fine on our PostDev environment but we could just not see what was different or missing.

Time was absolutely against us and after exhausting all other options in a last ditch effort to find the issue we downloaded Red Gates SQL Compare and ran the demo version to compare our PostDev Database Schema to our Production Database Schema. In under a minute we knew exactly what the issue was and with a click of a button we had it fixed. The fact that we had no prior training on Red Gates SQL compare at that point and yet were able to use it effectively under pressure is a tribute to how much Red Gate has embraced their philosophy of creating ingeniously simple tools. After that experience we happily ordered and paid for our SQL Toolbelt license and have not looked back since.

Why try the Red Gates Webinars
In the book Pragmatic Thinking & Learning (a great read), Andy Hunt talks about how different people have different primary learning modes. The three main types of learning modes are…

Visual
Auditory
Kinesthetic
I am definitely a visual / auditory learner – I learn more from seeing a demo of a product and asking a few questions than I do from reading a technical brief. This is one reason why the webinar appealed to me – it’s better than just watching a video because you can ask questions and interact with the presenter, closing the feedback loop.

Red Gate currently has a few webinars it offers which include the following titles…

“Whatever your source control system – use it to version control your database”
“Repeatable deployment without fear of data loss”
Each webinar consists of two parts, a demo and then a Q&A section. The demo is pretty much a quick overview of the tool with a demo scenario – I found it a good way to get a basic idea of how the tools works, but the section that I really enjoyed in each webinar was the QA section – I learned a ton of things, and it highlighted things that I missed that other Devs had concerns about that were relevant.

For this review Red Gate asked if I would sit through one webinar and blog about what I learned, but I actually ended up sitting through both just because I have a real interest in getting the most from these tools. Without giving to much away, at the end of each webinar I had a good starting point.

In addition, 3 things that stood out to me that I was not aware of before the webinars were…

With SQL Source Control tool conflict resolution in the tool is currently at an object level
The dedicated model is the preferred model for SCC of the DB
For SCC with Git you can only view the history via Git Console, but with TFS and SVN you can view the history in the tool
There are a bunch of other gems in there, but I am going to leave them up to you to discover.

Going forward what would I like to see?

A webinar I could not find that I would really enjoy is an example of implementing these tools into continuous integration. Red Gate has a document targeting continuous integration but to see an example in action would be really useful. If they don’t do one, maybe I will Winking smile

My next big thing with the team I am on is to integrate the Red Gate tools with my CI server and a webinar on that would be great.