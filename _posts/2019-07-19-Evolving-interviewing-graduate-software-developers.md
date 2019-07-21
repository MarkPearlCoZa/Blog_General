---
layout: post
title:: Evolving interviewing graduate software developers
tags: 
category: General
---

Today I want to spend some time thinking through what to look for when hiring a graduate software developer. Prior to being involved in our graduate programme I would never have thought this was an interesting question. As I dig more into it I'm realizing what an interesting question it is.

## Before interviewing graduate software developers...

Before I go into the evolution of interviewing graduate software developers let me quickly go through what I used to look for when interviewing software developers in general. Let me share a snapshot of my normal interview process at around 2016.

The goal was to identify a candidate that would be contributing as soon as possible to the team that was also a good fit for the team. This process was used for experienced software engineers (people that had a couple of years under their belt) and was a 4 step process. We would look at:

> The goal was to identify a candidate that would be contributing as soon as possible to the team that was also a good fit for the team.

1) Cultural fit and software process mindset  
2) Technology competency  
3) Coding skills assessment  
4) Team fit  

Let me dig into what we covered at each step.

### Cultural fit and software process mindset

Generally this would be an unscripted conversation. We would talk about what got them into software. What they look for in a team. Why they are leaving their current team / position. How they handle conflict. You get the idea. We would also have a chat about team software processes. What does agile mean to them, when would you adopt a particular team process to making software (Scrum, Kanban, etc.) At the very end I would answer any questions around our company values and how we see the world or anything else they want to know about.

### Technology competency

The next step was a technology competency assessment. Do they know the tech we use, how much of this tech did they really understand and at what level of understanding. Again this would be conversation style with potential whiteboarding. We would talk about the tech stack, there would be some general questions around technology they have used. Things they would do or avoid. Often we would map out a build pipeline or something along those lines.

### Coding skills assessment

Next up was the coding skills assessment. This was usually done using pair programming. We would pick a code kata and see if they could solve it. We would use a form called strong pairing where the candidate would be the navigator and the interviewer the driver. This would give me a good idea on whether they write clean code. Do they use a TDD approach. What they would be like to pair with and so on.

### Team fit

The final step would be a team fit session. The candidate would get to meet the team. We would usually do a "agile game", something where we needed to build something together as a group and collaborate together followed by general Q&A from the team. Post the session the team would get together to share their thoughts. If the team was in favor of proceeding they would get an offer.

### My thoughts around this process 

The challenge with this approach was it was lengthy, generally someone is looking for work as soon as possible and with the multiple stages it took time. Good experienced software developers are in high demand so there was always pressure from our internal recruiters to speed up the process so we didn't loose this person to the competition. 

I'm also not sure how effective some of the steps were. To be honest, retrospectively I don't think I got much out of the culture fit conversations or even the technology conversations. It was also hit and miss with the team fit session, sometimes it went great and sometimes not so great. If team members were poor at asking questions they got canned responses - I've never found anyone in an interview to tell you they don't like collaborating with others or giving good feedback.

I would rate the over all process as a 5 out of 10. Not terrible, but not great.

## Now I have to interview graduate software developers... now what?

When I moved into the graduate space our goal had changed. Instead of hiring experienced practitioners with an expectation that they could deliver from day one, we would hire inexperienced people worth investing in and grow them into the software professionals we wanted.

> The goal had changed, we would hire inexperienced people worth investing in and grow them into the software professionals we wanted.

With this change in hiring goals I suddenly had a problem. Most of my traditional measures for interviewing were no longer useful. 

* Measuirng existing coding skills were not applicable, most graduates have what I call an academic style to coding (lots of comments, immaturely structured solutions), in depth discussions around code construction and design are often beyond the scope of their current abilities. 
* Level of technology competency is largely irrelevant. Because they are new in their career they don't have much technology experience. You realize very soon on that you will be teaching them most if not all of the technology. 
* Team software process experience is minimal. Most candidates have worked in one or two group projects. Often at best a candidate will have a very theoretical idea of scrum or some software methodology. 
* A specific team fit interview doesn't apply. Graduates are not hired into a specific team, instead they enter a graduate programme where they are expected to spend 3 to 6 months with a team before having to move to another team.

So how do you know who to hire? How do you know if someone has the potential to become a great software developer in our company and is worth investing vs someone else?

## Iteration 1 - The bulk approach

### What are we looking for in a great candidate?

The question around who to invest in led us to ask what makes a great software developer? We felt there was a mix of technical, collaboration and problem solving skills. We expected candidates to have some coding skills but we felt that if they were passionate enough about the field this was a space where they could learn and grow.

As iteration 1, we took the approach that we wanted to hire passionate software developers that were great collaborators and problem solvers. Because we were going to invest in their technical skills we were not too concerned about current technical ability provided they had some basic coding skills and a passion to learn.

### Implementation

We settled on a two part interview process which was done as a bulk interview. Following an initial CV scan we identified candidates we felt were worth interviewing. We then invited the top 20 candidates to a group interview day.

The interview day consisted of a group activity (building lego structures as a team) followed by a "cultural interview" where they were asked general questions around collaboration as well as their passion software. The cultural interview was done by two people. 

At the end of the day all the interviewers would get together and share notes and we would pick our top candidates and make an offer.

In the collaboration exercise we would look at:
* How well candidates interacted with others
* Their creativity in solving problems
* Their ability to communicate with their group memebrs
* How dominant / compliant they were, did they override team members decisions, etc.

In the cultural interview we would:
* Ask questions around working in a team
* Their passion around software development
* Why they wanted to work for our company.

### Summary of effectiveness

Looking back at this approach there were pro's and con's

Pro's included:
* It's quick. You can get interviewing a large group of people out in a very short period of time
* It has deversity built in. Becuase you have a group of people interviewing you naturally come out with a mix of people and personalities in selected candidates
* Indications were that we got a good feel for how much people wanted to work at MYOB

Con's included:
* Hard to compare between candidates. Because different people have interviewed different candidates it's hard to compare. Someone that has higher standards / criteria may rank their candidate lower than someone else
* Didn't see much value in the collaboration activity. Candidates know they are being observed, having a collaboration game for 2 hours is not enough for people to stop posing so you really don't know how good someone is at collaboration
* Didn't really get a feel for how passionate people were. Passion is a very ambigous word. In my opinion most people when asked how passionate they are about something will tell you they are very passionate... especially if it leads to a job.
* Have to interview in groups. With the lego simulation this puts you down the road that you need to interview with a group of people. Great candidates are not always available at the same time. Restricting yourself to only being able to interview as a large group can potentiall filter out some great candidates.

## Iteration 2 - The individual approach

### What are we looking for in a great candiate?

After our first intake we re-evaluated what were were looking for in a great candidate. We came up with the following:

1) Should display an endurance to coding. We didn't care what programming language, more that they had "programmed" over a period of time and could endure being in front of a machine looking at code over an extended period of time.  
2) Should be able to think end to end BUT also go deep into an idea. We wanted people that would look at a problem and ask what is it we are actually trying to solve. We then wanted them to be able to get into implementation.  
3) **Should have experience and a skills collaborating with others in a team.* Software is a team sport, we want people that can work with others.  
4) Should be resilient. We want people that can be stretched and recover quickly.
5) Should be a strong problem solver. We are not looking for people that can just "program". We want people that can program to solve actual problems. Sometimes the best solutions don't involve code! 

### Implementation

For iteration we had a 3 step interview process

1) Cultural interview  
2) Systems thinking interview  
3) Code problem

The cultural interview was an in person interview with a set of predetermined questions. The questions covered a range of topics. We wanted to gauge was this person going to add to our culture (were they more than just a coder). We also wanted to know what had attracted them to the industry, what was their motive? How much do they know about us as an organisation? What questions do they ask when handling unknowns? How well do they know themselves and how others perceive them?

The systems thinking interview was an in person problem solving interview. It was specifically designed to not have any code in it. Rather we wanted to see if someone could think end to end. Ask relevant questions and then work at different levels of a system to map out process.

The final step was a coding problem. We would allow a candidate to code a problem. We would then review it, give feedback and see how they adjust. We were establishing at what level is this person's baisc coding skills. How do they handle feedback?

### Summary of effectiveness

Approach 2 had certain trade offs again

Pro's included:
* Had a much better idea of how someone problem solves and their ability to think end to end and then go deep into a problem.
* Were able to interview people individually at different times. This meant we were able to have interviewers in more than one interview which allows them to compare against candidates

Con's inlcuded:
* Time intensive. Because we reduced the number of interviewers it was a way more time intensive process. 
* Some of the quesitons in the cultural interview were poorly formed and added no value. We had questions around how they would approach solving a problem, this was pretty useless. It was way more useful seeing them actuall solve a problem.
* Got very little value from reviewing their code. The intial intention to give feedback and see them adjust didn't work well in this instance.

## Iteration 3 - Individual approach with validation

After our second iteration I was more comfortable with the interview process and the reliability of candidates coming through. In a random conversation with someone I was sharing a taxi with who worked in this field they suggested we look at introducing a particular cognitivie test to our approach. Her comments were in over a decade of doing interviews this type of test was the only one she had found reliable.



How does this change our approach to interviewing?
- You can still focus on culture, do they add to our culture
- Have they demonstrated some sort of endurance to coding (university coding course, internship, hobby programming)
- Are they a strong critical thinker
- How much time will we invest in them before we can get value... what are the foundational principles we are looking for? If someone hasn't demonstrated that they are a great software developer... what attributes would give us an indication that they will be one eventually?

First attempt we came up with
- Have they demonstrated an tendency to code
- Are they a collaborator, can they work with others[
- Do they like the industry we operate in (have they shown an interest in Accounting, what problem we solve, the company)
- Can they think of a problem end to end and then go deep and into the nitty gritty's
- Are they passionate about software

Second attempt 
- Are they show an apptitude to be able to learn new concepts quickly

Third attempt
- Have they demonstrated an tendency to code
- Do they ask questions or make assumptions
- Are they good at problem solving, given a lot of unknowns can they navigate their way through to a solution
- Domain Modelling. Are they able to conceptualize a domain and handle how behaviour and data
- Knowledge Representation. Can they represent knowledge effectively so it is easy to consume
- Efficiency in problem solving - How easily can they solve a problem
- Abstraction / modularity - Can they think at different levels, are they able to think abstractly about a problem and then give concrete examples of abstract concepts
- Novelty / creativity - Can they look at a problem in different angles
- Categorization - Can they categorize things, group them
- Communication skills with experts in other domaions - Can they communicate with other effectively, verbal, written, etc.
- Adoption of good practices in software engineering - Do they have great software engineering practices

- 
