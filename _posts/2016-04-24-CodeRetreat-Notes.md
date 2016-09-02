---
layout: post
title: Code Retreat Notes
tags: Learning
category: Misc
---
## Purposes / Outcomes of Code Retreats

- Emergent Design  
- Pair Programming & TDD
- Learn different languages
- Legacy code

### Emergent Design Outline

- 6 sessions, 45 minutes each with 10 minute retro after each session  
- After each session delete code and then stand up  
- Should have a different partner for each session  

#### Outline of Sessions

1. No Constraints / Understand the problem (Solve Conway's Game of Life)  
2. No method longer than 4 lines   
3. No primitives across method boundaries & no if's
4. Ping Pong with Safe Refactoring 
5. Evil coder 
6. No Constrains / Pair up with original partner  

-------------------------------------------------------------------------------------------------------------

## Internal Code Retreats

### General suggestions

- Company teams that have an element of 'support' that they provide should make sure that not all 'technical' members of the team attend the Code Retreat on the day. If not there is a high probability that someone in the team will be 'called' out during the day for support calls which is disruptive.  

- Having a financial cost per person to attend the Code Retreat increases the chances of people staying the whole day.  

- Being specific on what the minimum skill level of attendees should be increases the general experience. We had QA's & BA's attend a Code Retreat, we were not specific enough on the level of skill's needed to get value from the day which ended up in a skills mismatch on the day.  

### Minimum skills to attend

- Know what object orientation is  
- Know how to declare an 'object' in that area
- Has an interest in deepening their 'developer' skill set (you don't need to be a dev, but you should be interested in being able to grow your 'developer' skills  

### Timings for Company Internal Code Retreat  

9:30 - 9:45 	- People Arrive, Setup, Name Tags, Find a partner  
9:45 - 10:30 	- First Session  
10:30 - 10:45 	- Welcome & Introduction (Perfect Practice)  
10:45 - 11:30 	- Second Session  
11:30 - 11:40 	- Retro (Small Circle)  
11:40 - 12:25 	- Third Session  
12:25 - 12:35 	- Retro (Small Circle)  
12:35 - 1:34 	- Lunch
1:35 - 2:20 	- Fourth Session  
2:20 - 2:30 	- Retro (Small Circle) 
2:30 - 3:15	- Fifth Session  
3:15 - 3:25	- Retro (Small Circle) 
3:25 - 4:10	- Sixth Session  
4:10 - 4:20	- Retro of the Day  
4:20 - 4:30	- Closing Retro (Big Circle)  



-------------------------------------------------------------------------------------------------------------

## Session Explanations

### Ping Pong  

Write test first, get the test to pass, refactor safely  

### No method longer than 4 lines

### No primitives across method boundaries


### No if's  

- No if statements  
- No switch statements  

### Safe Refactoring  

### Vanilla (plain old)  

### 1969 (compile twice)  

### Ping Pong    

- No primitives across method boundaries  
- Tests for customers first  
- No conditional branching  

(One person writes the test, the other person gets the test to pass while trying to intentionally not solve the problem)   

-------------------------------------------------------------------------------------------------------------

## Preparing for a Code Retreat

### Things to do

#### Must do well in advance  

- Advertise event & get registrations  
- Book room and confirm room layout (see below)  
- Confirm dietary requirements  
- Organize giveaway prizes (if any)  

#### Must do day before event

- Send out reminder email
- Confirm materials for on the day are ready

#### Must have on the day

- Print Conway's Game of Life Rules on A4 paper for hand out (at least 1 per person)  
- Print Conway's Game of Life Poster (2 or 3 for the wall)   
- Make sure screen / projector that can show a timer that everyone can see  
- Buy name labels / name tags + Sharpies to write names  
- Timer for sessions that can be put on screen  

#### Nice to have on the day

- Print posters with "4 rules of simple design"  
- Print posters with "4 stages of naming"  
- Prizes for giveaways at end of day  

### Food Suggestions

- Avoid food that spikes energy levels and then drops you afterwards (sweets, chocolates, pizza)  
- Have fruit or slow energy release bars in the morning  
- Light lunch  
- Chocolates etc can be made available last hour of the day  

### Marketing / Communication

#### Examples of email sent out the day before the event...

~~~
Hi, you are getting this because you are lucky enough to be registered for the Code Retreat tomorrow.
 
Just some things to remember
- We start in Purple 1 & 2 at 9:30 (please don’t be late)
- We will finish by 16:30

Bring an external keyboard if you have one (this makes pairing easier)
- Bring your laptop set up with you IDE, refactoring tool of choice as well as a test framework (C# or JavaScript)
- No need to bring lunch, we will be providing it
 
We have limited attendance to 20 people, currently we have 16 confirmed – if you have a colleague who would like to attend who isn't on this mail let us know – we will work on a first come first serve basis.
 
See you tomorrow!
 
Kind Regards
Mark
 
If anything is unclear don’t hesitate to email me!~~
~~~

#### Examples of emails sent out to promote the event...  

~~~
“A Code Retreat is a day-long practice event focused at becoming a better programmer.”
 
We will be having our first day long Code Retreat next Friday (2nd September) with a specific focus on orientated emergent design and pair programming.
The event is limited to 20 people on a first register basis.
To register put your name on the Code Retreat list by the “What’s happening in engineering Experience Auckland board”
 
Who should attend?
The event is open to anyone regardless of official role (BA / QA / etc.). 
You should have basic knowledge of JavaScript or C# (you should know at a minimum what a class is, how to declare variables, how to do a loop without having to google it)  
 
What will you learn?  
You can expect by the end of the event to have a deeper understanding of object oriented emergent design and pair programming.
 
How long will it be?
- The event starts at 9:30 and will end by 16:30  
- Lunch will be provided.  
 
What to bring on the day…
- External Keyboard  
- Laptop (if you have one)  
- C# or JavaScript IDE Setup with test framework installed and running (NUnit, MSTest, etc)  
- Refactoring tool of choice (e.g. Resharper)  
- Open mind, willingness to learn & share  
~~~

### Room Layout

- Desk layout where two people can sit comfortably with keyboards next to each other
- Electrical extensions at each desk to plug computer / laptop in  
- No water/fluids on desks, separate table in the room that has glasses & water

<img class="img-responsive" alt="Suggested Room Layout" src="{{ site.url }}/assets/images/CodeRetreat-SuggestedRoomLayout.jpg">

#### References ####

- <a href="{{ site.url }}/assets/documents/CodeRetreat-GOL-Projector.zip">Conway's Game of Life for Projector</a>  
