---
layout: post
title: Object Oriented Analysis UNISA Studies - Chap 14
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA ICT 2622 tag should be considered study notes for my lectures...

Objectives of Chapter 14

Describe the difference between user interfaces and system interfaces.
Explain why the user interface is the system to the users
Discuss the importance of the three principles of user-centred design
Describe the historical development of the field of human-computer interaction (HCI)
Describe the three metaphors of human-computer interaction
Discuss how visibility and affordance affect usability
Apply the eight golden rules of dialog design when designing the user interface
Define the overall system structure as a menu hierarchy
Write user-computer interaction scenarios as dialogs
Create storyboards to show the sequence of forms used in a dialog
Design windows forms and browser forms that are used to implement a dialog
List the key principles used in Web Design
Key Words & Definitions
System interfaces – the parts of an information system involving inputs and outputs that require minimal human intervention
User interfaces – the parts of an information system requiring user interaction to create inputs and outputs
human-computer interaction (HCI) – the study of end users and their interactions with computers
user’s model – what the user knows about using the system, including the problem domain things the user is manipulating, the operations that can be performed, and the procedures followed when carrying out tasks
user-centred design – a collection of techniques that place the user at the centre of the development process
usability – the degree to which a system is easy to learn and use
human factors engineering (ergonomics) – the study of human interaction with machines in general
direct manipulation – a metaphor of HCI in which the user interacts directly with objects on the display screen
desktop metaphor – a direct manipulation approach in which the display screen includes an arrangement of common objects found on a desk
document metaphor – a metaphor of HCI in which interaction with the computer involves browsing and entering data in electronic documents
hypertext – documents that allow the user to click on a link and jump to different part of the document or to another document
hypermedia – technology that extends the hypertext concepts to include multimedia content such as graphics, video, and audio
dialog metaphor – a metaphor of HCI in which interacting with the computer is muck like carrying on a conversation or dialog
interface design standards – general principles and rules that must be followed for the interface of any system developed by the organization
visibility – a key principle of HCI that states all controls should be visible and provide feedback to indicate that the control is responding to the user’s action
affordance – a key principle of HCI that states the appearance of any control should suggest its functionality
storyboarding – a technique used to document dialog designs by showing a sequence of sketches of the display screen
browser forms – forms programmed using html and script languages that follow internet conventions
text box – an input control that accepts keyboard data entry
list box – an input control that contains a list of acceptable entries the user can select
spin box – a variation of the list box that presents multiple entries in a text box from which the user can select
combo box – another variation of the list box that permits the user to enter a new value of select from the entries
radio buttons – input controls that enable the user to select one option from a group
check boxes – input controls that enable the user to select more than one option from a group
Identifying and Classifying Inputs and Outputs
Inputs and outputs are an early concern of any system development project. The project plan lists the inputs and outputs that the analyst has identified when defining the scope of the system. These inputs & outputs are either user based or system based interfaces.

A system interface is the part of an information system involving inputs and outputs that require minimal human intervention while a user interface is the parts of an information system requiring user interaction to create inputs and outputs.

Understanding the User Interface
Human-computer interaction (HCI) is the study of end users and their interactions with computers. There are many different aspects of HCI including…

Physical Aspects of the User Interface – includes devices the user touches, reference manuals, data entry forms etc.
Perceptual Aspects of the User Interface – includes everything the end user sees, hears, or touches. All data displayed on the screen, speech recognition software, etc.
Conceptual Aspects of the User Interface – Includes everything the user knows about the system. Problem domain things, the user’s model of the system, etc.
A user’s model is what the user knows about using the system, including the problem domain things the user is manipulating, the operations that can be performed, and the procedures followed when carrying out tasks.

User Centred Design
User-centred design is a collection of techniques that place the user at the centre of the development process. It includes the following principles…

Focus early on the users and their work
Evaluate designs to ensure usability - usability is the degree to which a system is easy to learn and use.
Use iterative development – after each iteration analyze the user requirements and how they have been met.
The traditional approach to system design focuses more on business processes while the object oriented approach is more user centric.

A major challenge facing user centred design is that a system that is often easy to learn is not easy to use. The ideal is to get a system that is easy to learn and easy to use.

Human-Computer Interaction as a Field Study
Human factors engineering or ergonomics is the study of human interaction with machines in general. The field of human factors was first associated with engineering because engineers designed machines, however engineers are used to precise specifications and predictable behaviour and often find human factor frustrating.

Information systems specialists with an interest in human-computer interaction study computers the following disciplines…

Sociology
Cognitive Psychology
Linguistics
Anthropology
Physiology
Computer Science
Engineering
Graphic Art
Media
Social Psychology
Metaphors for Human-Computer Interaction
There are many ways to think about human-computer interaction, including metaphors or analogies. Three alternatives are…

Direct Manipulation Metaphor
Document Metaphor
Dialog Metaphor
The direct manipulation metaphor is a metaphor of HCI in which the user interacts directly with objects on the display screen. An example of this would be word processors.

Direct manipulation coupled with object-oriented programming eventually evolved into the desktop metaphor. The desktop metaphor is a direct manipulation approach in which the display screen includes an arrangement of common objects found on a desk. An example would be a calculator, clock, etc.

Another view of the interface is the document metaphor. The document metaphor is a metaphor of HCI in which interaction with the computer involves browsing and entering data in electronic documents. An example of this would be the internet.

Finally, another view of the interface is the dialog metaphor. The dialog metaphor is a metaphor of HCI in which interacting with the computer is muck like carrying on a conversation or dialog. An example of this (somewhat abstract) is using email – the user requests to check his inbox, and the computer displays the results.

Guidelines for Designing User Interfaces
User interface design guidelines range from general principles to very specific rules. Design standards help ensure that all user interfaces function well and that all systems developed by the organization have a similar look and feel.

Visibility and Affordance
Visibility states all controls should be visible and provide feedback to indicate that the control is responding to the user’s action.

Affordance states the appearance of any control should suggest its functionality.

A well designed interface has both visibility and affordance.

A high level of visibility and affordance will reduce the amount learning a user will need to do to use the system.

Eight Golden Rules
Another general guideline is the eight golden rules guideline.

Strive for consistency – interfaces need to be consistent through the system.
Enable Frequent Users to Use Shortcuts – shortcuts can help power users get more from the system.
Offer Informative Feedback – whether subtle or obvious it is important to let the user know that a request has been received and processed by the system.
Design Dialogs to Yield Closure – each dialog should be designed with a clear purpose – a beginning, middle and end.
Offer Simple Error Handling – if an error occurs,  the system should make it easy to correct the error and indicate it as early as possible.
Permit Easy Reversal of Actions - Users need to be able to feel like they can explore the system and undo any mistakes that they create.
Support internal locus of control – Users want to feel like they are in charge and should not be forced to do anything – i.e. forcing a reboot of a pc
Reduce short term memory load – People can remember only about 7 chunks of information at any one time. Systems should keep this in mind and display information out of this scope as reminders etc.
Documenting Dialog Designs
Many techniques are available to help the designer think through and document dialog designs.

Use Cases, Subsystems, and the  Menu Hierarchy
Inputs and outputs are obtained from data flow diagrams or use case and scenarios. Generally each input obtained interactively from a user requires a dialog design. Also, each output produced at the request of a user requires a dialog design.

Dialog design must be done simultaneously with other design activities.

Dialogs and Storyboards
After identifying all required dialogs, the designers must document the dialogs. There are no de facto standards and many options exist.

One technique used to show the screens of a dialog is storyboarding. Storyboarding is done by showing a sequence of sketches of the display screen. Designers can implement a storyboard with a visual programming system such as blend.

All the different approaches to dialog design provide only a framework to work from, and the resulting design remains fairly general.

Dialog Documentation and UML Diagrams
The OO approach provides UML diagrams that are useful for modelling user computer dialogs. Use case descriptions include a list of steps followed as the user and system interact.

The OO approach involves adding more types of objects to class diagrams and interaction diagrams as the project moves forward from analysis to design. The additional classes are packaged into three layers that contain user interface, problem domain and data access classes.

When a class is added to the user interface classes section, a dialog design can be created.

Guidelines for Designing Windows and Browser Forms
We need to consider two types of of forms…

Windows Forms
Browsers
Windows Forms are typically platform specific but are easy to design and flexible on the particular platform. Browser forms on the other hand are forms programmed using html and script languages that follow internet conventions that are platform independent.

There are 4 major issues to consider in the design of these forms.

Form layout and formatting
Data keying and entry
Navigation and support controls
Help support
Form Layout and Formatting
Form layout and formatting are concerned with the general look and feel of the form. The following considerations need to be made…

Consistency
Headings, Labels and Logos
Distribution and order of data-entry fields and buttons
Font sizes, highlighting, and colours
Data Keying and Data Entry
The heart of any input form is the entry of the new data.

The primary objective of data entry is to require as little data entry as possible. Any information already in the computer, or that can be generated by the computer should not be re-entered.

There are several types of data entry controls that can be used…  below is listed a few of the most general ones…

text box – an input control that accepts keyboard data entry
list box – an input control that contains a list of acceptable entries the user can select
spin box – a variation of the list box that presents multiple entries in a text box from which the user can select
combo box – another variation of the list box that permits the user to enter a new value of select from the entries
radio buttons – input controls that enable the user to select one option from a group
check boxes – input controls that enable the user to select more than one option from a group
 

One major difference between windows forms and browser forms is that in a basic browser input form, the edits are not performed until the entire form is transmitted to the server whereas with the windows forms the data can be submitted as it is entered.

Navigation and Support Controls
Windows forms include standard navigation such as maximize, Minimize and Close buttons

Browser forms include back buttons, etc.

Help Support
A primary objective in the design of each input form is that it should be intuitive so that users will not need help.

Most systems provide tutorials in training new users.

There is also context sensitive help which automatically displays the appropriate help topic based on the location of the insertion point.

Guidelines for Designing Web Sites
Website design is continually changing however below is outlined some general basic guidelines…

Ten good deeds in web design
After reading these guidelines I felt that they were way to general for any use and so have omitted them – if you need them then refer to page 553 of the text book.

Web site design principles
Five guidelines to consider include…

Craft the look and feel of the pages to take advantage of the medium
Make the design portable because it will be accessed with a wide range of technology
Design for low bandwidth because users will not want to wait for page loads
Plan clear presentation and easy access to information to ease users navigation through the site
Reformat information for online presentation when it comes from other sources
Designing the Whole Site

Craft the look and feel of the pages to match the impression desired by the organization
Create smooth transitions between web pages so users are clear about where they have been and where they are going
Lay out each page using a grid pattern to provide visual structure for related groups of information
Leave a reasonable amount of white space on each page between groups of information
Designing for the User

Design for interaction because web users expect sites to be interactive and dynamic
Guide the users eye to information on the page that is the most important
Keep a flat hierarchy so that the user does not have to drill down too deeply to find detailed information
Use the power of hypertext linking to help users move around and through the site
Decide how much content per page is enough based on the characteristics of the typical user.
Design for accessibility for a diverse group of users, including those with disabilities.