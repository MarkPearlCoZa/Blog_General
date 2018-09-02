---
layout: post
title: Object Oriented Analysis UNISA Studies - Chap 16
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA ICT 2622 tag should be considered study notes for my lectures…

Objectives of Chapter 16

Describe implementation and support activities
Choose an appropriate approach to program development
Describe various types of software tests and explain how and why each is used
List various approaches to data conversion and system installation and describe the advantages and disadvantages of each
Describe different types of documentation and the processes by which they are developed and maintained
Describe training and user support requirements for new and operational systems
Key Words & Definitions
input, process, output (IPO) development -  a development order that implements input modules first, process modules next, and output modules last
top-down development – a development order that implements modules at the top of a structure chart first
bottom-up development – a development order that implements modules at the bottom of a structure chart first
cooperating peer team – a team with members of roughly equal skill and experience and with overlapping areas of specialization
chief developer team – a team with a single leader who makes all important decisions
collaborative specialist team – a team with members who have wide variation in and minimal overlap of skills and experience
source code control system – an automated tool for tracking source code files and controlling changes to those files
alpha version – a system that is incomplete but ready for some level of rigorous testing
beta version – a system that is stable enough to be tested by end users
production version, release version or production release – a system that is formally distributed to users or made operational
maintenance release – a system update that provides bug fixes and minor changes to existing features
quality assurance (QA) – the process of ensuring that an information system meets minimal quality standards
technical review – a formal or informal review of design or construction details by a group of developers
inspection – a formal review of design or construction details by a group of developers, where each person plays a specific role
test case – a formal description of a starting state, one or more events to which the software must respond, and the expected response or ending state
test data – a set of starting states and events used to test a module, a group of modules, or an entire system
unit testing, or module testing – testing of individual code modules or methods before they are integrated with other modules
driver – a module, developed for unit testing, that simulates the calling behaviour of a module that hasn’t yet been developed
stub – a module, developed for testing, that simulates the execution or behaviour of a module that hasn’t yet been developed
integration test – a test of the behaviour of a group of modules or methods
system test – a test of the behaviour of an entire system or independent system
build and smoke test – a system test that is performed daily
usability test – a test to determine whether a module, method, class, subsystem, or system meets user requirements
performance test -  a system test that determines whether a system can meet time-based performance criteria
response time – the desired or maximum allowable time limit for software response to a query or update
throughput – the desired or minimum number of queries and transactions that must be processed per minute or hour
acceptance test – a system test that determines whether the system fulfils user requirements
testing buddy – a programmer assigned to test code written by another programmer
direct installation, or immediate cutover – an installation method that installs new system, quickly makes it operational, and immediately turns off any overlapping systems
parallel installation – an installation method that operates both the old and new systems for an extended period of time
phased installation – an installation method that installs a new system and makes it operational in a series of steps or phases
system documentation – descriptions of system functions, architecture, and construction details, as used by maintenance personnel and future developers
user documentation – descriptions of how to interact with and maintain the system, as used by end users and system operators
software maintenance – modification of a software product after delivery to correct faults, improve performance or other attributes, or adapt the product to a changed environment
production system – the version of the system used from day to day
test system – a copy of the production system that is modified to test changes
Example Questions on this Section
Define the terms alpha version, beta version, and production version. Are there well defined criteria for deciding when an alpha version becomes a beta version or a beta version becomes a production version?
What are characteristics of good test cases?
What factors make testing object-oriented programs more complex than testing structured programs?
Program Development
Developing a complex system is an inherently difficult process. When most people think of system development, they primarily think of programming. It's importance arises from several factors, including the following…

Required resources
Managerial complexity
System quality
Program development consumes more resources than any other system development activity and typically accounts for between one third and half of the project development schedule.

Order of Implementation
One of the most basic decisions to be made about program development is the order in which program components will be developed. Several orders are possible, including…

Input, process, output
Top-down
Bottom-up
Input, process, output (IPO) development is  a development order that implements input modules first, process modules next, and output modules last.

The main advantage of the IPO development order is that it simplifies testing. IPO development order is also advantageous because important user interfaces are developed early.

A disadvantage of IPO development order is the late implementation of outputs. Output programs are useful for testing process-oriented modules and programs.

Top-down development is a development order that implements modules at the top of a structure chart first.

Bottom-up development is a development order that implements modules at the bottom of a structure chart first.

There are other factors that need to be considered as well when developing a system. These include…

User Feedback
Training
Documentation
Use Case Driven Development
Testing
Framework Development
Typically there are a set of foundation classes that are used through out a system. It is important that these classes are tested thoroughly as changes done at a later stage to the foundation classes will have a ripple effect to all systems based on them.

Team-Based Program Development
Team based program development has many advantages, but also introduces several challenges including…

Organization of programming teams
Task assignment to specific teams or members
Member and team communication and coordination
Also, teams need to be organized, some common organization formations include…

Cooperating Peer – equal skills, overlapping specialties, consensus based decision
Chief Developer – organized as a military platoon, one leader makes all important decisions
Collaborative Specialist – wide variation in skills, leader is primarily administrative
Depending on the type of project, different team structures may be best suited.

Source Code Control
A source code control system (SCCS) is an automated tool for tracking source code files and controlling changes to those files.

A SCCS prevents multiple programmers from updating the same file at the same time, and is a necessity for multiple developer teams.

A SCCS also provides additional features such as backup and recovery operations.

Versioning
Versioning is critical, especially when a system is being continually developed and changed.

Test versions provide a static system snapshot and a checkpoint to evaluate the project’s progress.

The following names are generally used to define snapshot versions…

alpha version – a system that is incomplete but ready for some level of rigorous testing
beta version – a system that is stable enough to be tested by end users
production version, release version or production release – a system that is formally distributed to users or made operational
maintenance release – a system update that provides bug fixes and minor changes to existing features
Version control capabilities are typically built into SCCS.

Quality Assurance
Quality assurance (QA) is the process of ensuring that an information system meets minimal quality standards as determined by users, implementation staff, and management.

Quality assurance is a set of activities that are performed throughout the SDLC to build systems correctly from the start and to detect and fix errors as soon as possible.

QA activities during analysis concentrate on identifying gaps or inconsistencies in system requirements. QA activities during design concentrate on satisfying stated requirements and on making design decisions that will lead to easily implemented, bug-free programs. QA during implementation consist primarily of testing.

QA is essential to build into the SDLS early as the cost of repairing an error at a later stage in the cycle is extremely expensive compared to early in the cycle.

Technical Reviews
Technical review is a formal or informal review of design or construction details by a group of developers. Technical reviews vary from one organization to another and from project to project.

Inspection is a formal review of design or construction details by a group of developers, where each person plays a specific role. A walkthrough would be similar to an inspection, however it would be less formal.

Walkthroughs and inspections are important QA processes because they can detect errors before code has been written.

Testing
Testing is the process of examining a product to determine what defects it contains. To conduct a test, programmers must have already constructed the software and have well-defined standards for what constitutes a defect.

Software Testing has many different areas and can be done throughout the SDLC.

Integration testing is where groups are components are tested.
Unit testing is where individual components are tested.
System testing is where the entire system is tested.
An important part of developing tests is specifying test cases and data. A test case is a formal description of the following…

A starting state
One or more events to which the software must respond
The expected response or ending state
Both starting state and events are represented by a set of test data.

A test case is a formal description of a starting state, one or more events to which the software must respond, and the expected response or ending state

Test data is a set of starting states and events used to test a module, a group of modules, or an entire system.

Unit Testing

Unit testing, or module testing is testing of individual code modules or methods before they are integrated with other modules.

The goal of unit testing is to identify and fix as many errors as possible before modules are combined into larger software units. Errors become more difficult and expensive to locate and fix when many modules are combined.

Few modules are designed to operate in isolation. Instead, groups of modules are designed to execute as an integrated whole.

A driver is a module, developed for unit testing, that simulates the calling behaviour of a module that hasn’t yet been developed. Using drivers enables testing of a subroutine module before modules that call it have been written. Drivers are used extensively in bottom-up development because child modules are developed and unit-tested before their parents are developed.

A stub is a module, developed for testing, that simulates the execution or behaviour of a module that hasn’t yet been developed. Stubs are needed for top-down development. Often with top down development begins with writing a stub for every module or method in a program or class.

Integration Testing

Integration test is a test of the behaviour of a group of modules or methods.

The purpose of an integration test is to identify errors that were not or could not be detected by unit-testing individual modules or methods. Such errors could arrise from a number of problems, including…

Interface incompatibility – a caller module passes a variable of the wrong data type to a subordinate module.
Parameter values – a module is passed or returns a value that was unexpected
Run-time exceptions – a module generates an error such as “out of memory” due to conflicting resource needs
Unexpected state interactions – the states of two or more modules interact to cause complex failures
Integration testing is easier for traditional systems, but are more complicated for OO systems as in OO systems methods are called from a number of places.

System Testing

A system test is a test of the behaviour of an entire system or independent system.

If a system is developed in many iterations, system testing is usually performed at the end of each iteration to identify significant issues such as performance problems that must be addressed in the next iteration.

A build and smoke test is a system test that is performed daily. The system is completely compiled and built and tested to see if anything malfunctions in an obvious way. Build and smoke tests are commonly associated with iterative or rapid development.

Usability Testing

A usability test is a test to determine whether a module, method, class, subsystem, or system meets user requirements.

A performance test is a system test that determines whether a system can meet time-based performance criteria. Response time requirements specify the desired or maximum allowable time limit for software response to a query or update. Throughput requirements specify the desired or minimum number of queries and transactions that must be processed per minute or hour. An acceptance test is a system test that determines whether the system fulfils user requirements.

Who Tests Software

Programmers are generally responsible for their own unit testing. In some instances programmers are assigned a testing buddy who is a programmer assigned to test code written by another programmer. Having a different programmer test code to the one who wrote it often results in more errors being found.

Data Conversion
Reusing Existing Databases
Most new information systems replace or augment an existing manual or automated system. In the simplest form of data conversion, the old system database is used directly by the new system with little or no change to the database structure.

Reusing an existing database is fairly common because of the difficulty and expense of creating new databases from scratch.

Reloading Database Contents
Sometimes more complex changes to database structure might require reloading data after the change. In that instance programs are created to convert / alter data to the new format.

Creating New Databases
If a system is entirely new or if it replaces a manual system, initial data must be obtained from manual records or from other automated systems in the organization. One approach is to add data as needed which has the benefit of reducing upfront costs, but has the downside that the initial loading of data may slow the system down initially until all required data is loaded onto the new system.

Installation
Installing a system and making it operational are complex because there are many conflicting contraints, including cost, customer relations, employee relations, logistical complexity, and overall exposure risk.

Some of the important issues to consider when planning installation including…

Incurring costs of operating both systems parallel
Detecting and correcting errors in the new system
Potentially disrupting the company and its IS operations
Training personnel and familiarizing customers with new procedures
Different approaches to installation represent different trade-offs among cost, complexity, and risk. Some of these approaches include…

Direct Installation
Parallel Installation
Phased Installation
Direct Installation
In a direct installation, or immediate cutover it is a installation method that installs new system, quickly makes it operational, and immediately turns off any overlapping systems.

The primary advantage is that it is simple to implement.

The primary disadvantage is the risk level, because if there are errors in the system, it is effecting live business processes.

Direct installation is typically used under one or both of the following conditions…

The new system is not replacing an older system
Downtime of days or weeks can be tolerated
If neither condition applies, parallel or phased installation is usually preferable to minimize risk of system unavailability.

Parallel Installation
Parallel installation is an installation method that operates both the old and new systems for an extended period of time.

Ideally the old system continues to operate until the new system has been thoroughly tested and determined to be error-free and ready to operate independently.

The primary advantage of parallel installations is a relatively low risk of system failure and the negative consequences that might result from that failure.

The primary disadvantage of parallel installation is cost. The organization pays to operate both systems including the costs of…

Hiring temporary personnel or temporarily reassigning existing personnel
Acquiring extra space for computer equipment and personnel
Increasing managerial and logistical complexity
Phased Installation
Phased installation is an installation method that installs a new system and makes it operational in a series of steps or phases.

During each phase the system is tested to ensure that it is ready for the next phase.

The primary advantage of phased installation is reduced risk. If a single phase fails, it is generally less problematic than if an entire system fails.

Phased installation is also useful when the system is extremely large, complex, and composed of relatively independent subsystems.

Personnel Issues
Note that when systems are being implemented, there is increased stress on personal. This needs to be taken into consideration and steps implemented to reduce these levels of stress.

This can be done by hiring more temporary staff during the period as well as a number of other measures.

Documentation
Preparing documentation is important but frequently overlooked.

Automated documentation is now the norm, and formats include the following…

Electronic Documents – PDF files
Hyperlinked Documents – formatted for web browsers
Online documentation – stored on a website
Embedded Documentation – stored on DVD or CD
Electronic system models – stored as Jpegs or BMP’s
Tool Specific System Models – IDE models, etc
Documentation can be loosely classified into two types…

System documentation
User Documentation
System Documentation
System documentation has descriptions of system functions, architecture, and construction details, as used by maintenance personnel and future developers.

It serves one primary purpose – providing information to designers and developers who will maintain or re-implement the system.

System documentation must be actively managed to remain effective. It must be stored in an accessible location and form, retrieved when necessary for maintenance changes, and updated after changes have been implemented.

User Documentation
User documentation has descriptions of how to interact with and maintain the system, as used by end users and system operators.

Topics typically covered include the following…

Software Startup and Shutdown
Keystroke, mouse, or command sequences required to perform specific functions
Program functions required to implement specific business procedures
Common errors and ways to correct them
User documentation is an important organizational asset,  however many organizations fail to prepare comprehensive high-quality user documentation for internally developed systems. Some of the reasons include…

The assumption that trained programmers can examine the source code, figure out how the system works and train users.
The assumption that users trained during system implementation will informally pass on their knowledge to future users.
The lack of resources and special skills required to develop documentation and keep it up to date.
Training and User Support
There are two classes of users – end users and system operators. Both types will need training and support.

Training and support activities vary with the target audience. Audience characteristics that affect training include the following…

Frequency and duration of system use
Need to understand the system’s business context
Existing computer skills and general proficiency
Number of users
Generally system operators use the system infrequently, while end users use the system frequently.

System operators are few while end users may be many – so different training methods are feasible with each type (i.e. one on one training with system operators may be feasible).

Ongoing Training and User Support
User support can be provided by a number of methods, including the following…

Online documentation and troubleshooting
Resident experts
A help desk
Technical support
Each method has its own advantages and disadvantages, typically the easier the support & training, the more expensive (i.e. online documentation is cheaper than one on one training to many users).

Maintenance and System Enhancement
Software maintenance is the modification of a software product after delivery to correct faults, improve performance or other attributes, or adapt the product to a changed environment.

The term maintenance covers virtually everything that happens to a system after delivery except for total replacement or abandonment.

Maintenance activities include the following…

Tracking modification requests and error reports
Implementing changes
Monitoring system performance and improving performance or increasing capacity
Upgrading hardware and system software
Updating documentation to reflect maintenance changes
Submitting Change Requests and Error Reports
To reduce risk associate with changing a system, most organizations adopt formal control procedures for all operational systems.

Typical change control procedures include the following…

Standard change request forms
Review of requests by a change control committee
Extensive planning for design and implementation
Implementing a Change
Planning for change includes the following activities…

Identify what parts of the system must be changed
Secure resources to implement the change
Schedule design and implementation activities
Develop test criteria and a testing plan for the changed system
Implementation activities are normally performed on a copy of the operational system.

The production system is the version of the system used from day to day while the test system is a copy of the production system that is modified to test changes.

The test system becomes operational system only after complete and successful testing.

Upgrading Computer Infrastructure
Computer hardware, system software, and networks must be periodically upgraded for many reasons, including the following…

Software maintenance releases
Software version upgrades
Declining system performance
The rule is as follows… if an operational system isn’t broken, don’t fix it. However also keep up to date of changes to predict when major upgrades of infrastructure are necessary.