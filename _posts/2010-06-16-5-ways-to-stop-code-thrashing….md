---
layout: post
title: 5 ways to stop code thrashing…
tags: 
category: General
---
A few days ago I was programming on a personal project and hit a roadblock. I was applying the MVVM pattern and for some reason my view model was not updating the view when the state changed??? I had applied this pattern many times before and had never had this problem. It just didn’t make sense.

So what did I do… I did what anyone would have done in my situation and looked to pass the blame to someone or something else. I tried to blame one of the inherited base classes, but it looked fine, then to Visual Studio, but it seemed to be fine and eventually to any random segment of code I came across. My elementary problem had now mushroomed into one that had lost any logical basis and I was in thrashing mode!

So what to do when you begin to thrash?

1) Do a general code cleanup – Now there is a difference between cleaning code and changing code . When you thrash you change code and you want to avoid this. What you really want to do is things like rename variables to have better meaning and go over your comments.

2) Do a proof of concept – if cleaning code doesn’t help. The  you want to isolate the problem and identify the key concepts. When you isolate code you ideally want it to be in a totally separate project with as little complexity as possible. Make the building blocks and try and replicate the functionality that you are getting in your current application.

3) Phone a friend – I have found speaking to someone else about the problem generally helps me solve any thrashing issues I am having. Usually they don’t even have to say anything to solve the problem, just you talking them through the problem helps you get clarity of mind.

4) Let the dust settle – Sometimes time is the best solution. I have had a few problems that no matter who I discussed them with and no matter how much code cleaning I had done I just couldn’t seem to fix it. My brain just seemed to be going in circles. A good nights rest has always helped and often just the break away from the problem has helped me find a solution.

5) Stack overflow it – So similar to phone a friend. I am really surprised to see what a melting pot stack overflow has been and what a help it has been in solving technology specific problems. Just be considerate to those using the site and explain clearly exactly what problem you are having and the technologies you are using or else you will probably not get any useful help…
