---
layout: post
title: Object Oriented Analysis UNISA Studies - Chap 12
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA ICT 2622 tag should be considered study notes for my lectures...

Objectives of Chapter 12

Explain the different types of objects and layers in a design
Develop a sequence diagram for use case realization
Develop communication diagrams for detailed design
Develop updated design class diagrams
Develop multilayer subsystem packages
Explain design patterns and recognize various specific patterns
Key Words & Definitions
use case realization – the process of elaborating the detailed design with interaction diagrams of a particular use case
design patterns – standard design techniques and templates that are widely available and recognized as good practice
activation lifeline – a representation of the period in which a method of an object is alive and executing
separation of responsibilities – a design principle to segregate classes into separate components based on the primary focus of the classes
link – in a communication diagram, the connection between classes that indicates messages can be passed
dependency relationship – a relationship between packages, classes, or use cases that indicates a change in the independent item willrequire a corresponding change in the dependent item
Example Questions for the Chapter
List the major implementation responsibilities of each layer of a three-layer design
Develop a first-cut sequence diagram, which only includes the actor and problem domain classes
Detailed Design of Multilayer Systems
Several questions should come to mind as you review detailed system design…

How do all these objects get created in memory?
Will other objects be necessary?
What object does authentication?
What is the lifespan of each object?
Design Patterns & the Use Case Controller

Patterns also called templates are used repeatedly in everyday life. Patterns are used to solve problems.

A design patterns are standard design techniques and templates that are widely available and recognized as good practice.

Controllers are typically intermediary class that acts as a buffer between the user interface and the domain classes.

A Use Case controller has 5 main elements…

The pattern name
The problem that requires a solution
The solution, or explanation, of the pattern
Example of the pattern
The benefits and consequences of the pattern
Controller Pattern

See diagram below for the controller pattern..

004

A use case controller is a completely artificial class created by the person designing the system. Sometimes such classes are called artifacts or artifact objects.

Use Case Realization with Sequence Diagrams
Developing interaction diagrams is at the heart of object-oriented detailed design.

Two types of interaction diagrams can be used at design time…

Sequence diagrams
Communication Diagrams
Please note that this section goes into detail about creating sequence diagrams – for a better understanding of how to create these diagrams please refer to the chapter summary from page 433 – 440.

Guidelines & Assumptions for Preliminary Sequence Diagram Development

The following tasks are not done sequentially, but only when necessary to build the sequence diagram.

Take each input message and determine all of the internal messages that result from that input. For each message determine its objective. Determine what information is needed, what class needs it and what class provides it. Determine whether any objects are created as a result of the input. This will help you to define internal messages, their origin objects, and their destination objects,
As you work with each input message, be sure to identify the complete set of classes that will be affected by the message. In other words, select all the objects from the domain class diagram that need to be involved. Other classes to include are those that are created, classes that are the creators of objects for the use case, classes updated during the use case, and those that provide information used in the use case.
Additionally, flesh out the components for each message. Add iteration, true/false conditions, return values, and passed parameters. The passed parameters should be based on the attributes found in the domain class diagram.
The development of first-cut sequence diagrams is based on several simplifying assumptions, including the following three…

Perfect Technology Assumption
Perfect memory Assumption
Perfect Solution Assumption
Designing with Communication Diagrams
Communication diagrams are useful for showing a different view of the use case – one that emphasizes coupling.

Communication diagrams are also easier to use to sketch design ideas in meetings, as they are easier to change and rearrange on the fly.

Updating and Packaging the Design Classes
Refer to book for more info

Design Patterns
 

There are many design patterns – in this section we will refer just to a few GoF patterns….

Adapter Pattern

The adapter pattern works just like a wall plug adapter. It plugs an external class so that it can be inserted into a system.

The pattern is a standard solution for protection from variations. On one side of an adapter class is the outputs & inputs expected by the system, on the other side is the inputs & outputs expected by the class that is being plugged in.

Factory Pattern

A factory class is one that handles the creation of objects between the business layer and the data access layer. The business layer will always refer to the factory class about getting data – the factory class would then decide whether to retrieve the data from memory or from disk.

Singleton Pattern

The singleton pattern is one that caters for situations where only one instance of a class is needed for the system. Once the class has been created, any calls to the object get redirected to that instance.

Observer Pattern

Refer to book