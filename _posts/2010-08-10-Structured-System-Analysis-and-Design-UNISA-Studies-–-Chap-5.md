---
layout: post
title: Structured System Analysis and Design UNISA Studies – Chap 5
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA ICT 2621 tag should be considered study notes for my lectures...

Please note this chapter is also covered in ICT2622 – Object Orientated Analysis

Objectives of Chapter 5

Understand why identifying use cases is the key to defining functional requirements
Use three techniques for identifying use cases
Write brief, intermediate, and fully developed use case descriptions
Explain how the concept of things in the problem domain also define requirements
Identify and analyze data entities and domain cases needed in the system
Read, interpret, and create an entity-relationship diagram
Read, interpret, and create a domain model class diagram
Key Word & Definitions
use case – an activity the system performs
user goal technique – an approach for identifying use cases in which an analyst talks to all users to get them to describe their goals in using the system
CRUD techniques – an approach in which an analyst looks at each type of data and includes use cases that create the data, read or report on the data, update the data, and delete the data.
elementary business process (EBP) – a task that is performed by one person, in one place, in response to a business event; it adds measurable business value and leaves the system and its data in a consistent state.
event – an occurrence at a specific time and place that can be described and is worth remembering
event decomposition – an analysis technique that focuses on identifying the events to which a system must respond and then determining how the system must respond.
external event – an event that occurs outside the system, usually by an external agent or actor.
temporal event – an event that occurs as a result of reaching a point in time.
state event – an event that occurs when something happens inside the system that triggers the need for processing
system controls – check or safety procedures put in place to protect the integrity of the system
perfect technology assumption – the assumption that events should be included during analysis only if the system would be required to respond under perfect conditions.
event table – a catalogue of use cases that lists events in rows and key pieces of information about each event in columns.
trigger – a signal that tells the system that an event has occurred, either the arrival of data needing processing or a point in time.
source – an external agent or actor that supplies data to the system
response – an output, produced by the system, that goes to a destination
destination – an external agent or actor that receives data from the system
use case description – a description that lists the processing details for a use case
actor – in UML diagrams, a person who uses the system
scenario or use case instance – a unique set of internal activities within use case that represents a unique path through the use case
preconditions – conditions that must be true before a use case begins
post conditions – conditions that must be true upon completion of the use case
relationship – a naturally occurring association among specific things, such as “an order is placed by a customer and an employee works in a department”
cardinality – the number of associations that occur among specific things, such as a customer places many orders and an employee works in one department.
multiplicity – a synonym for cardinality
binary relationships – relationships between two different types of things such as a customer and an order
unary relationships - a relationship among two things of the same type, such as one person being married to another person
ternary relationship – a relationship among three different types of things
n-ary relationship – a relationship among n different types of things
attribute – one piece of specific information about a thing
identifier (key) – an attribute that uniquely identifies a thing
compound attribute – an attribute that contains a collection of related attributes
data entities – the things about which the system needs to store information in the traditional approach to information systems
associative entity – a data entity that represents a many-to-many relationship between two other data entities
generalization / specialization hierarchies – hierarchies that structure or rank classes from the more general super class to the more specialized subclasses; sometimes called inheritance hierarchies.
inheritance – a concept that allows subclasses to share characteristics of their super classes
whole-part hierarchies – hierarchies that structure classes according to their associated components
aggregation – whole-part relationship between an object and its parts
composition – whole-part relationship in which the parts cannot be dissociated from the object
User Goals, Events, & Use Cases
(See Wiki on Use Cases for more info)

Use cases are used in almost all modern system analysis approaches. A use case is an activity the system performs, usually in response to a request by a user.

Several techniques are recommended for identifying use cases including…

User Goal Technique - This is an approach for identifying use cases in which an analyst talks to all users to get them to describe their goals in using the system.
CRUD Technique – This an approach in which an analyst looks at each type of data and includes use cases that create the data, read or report on the data, update the data, and delete the data
Event Decomposition Technique – This is the most comprehensive technique for identifying use cases and focuses on identifying the events to which a system must respond and then determining how the system must respond.
It is important with use cases to identify the appropriate level of detail, you do not want to be to broad, or to narrow. One way to do this is to define the EBP (Elementary Business Process). Basically, an EBP is a process where no major time gap occurs during the process – i.e. it may seem seamless.

Event Decomposition Technique

identify the events to which a system must respond
determine how the system must respond
focus on events
Types of Events

There are three main types of events in a system…

External Event – an event that occurs outside the system, usually by an external agent or actor.
Temporal Event – an event that occurs as a result of reaching a point in time (time based event)
State Event – an event that occurs when something happens inside the system that triggers the need for processing
Identifying Events

It is not always easy to define the events that affect a system. The following need to be taken into consideration.

Events vs. Prior Conditions & Response – is this actually an event or part of a prior condition? Try and use the EBP principle.
The Sequence of Events : Tracing a Transactions Life Cycle – sometimes useful to trace all events that will occur with an actor.
Technology Dependent Events & System Controls – assume the “perfect technology assumption”. These events should not form part of the initial use cases as they are technology dependant – i.e. logging in to a system, etc.
Event Table

An event table is a catalogue of use cases that lists events in rows and key pieces of information about each event in columns.

An event table includes row and columns representing events and their details, respectively. An example of an event table is shown below…

Event	Trigger	Source	Use Case	Response	Destination
Customer wants to check item availability	Item Inquiry	Customer	Look up item availability	Item Availability Details	Customer
 

Use an event table as a catalogue of information about the use cases that make up the functional requirements of the system

Each column in the event table represent a section…

trigger – a signal that tells the system that an event has occurred, either the arrival of data needing processing or a point in time.
source – an external agent or actor that supplies data to the system
response – an output, produced by the system, that goes to a destination
destination – an external agent or actor that receives data from the system
Use Case Descriptions
A list of use cases and an event table provide an overview of all the use cases for a system. Detailed information about each use case is described with a use case description.

In UML, an actor is a person. An actor is always outside the automation boundary of the system but may be part of the manual portion of the system.

There are three levels of use case descriptions…

Brief Description
Intermediate Description
Fully Developed Description
Brief Description

Used for very simple use cases
Usually it is changed to a intermediate description or a fully developed description
Intermediate Description

Below is an example of a template layout for a intermediate description…

Title of the Use Case
Main Flow

Step by Step descriptions of the flow
Exception Conditions 
Fully Developed Description

The most formal description

Example of description listed below…

Use Case Name	 
Scenario	
Triggering Event	
Brief Description	
Actors	
Related Use Cases	
Preconditions	
Post conditions	
Flow of Activities	
Actor

System

Exception Conditions	
 	 
 

Preconditions and post conditions are critical to understanding the processing done for a use case.

“Things” in the Problem Domain
In the traditional approach, the “things” make up the data that is stored. The type of data that is stored is key to the system requirements.

In the object orientated approach, the “things” make up the objects that are mapped.

Whether you use the traditional or object oriented approach, identifying the “things” is a key initial step.

Types of Things

An analyst can identify the types of things by  thinking about each event in the event table and asking questions.

There are several procedures that can assist an analyst in this process. Outlined below is one such procedure…

Use the event table and information about each event and identify all of the nouns.
Using other information from existing systems, current procedures, and current reports or forms, add items or categories of information needed
Refine the list and record assumptions or issues to explore.
Relationships Among Things

Once you have identified the “things”, you should identify the relationship between them.

A relationship is a naturally occurring association among specific things, such as “an order is placed by a customer and an employee works in a department”.

It is important to note that relationships between things apply in two directions – i.e. a customer orders a products, products have been ordered by a specific customer.

It is important to also understand the cardinality that exists between objects. Cardinality is the number of associations that occur among specific things, such as a customer places many orders and an employee works in one department. Sometimes this can be called multiplicity. (see wiki for more on cardinality)

It is important not just to understand the cardinality, but also the range of possible values. i.e. A particular customer might not ever place an order, but if he wanted to he could place many orders. (range is the minimum and maximum cardinality).

There are several different types of relationships… outlined below are some of the major ones…

binary relationships – relationships between two different types of things such as a customer and an order
unary relationships - a relationship among two things of the same type, such as one person being married to another person
ternary relationship – a relationship among three different types of things
n-ary relationship – a relationship among n different types of things
 

Initially focus on identifying each “thing” in the problem domain, but also be sure to focus on associations/relationships among them, which are often just as important to the system users.

Attributes of Things

An attribute is one piece of specific information about a thing. In .Net we usually call these properties of objects. i.e. the Name of a Person would be an attribute.

Some attributes are key identifiers which means that the attribute uniquely identifies the “thing”.

You can also get compound attributes – which is an attribute that contains a collection of related attributes – i.e. Full Name is a compound attribute of First Name & Last Name.

The Entity-Relationship Diagram
Data entities are the things about which the system needs to store information in the traditional approach to information systems. The model used to define the data storage requirements with the traditional approach is called the entity-relationship diagram (ERD).

(For more information on ERD diagrams see the wiki)

An important aspect of an entity diagram is an associative entity which is a data entity that represents a many-to-many relationship between two other data entities.

Several refinements are done to ERD during the design process. One such refinement is called normalization (see wiki for more info).

The Domain Model Class Diagram
The domain model class diagram (See wiki for more info) is a type of UML class diagram shows the things in the users work domain.

The book covers the notation for this type of UML diagram however the summary will not go into any depth on this.

The section also covers generalization/specialization of classes.

A generalization / specialization hierarchy is one in which one can structure or rank classes from the more general super class to the more specialized subclasses; sometimes called inheritance hierarchies. i.e. A Vehicle Class can have specialization sub classes of Cars or Trucks.

Another way that people structure information about things is by defining them in terms of their parts. This is called whole-part hierarchies.

Whole-part hierarchies are hierarchies that structure classes according to their associated components.

There are two types of whole part hierarchies…

Aggregation
Composition
Aggregation is used to describe a form of association that specifies a whole-part relationship between the aggregate (whole) and its components (parts) where the parts can exist separately.

Composition is used to describe a form of association that is even stronger than aggregation, where the parts once associated, can no longer exist separately.

(See Page 191 of the book for graphical examples).

Whole-part hierarchies serve mainly to allow the analyst to express subtle distinctions about associations among classes. As with any association relationship, multiplicity can apply such as when a computer has one or more disk storage devices.

Composition – whole-part relationship in which the parts cannot be dissociated from the object