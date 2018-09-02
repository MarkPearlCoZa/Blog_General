---
layout: post
title: Structured System Analysis and Design UNISA Studies – Chap 4
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA ICT 2621 tag should be considered study notes for my lectures...

Objectives of Chapter 4

Describe the activities of system analysis.
Explain the difference between functional and non-functional system requirements.
Describe three types of models and reasons for creating models
Identify and understand the different types of users who will be involved in investigating system requirements
Determine the kind of information that is required to model system requirements
Determine system requirements through review of documentation, interviews, observation, prototypes, questionnaires, joint application design sessions, and vendor research.
Discuss the need for validation of system requirements to ensure accuracy and completeness and the use of a structured walkthrough.
Key Words & Definitions
logical model – any model that shows what the system is required to do without committing to any one technology
physical model – any model that shows how the system will be actually implemented
system requirements – specifications that define the functions to be provided by a system
functional requirements – a system requirement that describes an activity or process that the system must perform
non-functional requirement – characteristics of the system other than activities it must perform or support, such as technology, performance, usability, reliability, and security
technical requirement – a system requirement that describes an operational characteristic related to an organization’s environment, hardware, and software
performance requirement – a system requirement that describes an operational characteristic related to workload measures, such as throughput and response time.
usability requirement – a system requirement that describes an operational characteristic related to users, such as the user interface, work procedures, online help, and documentation.
reliability requirement – a system requirement that describes the dependability of a system, such as how it handles service outages, incorrect processing, and error detection and recovery.
security requirement – a system requirement that describes user access to certain functions and the conditions under which access is granted.
Mathematical model -  a series of formulas that describe technical aspects of a system.
Descriptive model – narrative memos, reports, or lists that describe some aspect of a system.
Graphical model – diagrams and schematic representations of some aspect of a system.
Stakeholders – all the people who have an interest in the success of a new system.
Transaction – a single occurrence of a piece of work or an activity done in an organization.
workflow – a sequence of steps to process a business transaction.
activity diagram – a type of workflow that describes the user activities and their sequential flow.
synchronization bar – a symbol in an activity diagram to control splitting or uniting of sequential paths.
swimlane – a rectangular area on an activity diagram representing the activities of a single agent.
prototype – a preliminary working model of a larger system.
mock-up – an example of a final product that is for viewing only and is not executable
closed-ended questions – questions that have a simple, definitive answer.
open-ended questions – questions that require discussion and do not necessarily have a simple, short answer.
joint application design (JAD) – a technique to define requirements or design a system in a single session by having all necessary people participate.
group support system (GSS) – a computer system that enables multiple people to participate with comments at the same time, each from their own computer.
structured walkthrough – a review of the findings from your investigation and of the models built based on those findings.
Analysis Activities in More Detail
There are six activities that need to be covered in analysis. They are…

Gather Information
Define System Requirements
Prioritize Requirements
Prototype for Feasibility & Discovery
Generate and Evaluate Alternatives
Review Recommendations with management
Keep in mind that these six activities are usually done almost simultaneously. For instance, one might be defining system requirements while gathering information, etc.

Here are the top key questions the book outlines for each activity…

Analysis Activity	Key Questions
Gather Information	Do we have all of the information (and insight) we need to define what the system must do?
Define System Requirements	What (in detail) do we need the system to do?
Prioritize Requirements	What are the most important things the system must do?
Prototype for Feasibility & Discovery	Have we proven that the technology proposed can do what we think we need it to do? 
Have we built some prototypes to ensure the users fully understand the potential of what the new system can do?
Generate & Evaluate Alternatives	What is the best way to create the system?
Review Recommendations with Management	Should we continue with the design and implement the system we propose?
 

Functional and Non-functional System Requirements
System requirements are all the capabilities and constraints that the new system must meet.

The system requirements are typically divided into functional and non functional requirements.

Functional requirements
Functional requirements are the activities that the system must perform.
They are what the business intends on using the system for.
They are based on the procedures and rules that the organization uses.
See wiki for more info on functional requirements.

Non-functional requirements
Non-functional requirements are characteristics of the system other than activities it must perform or support. There are many different types of non-functional requirements. Some examples of the include:
technical requirement
performance requirement
usability requirement
reliability requirement
security requirement
Have a look at the key definitions at the top of the blog for an explanation of the above requirements.

See wiki for more info on non-functional requirements.

Models and Modelling
The Purpose of Models
Models help discover how a system should work… the following are the major reasons why models are used for system development.

Learning from the modelling process
Reducing complexity by abstraction
Remembering all of the details
Communicating with other development team members
Communicating with a variety of users and stakeholders
Documenting what was done for future maintenance/enhancement
Types of Model
There are three main types of models.

Mathematical Models
Descriptive Models
Graphical Models
Mathematical Models

A series of formula to describe technical aspects of a system
Usually models technical requirements
Descriptive Models

Narrative memos, reports, or lists
Sometimes descriptive models are converted to graphical models for better visualization
A form of descriptive modelling is pseudo code – or structured English to describe an algorithm
Graphical Models

Probably the most useful type of model
Includes diagrams and schematic representations of some aspect of the system
UML is an example of a graphical model.
Stakeholder – The Source of System Requirements
Stakeholders are all the people who have an interest in the successful implementation of the system. They can generally be categorized into one of three groups.

Users – people who actually use the system
Clients – people who pay for the system
Technical Staff – people who support the system
User Stakeholders

Examples of users include…

Business Users – people who capture data – i.e. generate an order
Information Users – people who view data but cannot change it – i.e. someone viewing the progress of an order
Management Users – people who monitor the performance of the business and need dashboards etc.
Executive Users – people who are concerned with the overall aspect of the business/system
External Users – for example, customers who order from home online
Client Stakeholders

Client stakeholders are the people paying/funding the development of the system
Sometimes the client stakeholder is also the executive user, however sometimes it is a third party group that funds the project.
Technical Stakeholders

The people who maintain the system.
Sometimes a technical stakeholder will form part of the development system.
Techniques for Information Gathering
Development of system requirements was initially a four step process…

Identify the physical processes and activities of the existing system
Extract the logical business function that was inherit in each existing physical process
Develop the logical business functions for the approach to be used in the new system
Define the physical processing requirements of the new system
A major disadvantage of this approach was the time it took to complete.

Also, often system analysts would simply automate the existing procedures without any innovation.

Avoid “analysis paralysis: by focussing on the new system requirements from the beginning.

Now days, analysis focuses on certain themes and uses various techniques to develop the logical model of the system. This is done by focussing on question themes.

Question Themes

What are the Business Processes?
How is the Business Process Performed?
What Information is Required?
The processes to answer the above questions can usually be achieved by doing the following…

Reviewing existing reports, forms & procedure descriptions
Conduct Interview & Discussion with Users
Observing and documenting business processes
Building prototypes
Distributing & collecting questionnaires
Conducting Joint Application Design Sessions (JAD)
Research Vendor Solutions
Reviewing existing reports, forms & procedure descriptions

Study best practices in Industry Journals
Study existing reports & forms used in the organization and understand the data that is being captured and why it is important.
Conduct Interview & Discussion with Users

Try and have at least two team members attend interviews so that they can verify their results

Things to do before the interview

Establish the objective for the interview
Determine correct user’s to be involved
Determine project team members to participate
Build a list of questions and issues to be discussed
Review related documents and materials
Set time & location
Inform all participants of objective, time & locations
Things to do during the interview

Dress appropriately
Arrive on time
Look for exception and error conditions
Probe for details
Take thorough notes
Identify and document unanswered items or open questions
Things to do after the interview

Review notes for accuracy, completeness and understanding
Transfer information to appropriate models and documents
Identify areas needing further clarification
Send thank-you notes if appropriate
Maintain an open-items list for unresolved problems and questions that came up in the interviews

Observing and Documenting Business Processes

Observe business processes in action
Document Workflows with Activity Diagrams
Building Prototypes

There are many different names for prototypes including…

thowaway prototype
discovery prototype – used for a single discovery objective and then discarded after the concept has been tested.
design prototype
evolving prototype – are prototypes that grow and change and may eventually even be used as the final, live system
Effective prototypes usually have the following attributes.

Operative – should be a working model and display look & feel
Focussed – should test a specific concept and focussed on its objective
Quick – Should not take to long to develop
Distributing & Collecting Questionnaires

Questionnaires include closed & open ended questions.
Limit the number of open ended questions (rather use them in interviews)
Conducting Joint Application Development

See wiki for more info on JAD.

The following people & groups may be involved in a JAD session…

JAD Session Leader
Users
Technical Staff
Project Team Members
One of the dangers of JAD is the risk involved in expediting decisions because the objective of a JAD session is to come to a conclusion quickly on policy decisions & requirements, sometimes decisions are not optimal however JAD sessions have been largely successful in reducing project development efforts & shortening the schedule.

Research Vendor Solutions

There may already be a solution on the market that solves the existing problem
The danger is that an off the shelf solution may not solve all of the problems so proper investigation is necessary
Try and get the following about a product before buying a solution

Technical Specifications
Demo or Trial of the System
References of Existing Clients who use the system
An on-site visit
Printout of screens & reports
Validating the Requirements
It is important to validate system requirements before development begins as it can be very expensive to change the system requirements once programming has commenced.

There are various techniques to validate information systems, one such technique is called a structured walkthrough whereby the analyst run through the system/sub system step by step and is reviewed by a panel. (see wiki for more info)

In a structured walkthrough, one should have a nonparticipant act as a “librarian” to record all errors, comments, and suggestions.

Once a walkthrough ahs been completed it is important to have a follow-up which is any corrections are made. If there are major issues an additional walkthrough with the amendments may be required.