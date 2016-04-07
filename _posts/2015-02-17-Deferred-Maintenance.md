---
layout: post
title: Eskom, Deffered Maintenance and your Technical Debt Negotiations
tags: Design
category: General
---
### Deffered Maintenace ###

##### Eskom & Load Shedding #####

In recent weeks South Africans have become all to familiar with the concept of load shedding - a process whereby the national electricity provider turns off parts of the countries electricity supply so that we don't have a [total grid melt down](http://www.timeslive.co.za/local/2014/11/03/load-shedding-is-to-avoid-grid-blackout-eskom). It sounds extreme and it is. It is going to have a major impact on South Africa's economy, and at this point it is necessary.

So how did we get to the point where we had to implement such an extreme measure? Two words... Deffered Maintenance.

As [explained](http://www.techcentral.co.za/eskom-commences-load-shedding/53593/) by a representative from Eskom...

> There is a need for load shedding because Eskom has deferred maintenance to its power plants for the last 5 years (since 2010). 

In [another interview](http://mybroadband.co.za/news/energy/116962-anc-government-contributed-to-power-crisis-eskom-ceo.html) with a representative from Eskom they compared the power crisis to a car... 

> If you continue to drive it without maintaining it, it will carry you, but at some point it breaks down. I think this is what is happening with many generating units of Eskom.

##### Why deffered maintenance at Eskom? #####

What's interesting about the deferred maintenance situation is the word **'deferred'**. Eskom knew they were meant to do maintenance - but decided to delay it. Several interviews with Eskom employees place the decision to defer maintenance with the South African Government. As explained by Eskom, they raised the issue of needing to do maintenance, and Government told them to instead 'keep the lights on'. 

I can imagine the discussion that went on between Government and Eskom went something like this...

~~~
Eskom: We need to do maintenance on the generators or else it will break down  
Government: When will it break down?  
Eskom: Not right now, but if people continue to use electricity it will break down sometime in the future
Government: Ok, let's defer the maintenance discussion till later, we have more important things to worry about right now like keeping the lights on  
Eskom: Ok, it's your call since you are our bosses but the maintenance needs to be done sometime or else...
Govenrment: Great, let's worry about it later then  
~~~

##### Deffered maintenance with Software System Maintenance #####

This pattern of deferring system maintenance is not unique to Eskom and it's generators. Businesses around the world are deferring maintenance on their software systems. I've heard of similar discussions happening weekly with a number of development teams.

~~~
Dev Team: We need to do maintenance on this system or else it will break down  
Business: When will it break down?  
Dev Team: Not right now, but if people continue to use it, sometime in the future  
Business: Ok, let's defer the maintenance discussion till later, we have more important features we need to worry about right now  
Dev Team: Ok, it's your call since you are our boss but maintennace needs to be done sometime  
Business: Great, let's worry about it later then.  
~~~

##### Who's to blame when deferring maintenance? #####

So the question has to be asked - who's to blame when maintenance is deferred? The typical responses I get from software developers when posed with this question is that blame lies solely with business. 

> We warned business that the maintenance needed to be done. They acknowledged our warning and didn't prioritize it. We only do what business prioritizes.

The problem I have with this response is that often business doesn't fully understand what they are doing. They are typically not technical, the implications of deferring maintenance aren't properly explained and they aren't able to decern when maintenance is critical or just nice to have. 

Put it another way, asking my 3 year old son to choose between eating his vegetables or sweets and expecting him to choose his veggies isn't going to happen - he doesn't understand the implications. Likewise business doesn't understand the implications either.

So, if most business people don't really understand what the technical implications are, what heuristics do they use when deciding on whether to defer maintenance or not.

##### Body language, conviction and pushback ####

I suspect most business people rely on body language and conviction when determining if something is important. If something is really important they expect the emotion when conveying the message to be a little higher than if it isn't. If they think someone is bluffing, they might push back a little bit to determine how convicted the person is to the message. 

> If you told me the house was on fire and I didn't believe you and had no way of checking myself, I would tell you to stay in the room.  
> If you stood their without any emotion patiently waiting, I would probably think you were lying...

Ironically, most technical people I know are very poor at using body language and conviction to convey an important message. When business pushes back a little to guage our conviction, we accept things without challenging them or showing any real conviction. They then assume that the maintenance wasn't that important and move back to their features. 

### Techniques to avoid deferring maintenance ###

I've listed a few techniques below that I have seen used effectively to avoid deferred maintenance. I would be interested in hearing of others.

##### Time box maintenance work #####

When prioritizing work bring up maintenance issues. Be specific and clear about the commitment of how much time the maintenance will take. If you are unsure of the time place a time box on the work so that business doesn't have to worry that they are giving the go ahead for a potentially infinite piece of work (yes, they are scared of you secretly re-writing the entire system for the next 3 years, they don't trust you not to do this). 

##### Bargain deferring work #####

Try bargaining when business says no. Business is used to bargaining, they often use it when negotiating a price on something. For instance, this would be a typical price bargaining example:

~~~
Business Person A: I'll give you 10 bucks for that widget. 
Business Person B: No way, this widget is worth at least 50.
Business Person A: How about 20. 
Business Person B: 45 and its yours. 
Business Person A: Okay, 43 and we have a deal. 
Business Person B: Deal
~~~

Most software developers are not good bargainers. We think in binary - it is either on or off, true or false. This is not how busienss typically looks at the world.

Next time you hear the "let's defer till later" instead of accepting it try something along the following lines...

~~~
Dev: look, this is really important how about just deferring this till next week, but no longer, if we leave it longer it is going to be expensive. 
Business: We really need to get these features out so we can make money. Let's talk about this another time. 
Dev: No, you are not understanding, this is CRITICALLY important, the latest I can professionaly allow you defer this is for 3 weeks.  
Business: Ok, if we slot it in for 4 weeks is that alright?
Dev: Deal
~~~

##### Get a little emotional #####

The final technique I'm going to mention is to get a little emotional. That doesn't mean throwing chairs at people or crying (although if lives are on the line I wouldn't rule it out). When business tells you to defer maintenance, raise the tone and volume of your voice and re-address the maitenance issue. Use [body language](http://www.businessballs.com/body-language.htm) to show that this is important to you. It's a mental cue to business that this is something they need to reconsider.


