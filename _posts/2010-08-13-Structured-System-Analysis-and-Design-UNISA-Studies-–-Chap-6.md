---
layout: post
title: Structured System Analysis and Design UNISA Studies – Chap 6
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA ICT 2621 tag should be considered study notes for my lectures...

Objectives of Chapter 6

Explain how the traditional approach and the object oriented approach differ when modelling the details of a use case.
List the components of a traditional system and the symbols representing them on a data flow diagram.
Describe how data flow diagrams can show the system at various levels of abstraction
Develop data flow diagrams, data element definitions, data store definitions, and process descriptions
Develop tables to show the distribution of processing and data access across system locations
Key Word & Definitions
data flow diagram (DFD) – a diagram that represents system requirements as processes, external agents, data flows, and data stores
external agent – a person or organization outside the system boundary, that supplies data inputs or accepts data outputs
process – a symbol on a DFD that represents an algorithm or procedure by which data inputs are transformed into data outputs
data flow – an arrow on a DFD that represents data movement among processes, data stores, and external agents
data store – a place where data is held pending future access by one or more processes
level of abstraction – any modelling technique that break the system into a hierarchical set of increasingly more detailed models
context diagram – a DFD that summarizes all processing activity within the system in a single process symbol
DFD fragment – a DFD that represents the system response to one event within a single process symbol
event-partitioned system model, or diagram 0 – a DFD that models system requirements using a single process for each event in a system or subsystem
information overload – difficulty in understanding what occurs when a reader receives too much information at one time
rule of 7+-2 – the rule of model design that limits the number of model components or connections among components to no more than nine
minimization of interfaces – a principle of model design that seeks simplicity by limiting the number of connections among model components
balancing – equivalence of data content between data flows entering and leaving a process and data flows entering and leaving a process decomposition DFD
black hole – a process of data store with a data input that is never used to produce a data output
miracle – a process or data store with a data element that is created out of nothing
Structured English – a method of writing process specifications that combines structured programming techniques with narrative English
decision table – a tabular representation of processing logic containing decision variables, decision variable values, and actions or formulas
decision tree – a graphical description of process logic that uses lines organized like branches of a tree
data flow definition – a textual description of a data flow’s content and internal structure
data dictionary – a repository for definitions of data flows, data elements, and data stores
location diagram – a diagram or map that identifies all of the processing locations of a system
activity location matrix – a table that describes the relationship between processes and the locations in which they are performed
Traditional & Object-Oriented Views of Activities/Use Cases
Traditional approach

views system as a collection of processes
contains instructions that are typically sequential
involves processes, stored data, inputs & outputs, processing models
OO Approach

views system as a collection  of interacting objects
objects are based on things in the problem domain
objects are capable of behaviours (methods) that allow them to interact with each other
no conventional computer processes or data files per se
includes models that show objects, their behaviour, and their interactions with other objects
Data Flow Diagrams
(See wiki for more info)

Data flow diagram is the most commonly used process model.
It is a graphical system model that shows all of the main requirements for an information system in one diagram.
It is easy to read.
There are only five symbols to learn in a DFD

external agent (square)
process (rectangle with rounded corners)
data flows (lines with arrows)
real-time link – communication back and forth between external agents.
data store (flat open ended rectangle)
TMPDFD

An example of a basic DFD using these elements is shown below…

TMPDFDEG

When employing the traditional approach, identify use cases and then model the details of each use case with a data flow diagram fragment

DFD’s & Entity Diagrams

The DFD integrates processing triggered by events with the data entities modelled using the ERD. The picture below summarizes the correspondence among components of the DFD, events described in the event table and the entities defined in the ERD.

 

001


Data Flow Diagrams & Levels of Abstraction

DFD’s can show either higher level or lower level vies of a system.
A context diagram is a DFD that describes the most abstract view of a system – it summarizes all processing activity within the system in a single process symbol.
The topmost DFD is the context diagram.
A context diagram…

clearly shows the system boundary
does not usually show data stores because all of the system’s data stores are considered within the system scope.
usually created in parallel with the event table
External agents that supply or receive data from the system are outside the system scope, everything else is in the system scope and would be represented as one or more processes.

A DFD fragment…

is a DFD that represents the system response to one event within a single process symbol
is a self contained model showing how the system respond to a single event
usually created one at a time
A event-partitioned system model, or diagram 0…

a DFD that models system requirements using a single process for each event in a system or subsystem
used primarily as a presentation tool
summarises an entire system or subsystem in greater detail than the context diagram
diagram is often complex and unwieldy
Physical & Logical DFDs

A DFD can be a…

physical system model,
or a logical system model,
or a blend of the two.
If a DFD is a logical system model it assumes that the system might be implemented with any technology.

If a DFD is a physical model one or more assumptions about the technology will be embedded in the DFD.

A number of elements indicate assumptions about implementation technology…

Technology-specific processes
Actor-specific process names
Technology- or actor-specific process orders
Redundant processes, data flows, and files
If it is a logical system, it will make an assumption of perfect technology – meaning there would be no need to put in redundancy – i.e. capturing data incorrectly.

Analysts should avoid creating physical DFD’s during all analysis activities, except when generating alternatives.

Evaluating DFD Quality

High quality DFD’s are…

readable
internally consistent
accurately represent system requirements
have minimized complexity
Over complex models lead to information overload.

Information overload is when you have difficulty in understanding what occurs or when a reader receives too much information at one time. To avoid information overload we have the 7+-2 rule.

The rule of 7+-2 is the rule that limits the number of model components or connections among components to no more than nine.

Minimization of interfaces is directly related to the 7+-2 rule and is the principle of model design that seeks simplicity by limiting the number of connections among model components.

Ensuring Data Flow Consistency

Look for the following things in a DFD…

Differences in data flow content between process and its process decomposition.
Data outflows without corresponding data inflows.
Data inflows without corresponding data outflows.
The following words denote the above items one should look out for…

balancing – equivalence of data content between data flows entering and leaving a process and data flows entering and leaving a process decomposition DFD
black hole – a process of data store with a data input that is never used to produce a data output
miracle – a process or data store with a data element that is created out of nothing
How can black holes & miracles be detected…

Sometimes they can be detected by simply examining the DFD’s for consistency.
In some cases close examination of the data dictionary or process descriptions is also required.
Ensuring data flow consistency is a straightforward but tedious process, fortunately most analysis tools automatically perform consistency checks.
Documentation of DFD Components
In the traditional approach, DFD’s show all three types of internal system components on one diagram…

Processes
Data Flows
Data Stores
Process Descriptions

Each process of a DFD must be defined formally. There are several options for process definition, they include…

Process Decomposition (Explained in previous chapter)
Structured English
Decision Tables
Decision Trees
Each type of process is suited to a particular type of DFD process, i.e. a Structured English process might be well suited to record customer information, while a decision tree process might be a bad choice to represent this process.

Structured English is a method of writing process specifications that combines structured programming techniques with narrative English. See the example below…

001

Decision table is a tabular representation of processing logic containing decision variables, decision variable values, and actions or formulas. See the example below…

002

Decision tree is a graphical description of process logic that uses lines organized like branches of a tree. See the example below…

003


 

Functional requirements documentation for the traditional approach includes

an ERD with attributes
the set of DFD’s (context DFD, DFD Fragments, and any needed detailed DFD’s
process descriptions
data flow definitions, data store definitions & data element definitions
 

 

A data flow definition is a textual description of a data flow’s content and internal structure.

Data element definitions describe a data type, such as a string or integer. Each element should be described to indicate specifically what it represents.

Analysts need to maintain a central store of all these definitions as a project reference and to ensure consistency. A data dictionary is a repository for definitions of data flows, data stores, and data elements.

DFD Summary

A DFD will contain

Data Flow Diagrams
Process Definitions
Data Definitions
ERD Diagrams
Locations & Communication through Networks
Because structured systems analysis concentrates on logical modelling, physical issues such as processing locations and networks are sometimes ignored during analysis. However a great deal of information about process, data, and user distribution is needed during the early stages of design. Examples include…

Number of locations of users
Processing and data access requirements of users at specific locations
Volume and timing of processing and data access requests
Gathering location information during analysis enables analysts to make better decisions during the last two analysis activities…

Generate & Evaluate Alternatives
Review Recommendations with Management
There are a few steps involved in gathering location information, they are outlined below…

Generate a location diagram
Generate an activity matrix based on the location diagram