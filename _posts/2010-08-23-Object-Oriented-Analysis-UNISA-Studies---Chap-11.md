---
layout: post
title: Object Oriented Analysis UNISA Studies - Chap 11
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA ICT 2622 tag should be considered study notes for my lectures...

Objectives of Chapter 11

Explain the purpose and objectives of object-oriented design

Develop package diagrams and component diagrams

Develop design class diagrams

Use CRC cards to define class responsibilities and collaborations

Explain the fundamental principles of object-oriented design

Key Words & Definitions
instantiation – creation of an object based on the template provided by the class definition
enterprise-level system – a system that has shared resources among multiple people or groups in an organization
component diagram – a type of implementation diagram that shows the overall system architecture and the logical components within it
application program interface (API) – the set of public methods that is available to the outside world
deployment diagram – a type of implementation diagram that shows the physical components across different locations
artifact – a class invented by a system designer to handle a needed system function
realization of use cases – specification of all detailed system processing for each use case
stereotype – a way of categorizing a model element by its characteristics, indicated by guillements [<< >>]
entity class – a design identifier for a problem domain class
persistent class – an entity class that exist after a system is shut down
boundary class or view class – a class that exists on a system’s automation boundary, such as an input window
control class – a class that mediates between boundary classes and entity classes, acting as a switchboard between the view layer and domain layer
data access class – a class that is used to retrieve data from a database
visibility – a notation of whether an attribute can be directly accessed by another object; indicated by plus or minus signs
method signature – a notation that shows all of the information needed to invoke, or call, the method
overloaded method – a method with one name but two or more parameter lists
class-level method – a method that is associated with a class instead of with objects of the class
class-level attribute – an attribute that contains the same value for all objects in the system
overridden method – a method in a subclass that overrides the method in the parent class
abstract class – a class that can never be instantiated
concrete class – a normal class that can be instantiated
navigation visibility – a design principle in which one object has a reference to another object and thus can interact with it
encapsulation – a design principle of objects in which both data and program logic are included within a single, self contained unit
object reuse – a design principle in which a set of standard objects can be used repeatedly within a system
information hiding – a design principle in which data associated with an object is not visible to the outside world, but method are provided to access of change the data
coupling – a qualitative measure of how closely the classes in a design class diagram are linked
cohesion – a qualitative measure of the consistency of functions within a single class
protection from variations – a design principle in which parts of a system that are unlikely to change are segregated from those that will
indirection – a design principle in which an intermediate class is placed between two classes to decouple them but still link them
object responsibility – a design principle in which objects are responsible for carrying out system processing
Example Questions for the Chapter
What is an API? Why is it important?
What is meant by three-layer design, and normally what are the three layers?
In your own words, list the steps for doing detailed design.
Object-Oriented Design – Bridging from Analysis to Implementation
Object Oriented design is the process by which a set of detailed object-oriented design models are built and then used by the programmers to write and test a new system.
System design the the bridge between user requirements and programming the new system.
An object oriented system consists of sets of computing objects. Each object has data and program logic encapsulated within itself. An object does not come into existence until it is instantiated. Objects interact with each other via messaging.

The objective of object oriented design is to identify and specify all of the objects that must work together to carry out each use case and where they reside in different computing nodes.

Another design objective is to specify the detail methods and attributes within the classes so that a programmer can understand how a set of objects collaborate to execute a use case.

If you examine the diagram below you will see two columns (requirements models & design models) – the requirements models are those generated during analysis, the design models are those needed to be generated during design time.

While identifying the requirements of a system is critical, it is just as critical that once the requirements are identified a design is made that will fulfil the requirements. This is done using the design models.

001

Object-Oriented Architectural Design
There are three fundamental differences that effect the architectural design of the system…

State
Client Configuration
Server Configuration
Design Issue	Client/Server Network System	Internet System
State	Stateful or state based system	Stateless system
Client Configuration	Screens and forms that are programmed are displayed directly	Screens & forms are displayed through a browser
Server Configuration

Application or data server connects directly to client tier

Client tier connects indirectly to the application server through a web server

Component Diagrams & Architectural Design

A component diagram is a type of implementation diagram that shows the overall system architecture and the logical components within it

A component is an executable module or program, and it consists of all the classes that are compiled into a single entity. It has public interfaces that can be accessed by other programs or external devices. The set of these interfaces is called the application program interface (API).

The diagram below is an example of object-oriented component notation.

001

There are several different approaches to architectural design of internet systems.

Two-Layer Architectural Design of Internet Systems – very little domain/business logic is within the system, typically if any it is mixed with the UI layer
Three-Layer Architectural Design of internet Systems – separated with a UI layer, Business Layer & Data Access Layer
Web Services – design where services are exposed to the outside world, anyone can access the service provided they have the correct interface
Deployment Diagrams

A deployment diagram is a type of implementation diagram that shows the physical nodes/components across different locations.

A node can be thought of as a computer, or a bank of computers, representing a single computing resource. A node is a physical entity at a specific location.

One other symbol is a artifact which is a class invented by a system designer to handle a needed system function.

The diagram below is an example of a deployment diagram for an Internet based system.

002

 

Fundamental Principles of Object-Oriented Detailed Design
The two most important diagrams for detailed design are the…

Sequence Diagram
Communication Diagram
Object-oriented design is model driven & use case driven. The design process takes the requirements models as input and produces the design models as output. We need a method for organizing this activity, this is outlined below in a 5 step process called the Object Oriented Detailed Design Steps…

Develop the first-cut design class diagram showing navigation visibility
Determine class responsibilities and class collaborations for each use case using Class-Responsibility-Collaboration (CRC) cards
Develop detailed sequence diagrams for each use case – first-cut & multilayer sequence diagrams
Update the design class diagram by adding method signatures and navigation information using CRC cards and/or sequence diagrams
Partition the solution into packages as appropriate
Design Classes and the Design Class Diagram
Design class diagrams & detailed interaction diagrams work together.

A first iteration of the design class diagram is based on on the domain model & on engineering design principles. The preliminary design class diagram is then used to help develop interaction diagrams. As design decisions are made during development of interaction diagrams, the results are used to refine the design class diagram. As class diagrams are built, many more classes than were originally defined in the domain model are added to the system.

Design Class Symbols

UML does not specifically distinguish between design class notation and domain model notation however practical differences do occur between the two.

Design class diagrams are specifically defining software classes. Because many different types of design classes are identified during the design process, UML has a special notation called a stereotype which allows designers to designate a special type of class.

A stereotype is a way of categorizing a model element by its characteristics, indicated by guillements [<< >>]. It extends the basic definition of a model element by indicating that it has some special characteristics we want to highlight.

Four types of design classes are considered standard…

Entity Class – a design identifier for a problem domain class
Control Class - a class that mediates between boundary classes and entity classes, acting as a switchboard between the view layer and domain layer 
Boundary Class or View Class – a class that exists on a system’s automation boundary, such as an input window
Data Access Class – a class that is used to retrieve data from a database
The diagram below illustrates the standard stereotypes found in design models….

003

Design Class Notation

The table below illustrates the notation used to define a design class…

<<Stereotype Name>> 
Class Name::Parent Class

Attribute List 
visibility name:type-expression = initial-value {property}

Method List 
visibility name (parameter list): type-expression

 

Detailed Design with CRC Cards
CRC stands for Class-Responsibility-Collaboration. It defines a brainstorming technique that is quite popular among object-oriented developers.

A CRC card is simply a small card with lines that partition it into three areas -

Class Name
Responsibility
Collaboration Classes
The process of developing a CRC model is usually done in a brainstorming sessions. One of the main benefits of CRC is that it requires a group effort. For each use case you need to design, the following process is done iteratively…

Select a use case
Identify the problem domain class that has responsibility for this use case
Identify other classes that must collaborate with the primary object class to complete the use case
At the end of the process, one will have a small set of CRC cards that collaborate to spport the use case.

Fundamental Detailed Design Principles
Encapsulation and Information Hiding

Encapsulation is a design principle of objects in which both data and program logic are included within a single, self contained unit

Programmers rely heavily on the benefits of encapsulation to support the idea of object reuse. Related to encapsulation is the concept of information hiding, which dictates that the data associated with an object is not visible to the outside world.

Coupling

Coupling is a qualitative measure of how closely the classes in a design class diagram are linked. The objective is to have objects loosely coupled so that they can be tested individually. The higher the coupling, the hard it is to make changes to the system at a later stage.

Cohesion

Cohesion is a qualitative measure of the consistency of functions within a single class. The objective is to have high cohesion amongst methods of an object. If an object has low cohesion it has several different responsibilities in different areas of the system.

Protection from Variations

Protection from variations is a design principle in which parts of a system that are unlikely to change are segregated from those that will.

Indirection

Indirection is a design principle in which an intermediate class is placed between two classes to decouple them but still link them.

Object Responsibility

Object responsibility is a design principle in which objects are responsible for carrying out system processing .