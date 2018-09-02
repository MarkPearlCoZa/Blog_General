---
layout: post
title: Programming Contemporary Concepts UNISA studies – Chap 11
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA COS 2144 tag should be considered study notes for my lectures...

Section Outline
Widget Categories
QMainWindow & QSettings
Dialogs
Images and Resources
Layout of Widgets
QActions, QMenus, and QMenuBars
QActions, QToolbars, and QActionGroups
Regions and QDockWidgets
Questions for this Section
List six things that QWidgets have in common
How can you save and later restore the size, position, and arrangements of widgets for a GUI app?
Why would you want to do such a thing?
What is a dialog? Where is an appropriate place to use it?
What is a QLayout? What is its purpose? What is an example of a concrete QLayout class?
Can a widget be a child of a layout?
Can a layout be a child of a widget?
What are the advantages of listing our images in a resource file?
What is the difference between a spacer and a stretch?
What is a QActiuon? How are actions triggered?
It is possible to create QMenus without sing QActions. What are the advantages of using a QAction?
General
QWidgets interact wit their children in interesting ways. A widget that has no parent is called a window. If one widget is a parent of another widget, the boundaries of the child widget lie completely within the boundaries of the parent. The contained child widget is displayed according to layout rules.

A typical desktop GUI application can contain many different QWidget-derived objects, deployed according to parent-child relationships and arranged according to the specifications of the applicable layouts.

A QWidget is considered to be the simplest of all GUI classes, because it is rendered as an empty box.

Widget Categories
There are four categories of widgets…

Button widgets
Input widgets
Display widgets
Container widgets
In addition to the widgets, there are some Qt classes that do not have any graphical representation but are used in GUI development. They include…

Qt Data types
Controller classes
Layouts
Models
Database Models
QMainWindow and QSettings
QMainWindow
QMainWindow is the parent of all other widgets (in the main window).

It is common practice to extend the class for some applications.

QSettings – Saving and Restoring Application State
QSettings is a persistent map of key/value pairs. It is a QObject and uses QObject’s property interface, setValue() and value(), to set and get its values. It can be used to store any data that needs to be remembered across multiple executions.

 

Monostate Pattern – A class that allows multiple instances to share the same state is an implementation of the Monostate pattern.

 

The mechanism for the persistent storage of QSettings data is implementation dependent and quite flexible.

Dialogs
a dialog box pops up, shows the user something, and gets a response back from the user. It’s a brief interaction that can force the user to respond.

QDialog, the base class for dialogs.

It has a bool attribute named modal which sets whether the dialog will be displayed modally or not.

In general dialog boxes should be used for obtaining or communicating important information that should be dealt with before the program can proceed.

Input Dialogs and Widgets
When a user enters text into a box, it is an input widget, probably a QLineEdit or a QComboBox, QSpinBox, or QTextEdit. These widgets are never solitary because there needs to be a least a label nearby that tells the user what information is required.

Input dialogs are higher-level widgets that group together the lower-level input widgets with labels and decorations for convenience.

Images and Resources
Graphic images can be used to add visual impact to various applications.

Qt enables projects to make use of binary resources, such as images, sounds, icons, text, and so forth. Resources such as these are generally stored on disk in separate binary files.

The advantage of incorporating binary dependencies in the actual project is that they can then be addressed using paths that do not depend on the local file system, and they can “move” with the executable.

Attaching required binary data files to projects as resources makes the project more robust, The source code does not need to use non-portable pathnames for the resource files.

Layout of Widgets
A widget can be popped up on the screen, like a dialog, or it can be made a part of a larger window.

Whenever we wish to arrange similar widgets inside larger ones, you use layouts.

A layout is an object that belongs to exactly one widget. Its sole responsibility is to organize the space occupied by its owner’s child widgets.

Absolute sizing and positioning are rarely used in a windowing application because they impose an undesirable rigidity on the design.

The process of specifying the way that your widgets will be be arranged on the screen consists of dividing the screen into regions, each controlled by a QLayout. 

Layouts can arrange their widgets…

Vertically
Horizontally
In a grid
In a stack where only one widget is visible at any time
Widgets are added to QLayouts using the addWidget() function.

Layouts can have child layouts. One layout can be added as a sub-layout to another by calling addLayout().

Spacing, Stretching, and Struts
To get finer control over the layout of widgets, we can use the API of QLayout class. Box layouts, offer the following functions…

addSpacing – adds fixed pixel to end of layout
addStretch – adds a stretchable number of pixels
addStrut – imposes a minimum size to the perpendicular dimension
Normally layouts try and treat all widgets equally. When we want one widget to be off to a side, or pushed away from another, we use stretches and spacing to deviate from the norm.

QActions, QMenus, and QMenuBars
a QAction is a QObject that is a base class for user-selected actions. It provides a rich interface that can be used for a wide variety of actions.

A QMenu is a QWidget that provides a particular kind of view for a collection of QActions.

QActions, QToolbars, and QActionGroups
The command pattern encapsulates operations as objects with common execution interface. This can make it possible to place operations in a queue, log operations, and undo the results of an already executed operation.

Because and application might provide a variety of different ways for the user to issue the same command, encapsulating each command as an action helps to ensure consistent, synchronized behaviour across the application.

In Qt GUI applications, actions are typically triggered in one of the following ways…

A user clicks on a menu choice
A user presses a shortcut key
A user clicks on a toolbar button
Regions and QDockWidgets
Any class that derives from QMainWindow has four dock window regions, one on each of the four sides of the central widget. These four regions are used for attaching secondary windows to the central widget.