---
layout: post
title: Object Oriented Analysis UNISA Studies - Chap 15
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA ICT 2622 tag should be considered study notes for my lectures...

Objectives of Chapter 15

Discuss examples of system interfaces found in information systems
Define system inputs and outputs based on the requirements of the application program
Design printed and on-screen reports appropriate for recipients
Explain the importance of integrity controls
Identify required integrity controls for inputs, outputs, data, and processing
Discuss issues related to security that affect the design and operation of information systems
Key Words & Definitions
ad hoc reports – reports that are not predefined by a programmer but designed as needed by a user
detailed report – a report containing detailed transactions or records
summary report – a report that recaps or summarizes detailed information over a period of time or some category
exception report – a report that contains only information about nonstandard, or exception, conditions
executive report – a summary report from various information sources that normally used for strategic decisions
internal output – a printed report or document produced for use inside an organization
external output – printed documents – such as statements, notices, form letters, and legal documents – produced for use outside an organization
turnaround document – an external output that includes a portion that is returned to the system as an input
control break report – a report that includes detailed and summary information
drill down – to link a summary field to its supporting detail and enable users to view the detail dynamically
integrity control – mechanisms and procedures that are built into an application system to safeguard information contained within it
field combination control – an integrity control that verifies the data in one field based on data in another field or fields
value limit control – an integrity control that identifies when a value in a field is too large or too small
completeness control – an integrity control to ensure that all necessary fields on an input form have been entered
data validation control – an integrity control to validate the input data for correctness and appropriateness
access control – an integrity control that determines who has access to a system and its data
transaction logging – a technique whereby all updates to a database are recorded with the information or who, when, and how the update was performed
destination controls – integrity controls to ensure that output information is channelled to the correct people
security control – mechanisms usually provided by the operating system or environment to protect the data and processing systems from malicious attack
unauthorized user – a person who does not have authorized access to a system
registered user – a user who is registered or known to the system and is authorized to access some part of it
authorization – the process of determining whether a user is permitted to have access to the system and data
access control list – the list of users who have rights to access the system and data
privileged user – a user who has special security access privileges to a system
authentication – the process of identifying a user to verify that he can have access to the system
smart card – a computer-readable plastic card with security information embedded within it
encryption – the process of altering data so that it is unreadable by unauthorized users
decryption – the process of converting encrypted data back into a readable format
encryption algorithm -  a complex mathematical formula and process that encrypts or decrypts data
encryption key – a binary field that the encryption algorithm uses to transform data
symmetric key encryption – an encryption process that uses the same key to encrypt and to decrypt the data
asymmetric key encryption – an encryption process that uses one key to encrypt a different key to decrypt the data
public key encryption – a asymmetric key method in which one key is publicized and the other key is kept private
digital signature -  a technique in which a document is encrypted using private key to verify who wrote the document
certificate, or digital certificate – a text message that is encrypted by a verifying authority and used to broadcast an organizations name and public key
certifying authority – a well-known third party that sells digital certificates to organizations
secure sockets layer – a standard protocol to connect and transmit encrypted data
transport layer security – an updated version of ssl
secure hypertext transport protocol – an internet standard for transmitting web pages securely
Example Questions on this Section
What are the objectives of integrity controls in information systems? Explain what each of these three objectives mean, give an example of each.
Compare the strengths and weaknesses of using a DFD to define inputs with using a sequence diagram to define inputs. Which do you like best and why?
Based on the DFD given in Chapter 10 (Figure 10-26), add class schedule to the structure chart you developed there, identify the set of input and output screens for the system. Include the data fields that would be required.
A university library system is depicted in figure 14-25, with partial system sequence diagrams for two use cases, “Check out a book and return a book”. Based on the figure, construct four tables showing inputs and outputs, as shown in  figures 14-10 and 14-12 : Inputs for the Library System, (2) Outputs for the Library System, (3) Inputs for the Student Record System, and (4) Outputs for the Student Record System
Refer to the case study : TheEyesHaveIt.com Book Exchange System. Based on the system sequence diagrams below, develop a list of inputs and outputs required for this system. Also, identify any specific controls that might be necessary to ensure that information is entered accurately.
Identifying System Interfaces
System interfaces are any inputs or outputs with minimal or no human interfaces.

System interfaces can process inputs, interact with other systems in real time, and distribute outputs with minimal human intervention. The following list provides some categories of system interfaces to aid in identifying I/O requirements and design possibilities.

Inputs from other systems
Highly automated inputs
Inputs that are from data in external databases
Outputs that are to external databases
Outputs with minimal HCI
Outputs to other systems
Real-time connections (both input and output)
One of the biggest challenges of system interfaces is getting systems to communicate with each other. A popular format for achieving this is using XML data that can be easily transformed so that different systems can understand it.

Designing System Inputs
When designing inputs for a system, the system developer must focus on three areas:

Identifying the devices and mechanisms that will be used to enter input
Identifying all system inputs and developing a list with the data content of each
Determining what kinds of controls are necessary for each system input
Input Devices and Mechanisms
The primary objective of any form of data input is to enter or update error-free data into the system. The key term is error-free. Several good practices cam help reduce input errors…

Capture the data as close to the originating source as possible.
Use electronic devices and automatic entry whenever possible.
Avoid human involvement as much as possible.
If the information is available in electronic form anywhere, use it instead of re-entering the information.
Validate and correct information at the time and location it is entered.
One of the most common sources of errors in data entry is typing mistakes by users. A few of the more prevalent devices used to avoid human key stroking are as follows…

Magnetic card strip readers
Barcode readers
Optical character recognition readers and scanners
Radio-frequency identification tags
touch screens and devices
Electronic pens and writing surfaces
Digitizers such as digital cameras and digital audio devices
Defining the Details of System Inputs
The objective of this task is to ensure that the designer has identified all of the required inputs to the system and specified them correctly.

The fundamental approach that analysts use to identify user and system inputs is to identify all information flows that cross the system boundary for each activity or use case.

Using Traditional Structured Models

During systems design with structured techniques, one of the first tasks is to define the automation boundary. Even though it is possible to build an automation boundary on a high level DFD and identify the inputs on the diagram, it is usually better to work from the DFD fragments or even more detailed DFD’s because the high level DFD frequently does not provide enough detail to discern many data flows and hence inputs to the system.

The designer analyzes each DFD fragment to determine the required inputs. The data flows that cross the boundary on the DFD’s as inputs correspond to triggers for external events in the event table. The result of this task is a list of high level inputs for the new system.

The purpose of the preliminary list is to provide a master control list of all system inputs and user inputs that need to be designed. It does not provide quite enough detailed information to design the inputs themselves. The additional information that is needed is obtained from the data flow definitions, structure charts, and the user-centred design activities.

While developing the structure charts, the designer defines individual program modules and their associated data couples. Each input data flow on a data flow diagram might translate into one or more physical inputs on the structure chart.

The next step is to analyze each module and data couple and list the individual data fields for each data couple. This analysis consists of reviewing the elements in the data stores to ensure that all elements can be built based on the input data couples.

Because the identification of the detailed data elements is based on the analysis models, including the entity relationship data model, it provides cross-check. Ensuring that the two approaches yield the same data elements is a powerful technique to verify the quality of design.

Using Object Oriented Models

Identifying user and system inputs with the object-oriented approach consists of the same tasks as with the traditional structured approach. The difference is that system sequence diagrams and design class diagrams are used. The system sequence diagrams identify the incoming messages, and the design class diagrams are used to identify and describe the input parameters.

Designing System Outputs
The primary objective of system outputs is to present information in the right place at the right time to the right people.

As with input design, the tasks in this activity accomplish four objectives…

Determine the type of each system output
Make a list of specific system outputs required based on application design
Specify any necessary controls to protect the information provided in the output
Design and prototype the output layout
Defining the details of System Outputs
The objective of this task is to ensure that the designer has identified and specified all of the outputs for the new system. The technique is the same as that used for the definition of the system inputs. This model-based approach utilizes the information in the event table and other models to identify and define the detailed specifications of the outputs.

Using Traditional Structured Models

To identify the outputs in the traditional approach, analysts look at data flows coming out of the system across the system boundary in the data flow diagrams and fragments.

As analysts build the table of DFD outputs, report definitions, and data fields, they add two more columns. These two additional columns list (1) the files or data stores that are required to produce the report, and (2) the number of records from which the report is generated (a single record or set of records).

To verify that the structure chart modules are consistent with the structure of the output report, analysts again look at the data couples and the report data requirements. An analysis of the data couple being sent to the module and the data fields on the output report will verify that the application has been designed correctly to generate the report.

Using Object Oriented Models

In the object-oriented approach, outputs are indicated by messages in sequence diagrams that originate from an internal system object and are sent to an external actor. A review of all the output messages generated across all sequence diagrams provides the consistency check against the required outputs identified during analysis activities.

Output messages that are based on an individual object are usually part of the methods of that object class. To report on all objects within a class, a class-level method is used. A class-level method is a method that works on the entire class of objects, not a single object.

Designing Reports, Statements, and Turnaround documents
There are several types of reports that can be generated by a system. Below is listed some of the main categories of reports…

ad hoc reports – reports that are not predefined by a programmer but designed as needed by a user
detailed report – a report containing detailed transactions or records
summary report – a report that recaps or summarizes detailed information over a period of time or some category
exception report – a report that contains only information about nonstandard, or exception, conditions
executive report – a summary report from various information sources that normally used for strategic decisions
Formatting Reports
With all of the choices available today for output formats, system designers have more flexibility in what they can offer users. Analysts must keep three principles in mind during the design of output reports…

What is the objective of the report
Who is the intended audience
What is the medium for presentation
Designing Integrity Controls
Information system controls are mechanisms and procedures that are built into a system to safeguard both the system and the information within it.

Generally, controls that are integrated into the application and database are called integrity controls. The controls in the operating system and network are often referred to as security controls.

Integrity controls are mechanisms and procedures that are built into an application system to safeguard information contained within it

Usually when considering integrity controls, system developers focus on avoiding problems with the application systems and the employees who rightly have access to those systems. The primary focus is internal and the primary objectives are…

Ensure the only appropriate and correct business transactions occur
Ensure that the transactions are recorded and processed correctly
Protect and safeguard the assets of the organization
Input Integrity Controls
The objective is to reduce bad data within the system by limiting erroneous input.

Some common control techniques include…

Field combination controls – ie. application date must be prior to date the policy is in force
Value limit controls – i.e. check amount is reasonable, a person cannot order negative quantity
Completeness controls – i.e. make sure required fields are completed before submitting a form
Data validation controls – i.e. validation of banking codes or checking ID numbers match ID format requirements
Database Integrity Controls
Five major areas of security and control can be implemented at the database level…

Access control
Data Encryption – i.e. encrypted password in the database
Transaction Control – i.e. transaction logging
Update Control – i.e. record locking
Backup and Recovery Protection – i.e. duplicate database backups
Output Integrity Controls
The purpose of the output controls is to ensure that output arrives at the proper destination and is accurate, current, and complete.

Destination controls are integrity controls to ensure that output information is channelled to the correct people. Typically for printed material.

Completeness, Accuracy, and Correctness Controls

The following items are controls that should be printed on reports…

Date and time of report printing
Date and time of data in the report
Time period covered by the report
Beginning header with report identification and description
Destination or routing information
Pagination in the form of page numbers and total page numbers on each page
Control totals and cross footings
An “End of Report” trailer
The report version number and version date
Integrity Controls to Prevent Fraud
Typically three conditions are present in almost all fraud cases…

Personal pressure, such as the desire to maintain an extravagant lifestyle
Rationalization, such as a person’s thought that “I will repay this money”
Opportunity, such as unverified cash receipts
Factors affecting fraud risk

Separation of duties
Inadequate audit trails
Inadequate records
Inadequate monitoring
Easily removable assets
Inadequate security system
Designing Security Controls
Although the objective of security controls is to protect the assets of an organization from all threats, the primary focus is generally on external threats.

Maintain a stable, functioning operating environment for users and application systems
Protect information and transactions during transmission outside the organization
Security for Access to Systems
System developers must consider different types of users when designing access controls. The following are some of the types of users.

unauthorized user – a person who does not have authorized access to a system
registered user – a user who is registered or known to the system and is authorized to access some part of it
authorization – the process of determining whether a user is permitted to have access to the system and data
access control list – the list of users who have rights to access the system and data
privileged user – a user who has special security access privileges to a system
 

Password and smart cards

Authentication is the process of identifying users who request access to sensitive resources. Authentication is the basis of all security because security controls are useless unless the user is correctly identified.

Two techniques are used to define passwords,

The computer can randomly generate and assign passwords
Each user can choose his/her own password
The big challenge is for users to remember their passwords…

A smart card is a computer-readable plastic card with security information embedded within it. The smart card can store an encrypted version of the user’s password, fingerprint, retinal scan, or voice characteristics.

Authentication can also be done by other devices such as biometric devices – i.e. fingerprints, etc.

Data Security
Data that resides on an internal system needs to be protected, but data that is being transmitted outside the organization is especially subject to snooping and even modification.

The primary method of maintaining security of data, both on internal systems and transmitted data, is by encrypting the data.

Encryption is the process of altering data so that it is unreadable by unauthorized users. An encryption key is a binary field that the encryption algorithm uses to transform data. The encryption algorithm is a complex mathematical formula and process that encrypts or decrypts data based on the encryption key.

Decryption is the process of converting encrypted data back into a readable format.

Symmetric key encryption is an encryption process that uses the same key to encrypt and to decrypt the data. A significant problem with this form of encryption is that both the sender and receiver use the same key, which must be created and shared in a secure manner.

Asymmetric key encryption is an encryption process that uses one key to encrypt a different key to decrypt the data. Public key encryption is a asymmetric key method in which one key is publicized and the other key is kept private.

Digital Signatures and Certificates
Digital signature is a technique in which a document is encrypted using private key to verify who wrote the document.

A certificate, or digital certificate is a text message that is encrypted by a verifying authority and used to broadcast an organizations name and public key.

There are many certifying authority who are well-known third party that sell digital certificates to organizations.

Secure Transactions
Secure sockets layer is a standard protocol to connect and transmit encrypted data. It was adopted by the internet and renamed to transport layer security.

Secure hypertext transport protocol is an internet standard for transmitting web pages securely that makes use of encryption, digital signing, and certificate exchange.