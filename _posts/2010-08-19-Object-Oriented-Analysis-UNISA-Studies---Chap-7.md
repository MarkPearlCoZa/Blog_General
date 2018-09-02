---
layout: post
title: Object Oriented Analysis UNISA Studies - Chap 7
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA ICT 2622 tag should be considered study notes for my lectures...

Objectives of Chapter 7

Understand the models and processes of defining object-oriented requirements
Develop use case diagrams and activity diagrams
Develop system sequence diagrams
Develop state machine diagrams to model object behaviour
Explain how use case descriptions and UML diagrams work together to define functional requirements for the object oriented approach
Key Words & Definitions
use case model – a collection of models that can be used to capture system requirements based on use cases with the object-oriented approach
use case diagram – a diagram to show the various user roles and how those roles use the system
system sequence diagram – a diagram showing the sequence of messages between an external actor and the system during a use case or scenario
message – the communication between objects within a use case
domain model – a model that describes classes of objects and their states
state machine diagram – a diagram showing the life of an object in states and transitions
package – a symbol used to denote a group of similar elements
interaction diagram – either a communication diagram or a sequence diagram that shows the interactions between objects
lifeline, or object lifeline – the vertical line under an object on a sequence diagram to show the passage of time for the object
true/false condition – part of a message between objects that is evaluated prior to transmission to determine whether the message can be sent
state – a condition during an object’s life when it satisfies some criterion, performs some actions, or waits for an event
transition – the movement of an object from one state to another state
pseudo state – the starting point of a state machine diagram, indicated by a black dot
destination state – for a particular transition, the state to which an object moves after the completion of a transition
origin state for a particular transition - the original state of an object from which the transition occurs
message event – the trigger for a transition, which causes the object to leave the origin state
guard condition – a true/false test to see whether a transition can fire
action expression – a description of the activities performed as part of a transition
concurrency, or concurrent state – the condition of being in more than one state at a time
path – a sequential set of connected states and transitions
composite state – a state containing other states and transitions
Example Questions for the Chapter
What is UML? What type of modelling is it used for?
What is the difference between a use case description and an activity diagram?
What are the steps required to develop a system sequence diagram?
Object Oriented Requirements
System development starts with the identification of events that trigger elementary business processes called use cases.

The object oriented approach is a “divide and conquer” approach.

The use case model is a collection of models that can be used to capture system requirements based on use cases with the object-oriented approach. It includes…

use case diagrams
use case descriptions
activity diagrams
system sequence diagrams
The use case model is a collection of models that can be used to capture system requirements based on use cases with the object-oriented approach

The use case diagram is a diagram to show the various user roles and how those roles use the system

The system sequence diagram is a diagram showing the sequence of messages between an external actor and the system during a use case or scenario

The System Activities – A Use/Case Scenario View
The objective of the use case model is to identify and define all of the elementary business processes that the system must support.

There are two levels that use cases are defined…

Overview Level – event table & use case diagrams
Detailed Level – use case descriptions, activity diagrams, system sequence diagarm
Use Cases & Actors

A use case is an activity the system carries out usually in response to a request by a user of the system.

Implied in all use cases is a person (actor) who uses the system.

An actor is always outside the automation boundary of the system, but may be part of the manual portion of the system thus an actor is not always the same as the source of the event in the event table.

A source of an event is the initiating person who supplied the data and is usually external to the system (including the manual system).

Be sure that actors have direct contact with the automated system.

The Use Case Diagram

The diagram below shows how a use case is documented.

The use case itself is symbolized by an oval with the name of the use case inside.

A use case diagram is a graphical model that summarizes the information about the actors and use cases.

001

 

Automation Boundary

A rectangle is used to indicate an actor that is not a person. In the diagram below the Inventor System is indicated as an actor.

002 0

Use Case Diagram compared with the Event Table

The event table & use case diagram contain much of the same information.

The event table is really a catalogue of information about all the use cases.

Some differences do exist between the use case diagram and the event table…

Event table focuses on the business process while an use case diagram emphasis the automated system.
Use cases often overlook temporal & state events
Developing a Use Case Diagram

If there is an event table, then the analyst will use the event table to generate use case diagrams.

If there is no event table, the other starting point is to identify the actors & the elementary business processes with the user goal technique. For this to be feasible you need to make the system boundary an automated system so that the actors identified actually contact the system and you must assume perfect technology. Once this is done you can generate the use case diagrams using the following two step process…

Identify actors of the system – identify the specific roles each person plays
Develop the list of goals those roles have in the use of the automated system – a goal is a task performed by an actor to accomplish a business function that adds value to the business.
Activity Diagrams for Describing Use Cases

Activity diagrams  are an effective technique to document the flow of activities for each use case scenario.

An activity diagram can be used to support any level of use case descriptions.

Early termination of the workflow can be indicated.

Activity diagrams are also helpful in developing system sequence diagrams.

003

Identifying Inputs & Outputs – The System Sequence Diagram
An SSD Diagram is used to describe the flow of information into and out of the automated system.

A System Sequence Diagram is a diagram showing the sequence of messages between an external actor and the system during a use case or scenario

An SSD is a type of interaction diagram. Often the word interaction & message are used interchangeably.

SSD Notation

The emphasis in an SSD is on how the actor interacts with the system by entering data and receiving output data.

In an SSD the only object included is one representing the entire system.

A lifeline, or object lifeline is the vertical line under an object on a sequence diagram to show the passage of time for the object

004

Develop SSD’s carefully and correctly. They become critical components for detailed design and user interface design.

Developing a System Sequence Diagram

A SSD is normally used in conjunction with the use case descriptions to help document the details of a single use case scenario within a use case. To develop a SSD you will either need a fully developed description of a use case or activity diagrams.

An SSD will provide the explicit identification of inputs and outputs.

The development of an SSD based on an activity diagram can be divided into four steps…

Identify the input messages
Describe the message from the external actor to the system using the message notation described earlier
Identify and add any special conditions on the input messages, including iteration and true/false conditions
Identify and add the output return messages.
For a detailed explanation of this process see pages  256 – 260 of the textbook.

Identifying Object Behaviour – The State Machine Diagram
A state is a condition during an object’s life when it satisfies some criterion, performs some actions, or waits for an event.

States are described as semi permanent conditions because external events can interrupt a state and cause the object to go to a new state. An object remains in a state until some event causes it to move to another state (this is called transition).

Transition is the movement of an object from one state to another state.

Pseudo state is the starting point of a state machine diagram, indicated by a black dot (see diagram below).

Destination state for a particular transition is the state to which an object moves after the completion of a transition.

The origin state for a particular transition is the original state of an object from which the transition occurs.

005

The transition name is the name of a message event that triggers the transition and causes the object to leave the origin state.

A message event is the trigger for a transition, which causes the object to leave the origin state.

The guard condition is a qualifier or test on the transition and is simply a true/false test to see whether a transition can fire

The action expression is a procedural expression that executes when the transition fires. In other words it is a description of the activities performed as part of a transition.

Composite States & Concurrency

A composite state is a state containing other states and transitions. It means an object is in more than one state at the same time.

A composite state represents a higher level of abstraction and can contain nested states and transition paths.

Rules for Developing State Machine Diagrams

State machine diagram development follows a set of rules. Below is a list of steps that will help one develop state machine diagrams…

Review the class diagram and select the classes that will require state machine diagrams
For each selected class in the group, make a list of all the status conditions one can identify
Begin building state machine diagram fragments by identifying the transitions that cause an object to leave the identified state
Sequence these state transition combinations in the correct order
Review the paths and look for independent, concurrent paths
Expand each transition with the appropriate message event, guard condition, and action expression
Review and test each state machine diagram
