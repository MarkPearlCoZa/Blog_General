---
layout: post
title: Structured Systems Analysis and Design UNISA studies – Chap 1
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA ICT 2621 tag should be considered study notes for my lectures...

Objectives of Chapter 2

Explain the purpose and various phases of the traditional systems development life cycle (SDLC)
Explain when to use an adaptive approach to the SDLC in place of the more predictive traditional SDLC
Explain the differences between a model, a tool, a technique, and a methodology
Describe the two overall approaches used to develop information systems: the traditional approach and the object orientated approach
Describe the key features of current trends in system development: the Unified Process (UP), Extreme Programming (XP), and Scrum
Explain how automated tools are used in system development
Key Words & Definitions
project – a planned undertaking that has a beginning and an end and that produces a desired result or product
systems development life cycle (SDLC) – the entire process of building, deploying, using, and updating an information system
predictive approach – an SDLC approach that assumes the development project can be planned and organized in advance and that the new information system can be developed according to plan
adaptive approach – an SDLC approach that is more flexible, assuming that the project cannot be planned out completely in advance but must be modified as it progresses
phases – related system development activities which are grouped into categories of project planning, analysis, design, implementation, and support
waterfall model – a SDLC approach that assumes the various phases of a project can be completed sequentially – one phase leads into the next phase
spiral model – an adaptive SDLC approach that cycles over and over again through development activities until a project is complete
prototype – a preliminary working model showing some aspect of a larger system
iteration – system development process in which work activities – analysis, design, implementation – are done once, then again, and yet again on different system components they are repeated until the system is closer to what is ultimately needed.
incremental development – a development approach that completes parts of a system in several iterations and then puts them into operation for users
project planning – the initial activities of the SDLC, whose objective is to identify the scope of the new system and plan the project
analysis activities – the activities of the SDLC whose objective is to understand the user needs and develop requirements
problem domain – the area of the user’s business for which a system is being developed
design activities –the activities of the SDLC during which the system and programs are designed
application – the portion of the new information system that satisfies the user’s needs in the problem domain
implementation activities – the activities of the SDLC during which the new system is programmed and installed
support activities – the activities of the SDLC whose objective is to keep the system running productively after it is installed
help desk – the availability of support staff to assist users with any technical or processing problem associated with an information system
system development methodology – comprehensive guidelines to follow for completing every activity in the systems development life cycle, including specific models, tools, and techniques
 

model – a representation of an important aspect of the real world
tool – software support that helps create models or other components required in the project
technique – a collection of guidelines that help an analyst complete a system development activity or task
 

integrated development environment (IDE) – tools that help programmers with a variety of programming tasks
visual modelling tools – tools that help the analyst create and verify important system models, often generating program code
structured approach – system development using structured analysis, structured design, and structured programming techniques
structured program – a program or program module that has one beginning and one ending, and for which each step in the program execution consists of sequence, decision , or repetition constructs
top-down programming – dividing more complex programs into a hierarchy of program modules
structured design – a technique providing guidelines for deciding what the set of programs should be, what each program should accomplish, and how the programs should be organized into a hierarchy
structure chart – a graphical model showing the hierarchy of program modules produced by the structured design technique
structured analysis – a technique used to define what processing the system needs to do, what data it needs to store and use, and what inputs and outputs are needed
data flow diagram (DFD) – a structured analysis model showing the inputs, processes, storage, and outputs of a system
entity relationship diagram (ERD) – a structured analysis and information engineering model of the data needed by a system
information engineering – a traditional system development methodology thought to be more rigorous and complete than the structured approach, because of its focus on strategic planning, data modelling, and automated tools
 

object-oriented approach – an approach to system development that views an information system as a collection of interacting objects that work together to accomplish tasks
object – a thing in the computer system that can respond to messages
object-orientated analysis (OOA) – defining all of the types of objects that do the work in the system and showing what use cases are required to complete tasks
class diagram – a graphical model used the object orientated approach to show classes of objects in the system
Unified Process (UP) – an object oriented system development methodology offered by IBM’s Rational Software
repository – a database that stores information about the system in a visual modelling tool, including models, descriptions, and references that link the various models together. 
The System Development Life Cycle
(See wiki for a more detailed explanation)

The entire process of building, deploying, using, & updating an information system is called the systems development life cycle. A SDLC may vary in size and the time, and can be just a few days to several years depending on its scope.

In today’s diverse development environment there are many different approaches to developing systems, and each is based on a different SDLC’s.

Although it is difficult to find a single, comprehensive classification system that encompasses all of the approaches, one useful technique is to categorize SDLC approaches according to whether they are more predictive or adaptive.

A predictive approach is one which assumes that the new system can be developed according to plan. This approach is useful if the system is well understood and defined. When applying a predictive approach very few changes are done to the system once the final plan is approved.

A adaptive approach is one where the exact requirements of a system or the user’s needs are not well understood. In this situation, the project cannot be planned completely in advance, but the system can still be built and as the needs are better defined modifications to the system are done.

Predictive approaches are considered more traditional and were used extensively in the 80’s and 90’s. Many newer adaptive approaches have been adopted since the 90’s and are currently used.


It is important to recognize that any project will have a mix of both the predictive and adaptive elements.


The Traditional Predictive approaches to the SDLC
There are five main phases to the predictive approach:

Planning – Identify scope, ensure feasibility, develop schedule, resource plan & budget
Analysis – Understand & document in details business needs and processing requirements
Design – Design solution based on the requirements
Implementation – Build, Test & Install
Support – Keep system running
The most predictive approach is called the pure waterfall model as it assumes that the various phases of a project can be carried out and completed sequentially. Once a phase is completed, you cannot go back to it (like going over a waterfall). In practice the pure waterfall approach is not very effective as there are always areas that need further development.

There is a modified waterfall model that is more adaptive/predictive. Using this model basically you are saying that there are set phases, but that there may be overlap between them. A benefit of the modified model is efficiency as it allows team members to start phases or do pre-phases without having completed the previous phases. i.e. you may want to design a section of the system while planning because there is sufficient clarity initially.

The Newer Adaptive Approaches to the SDLC
The adaptive approach means a development approach in which project activities – including plans & models – are adjusted as the project progresses. One popular technique is called the spiral model.

The spiral model is considered the first adaptive approach to system development. For more info on it refer to the wiki entry here…

A key concept of the spiral model is the focus on risk, basically you identify the greatest risks first and address these in your first iteration. This may require producing a POC to prove the technology is viable etc.

Iteration means that work activities – analysis, design, implementation – are done once. A project may have many iterations depending on its complexity.

With most of the adaptive approaches the emphasis is on tackling the toughest problems first that have the highest risk ranking, then fine tuning the system to accommodate the entire problem scope.

Activities of Each SDLC Phase
There are several sections of the SDLC Phase, which include…

Project Planning – identify the scope of the system, ensure feasibility & develop a schedule & resource plan
Analysis Activities – understand & document the business needs & processing requirements of the system (discovery & understanding)
Design Activities – design solution based on requirements
Implementation Activities – result in final system being built.
Support Activities – keep the system running productively during the time following the initial installation.
Project Planning
Nothing to important here – read the summary above.

Analysis Activities
6 primary activities are considered as part of this phase…

Gather Information – learn about the problem domain
Define System Requirements
Build prototypes for discovery requirements
Prioritize requirements
Generate & evaluate alternatives
Review recommendations with management
Design Activities
7 major activities must be completed during this phase…

Design & integrate the network
Design the application architecture
Design the user interfaces
Design the system interfaces
Design and integrate the database
Prototype for design details
Design and integrate the system controls
Design activities are closely interrelated and generally are done with substantial overlap.

Implementation Activities
5 major activities must be completed during this phase…

Construct software components
Verify and test
Convert data
Train users and document the system
Install the system
Support Activities
3 major activities occur during this phase…

Maintain the system
Enhance the system
Support the users
Methodologies, Models, Tools & Techniques
Methodologies
A system development methodology provides guidelines to follow for completing every activity in the SDLC, including specific models, tools, and techniques.

Because methodology contains instructions about how to use models, tools, and techniques, one must understand what these are…

Models
A model is a representation of an important aspect of the real world. It is sometimes called an abstraction as it is used to separate out and aspect of particular importance.

There are many different models that are used in the SDLC, including planning models such as Gantt charts, or implementation models such UML diagrams.

Some models of system components include….

Flowchart
Data flow diagram
Entity relationship diagram
Structure chart
Use case diagram
Class diagram
Sequence diagram
Some models used to manage the development process include…

Gantt chart
Organizational Hierarchy chart
Financial Analysis Model
Tools
A tool in software development is  software support that helps create models or other components required in the project.

They can include really anything, but a few examples would be…

Drawing Programs for Diagrams
Database Applications to store information
IDE for programming
Microsoft project for planning
Techniques
A technique in system development is a collection of guidelines that help an analyst complete a system development activity or task.

Some examples include…

Data-modelling techniques
Software-testing techniques
User-interviewing techniques
Relational-database design techniques
A methodology includes a collection of techniques that are used to complete activities within each phase of system development.

Two Approaches to System Development
There are several approaches to system development and in the real world actual implementations of approaches vary from company to company however in this book they have divided it into two groups, the traditional approach and the object orientated approach…

The Traditional Approach
The traditional includes many variations based on techniques used to develop information systems with structured and modular programming. The approach is often referred to as the structured system development approach, but has also been refined (which is called the information engineering approach).

There are three techniques that make up the Structured System Development approach. They are…

Structured Analysis
Structured Design
Structured Programming
These three techniques are often referred to collectively as the Structured Analysis & Design Technique (SADT).

Structured Analysis (Modern) is the technique of defining system requirements. This approach requires one to define…

What the system needs to do
What data the system needs to store & use
what input & outputs are needed
How the functions work together as a whole
Initially this was done using DFD (Data Flow Diagrams), which shows the inputs, storage, outputs & processing.

Another diagram called the ERD (Entity Relationship Diagram) which is a database modelling method used to produce a type of conceptual scheme of a system.

Structured Design is the technique developed for providing some guidelines for deciding what the set of programs should be in a system, what each program should accomplish, and how the programs should be organized.

The modules and arrangement of the modules can be shown graphically using a structure chart.

There are two main principles of structured design which are…

Loosely coupled
Highly cohesive
Structured Programming is the technique of creating high quality programs that generate the correct outputs and are easy for other programmers to read. A structured program is one that has one beginning and one ending and each step in the program execution consists of one of three programming constructs

A sequence of program statements
A decision where one set of statements or another set of statements executes
A repetition of a set of statements
Another concept related to structured programming is Top-down programming where one module controls sub modules, and those sub modules each have sub-sub modules etc.

Some Weaknesses of the Structured Approach

Address some but not all of the activities of analysis & design
Makes processes rather than data the central focus
Information Engineering

Information engineering is a refinement to structured development that begins with overall strategic planning to define all of the information systems that an organization needs to conduct its business.

The information engineering approach refines many of the concepts of structured approach into rigorous and comprehensive methodology, thus the book will refer to both these approaches as the traditional approach.

The Object Oriented Approach
The object oriented approach views systems as a collection of interacting objects that work together to accomplish tasks.

An object is a thing in the computer system that is capable of responding to messages.

The object oriented approach covers three main areas…

Object oriented analysis – defines all of the types of objects that do the work in a system
Object oriented design – defines all of the additional types of objects necessary to communicate with various things, refines definitions of each objects so that it can be implemented in a programming language.
Object oriented programming – consists of writing statements in a programming language to define what each type of object will do.
A classification or “class” represents a collection of similar objects in a system.

Classes can be represented using class diagrams.

The object orientated approach has several benefits including…

It seems natural in many scenarios to specify things as objects
It allows for reuse of objects in other systems
Current Trends in Development
There are always new approaches coming out on the market. Some examples of these include…

The Unified Process
Extreme Programming
Scrum
I will not cover these topics from the book, but it may be worth checking out their definitions in wiki.

Tools to Support System Development
There are many tools that support system development that help automate the process.

Examples of these tools include…

Microsoft Visio (for diagram modelling)
IBM’s rational software
Use automated tools whenever possible, but remember that sketches on napkins or envelopes are often enough for a small team on a small project. Don’t let the tool create more problems than it solves.