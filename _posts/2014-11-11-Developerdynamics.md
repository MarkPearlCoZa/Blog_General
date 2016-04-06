---
layout: post
title: Developerdynamics
tags: Agile
category: General
---

#### What is Developerdynamics ####

In the physical world, aerodynamics is the [act of making something more flowable around the air. i.e. making it so that it can get less drag (going against) from the wind](https://answers.yahoo.com/question/index?qid=20100513200949AANwYxB). Software development also has a flow but instead of flowing through air, it flows through people and the tools they use. Developerdynamics is the act of making software development more flowable through people and their tools.

#### Identifying how fast you want development to flow ####

When designing a vehicle, it is important to identify how fast that vehicle is intended to travel. A vehicle that is designed to travel at 1000 km/h, at a structual level, is significantly different from a vehicle that is designed to travel at 10 km/h.

Likewise with software - it is important to identify at what rate delivery is intended to happen. An organization structure that is designed to deliver production software daily, at a structural level, is significantly different from an organization that is designed to deliver production software once a year.  

Identifying how fast you want development to flow is key to having a sound vehicle to deliver working software.

#### What happens when you make slow things go fast ####

Having a mismatch between a structure and the expected delivery is dangerous. If I were to take a vehicle that was designed to go 10km/h and attach a jet engine to it (I know this is probably not possible, but bear with me), and slowly speed the vehicle up - first I would expect to hear some rattles. As the vehicle got faster I would expect things to start really making a noise and shaking. At some pivotal point strucutral failure would occur. This would happen way before I hit jet engine speeds. When structural failure occurs I would have reached the end of the road - the strucutre would fall apart and everything would come to a sudden stop.

Software development is very similar. Having a mismatch between the structure of the organization developing software and the expected delivery rate is very dangerous. If I were to take an organization that was designed to deliver software once a year and apply a "pressure engine" to it - first I would expect people to start feeling stressed (usually at or around the deliver once a quarter stage). As we place further pressure on them to deliver production software faster to a monthly cadence I would expect things to start really making a noise and shaking (unexpected things would happen in the production system, significant bugs would crop up, people would start blaming each other). At some point, well before we reach a daily delivery cycle organizational structural failure would occur and everything would come to a sudden stop.

With the current popularity in agile methodologies I have seen a huge pressure on organizations to deliver production software faster at a monthly or even bi-weekly. Yet when I take a look at the structural integrity of the organization more often than not they are still strucutred to a quarterly cadence. This mismatch between businesses expectation of delivery and the realistic flow that one can get from a current structure is causing a lot of pain for many people.

#### Designing for Developerdynamics ####

The lesson to learn is that a strucuture that is appropriate for one speed is not necessarily appropriate for a different speed. In fact, certain structures that were extremely helpful at slow speeds may be the cause for structural failure at faster speeds.  

When looking at software development, remember that software flows through people and the tools they use. Being aware of the flow and how to make things more flowable is important. [Kent Beck gave a insightful talk on software gforce's and what structures would effect developerdynamics](https://www.youtube.com/watch?v=KIkUWG5ACFY). Below is an outline of the things Kent said we should start / stop doing depending on the speed of flow we want to achieve. I've added a few my own to his list as well.

#### Yearly Release Cycle ####

##### Start #####

- Looking for a new job

------------------------------------------------------------------

#### Quarterly Release Cycle ####

##### Start #####

- Automated Acceptance Tests  
- Refactoring  
- Continous Integration  
- Development & QA specialist teams

##### Stop #####

- QA at the very end after all features have been developed  

------------------------------------------------------------------

#### Monthly Release Cycle ####

##### Start #####

- Developer Testing  
- Stand-up meetings  
- Cards on a wall  
- Co-located cross functional teams (QA, Dev, BA integrated)

##### Stop #####

- Q/A Department  
- Multiple Deployed Versions  
- Change Request Process  
- Analysis & Build Teams

------------------------------------------------------------------

#### Weekly Release Cycle ####

##### Start #####

- Automated data migration  
- Temporary branches  
- Keystoning  
- Kanban  
- One button deploy  

##### Stop #####

- Test Team  
- Design Document  
- Up-front usability  
- Active release branch  

------------------------------------------------------------------

#### Daily Release Cycle ####

##### Start #####

- Immunization  
- Data-informed usability  
- Feature Flags  
- One piece flow

------------------------------------------------------------------

#### Hourly ####

##### Start #####

- Root cause analysis  
- Deploy on green  

#### Notes ####

- Keystoning is the process of pushing the UI changes to the end of the development of a feature, allowing you to introduce the majority of the feature into the codebase before it is exposed to the general end user  

- Immunization is the process of automatically rolling back a release to a previous stable release if a bug is detected in the current release.
#### References ####

- [Kent Beck on Software Gforce's](https://www.youtube.com/watch?v=KIkUWG5ACFY)
