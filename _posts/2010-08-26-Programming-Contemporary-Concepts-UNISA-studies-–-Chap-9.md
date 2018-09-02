---
layout: post
title: Programming Contemporary Concepts UNISA studies – Chap 9
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA COS 2144 tag should be considered study notes for my lectures...

This chapter examines the QObject, which is an important class to become familiar with and one from which all Qt Widgets are derived.

Questions for this Section
What does it mean when object A is the parent of object B?
What happens to a QObject when it is reparented?
Why is the copy constructor of QObject not public?
What is the composite pattern?
How can QObject be both composite and component?
How can you access the children of a QObject?
What is an event loop? How is it initiated?
What is a signal? How do you call one?
What is a slot? How do you call one?
How are signals and slots connected?
How can information be transmitted from one object to another?
Deriving a class from QObject more than once can cause problems. How might that happen accidently.
What is the difference between value types and object types? Give examples.
Introduction
Below is an abbreviated look at the QObject Definition

class QObject {
public:
    QObject(QObject* parent=0);
    QObject * parent () const;
    QString objectName() const;
    void setParent ( QObject * parent );
    const ObjectList & children () const;
    // ... more ...
};
 
Things to notice about QObject…

Copy Constructor is not public – it is not meant to be copied
Intended to represent unique objects with identity
Can never be passed by value to any function
Each QObject can have at most one parent object & an arbitrarily large container of QObject* children
Each QObject stores pointers to its children in QObjectList (the list is lazy)
Each QObject parent manages its children (the QObject destructor automatically destroys all of its child objects)
QObject’s Child Management
Take the following program sample…

Main.cpp

#include <QtCore/QCoreApplication>
#include <QDebug>
#include "person.h"


int main(int argc, char *argv[])
{
    qDebug() << "First we create a bunch of objects." << endl;
    Person bunch(0, "A Stack Object");

    Person *mike = new Person(&bunch, "Mike");
    Person *carol = new Person(&bunch, "Carol");
    new Person(mike, "Greg");
    new Person(mike, "Peter");
    new Person(mike, "Bobby");
    new Person(carol, "Marcia");
    new Person(carol, "Jan");
    new Person(carol, "Cindy");
    qDebug() << "Display the list using QObject::dumpObjectTree()" << endl;
    bunch.dumpObjectTree();
    qDebug() << "Program Finished";

    QCoreApplication a(argc, argv);        
    bunch.~Person();
    return a.exec();    
}
 

Person.h

#ifndef PERSON_H
#define PERSON_H

#include <QObject>

class Person : public QObject
{
    Q_OBJECT

public:
    Person(QObject *parent, QString name);
    ~Person();

private:
    
};

#endif // PERSON_H
 

Person.cpp

#include "person.h"
#include <QTextStream>
static QTextStream cout(stdout, QIODevice::WriteOnly);

Person::Person(QObject *parent, QString name) : QObject(parent)
{
    setObjectName(name);
}

Person::~Person()
{
    cout << QString("Destroying Person: %1").arg(objectName()) << endl;
}
 

Output…

2010-08-26 06-40-21 AM

 

Composite Pattern: Parents & Children
(To find out more about the composite pattern see wiki here.)

The Composite Pattern is intended to facilitate building complex objects from simpler parts by representing the part-whole hierarchies as tree-like structures. This must be done in such a way that clients do not need to distinguish between simple parts and more complex parts that are made up of simpler parts.

There are two distinct classes for describing the the two roles.

A composite object is something that can contain children
A component object is something that can have a parent
The top level node or root of the tree will have no parent and possibly one or more children. Each level under that will have one parent and zero-many children.

There are several built in functions in the QObject that allow finding the children easy. One of these is the findChildren() method. The signature of one of its overloaded forms looks like this:

QList<T> parentObj.findChildren<T> ( cont QString & name) const

If name is an empty string, findChildren acts as a filter by returning a QList holding pointers to all children, which can be typecast to type T.

Observer Pattern
While the observer pattern is not explained properly in this section of the book, it is a useful pattern and more can be found out about it on wiki here.

The book mentions that in different languages there are different implementations, but that some of the common characteristics mentioned in the book of the observer pattern across languages/implementations was that…

They all enable concrete subject classes to be decoupled from concrete observer classes.
They all support broadcast-style communication (one to many).
The mechanism used to send information from subjects to observers is completely specified in the subject’s base class.
QApplication and the Event Loop
A typical Qt program creates objects, connects them, and then tells the application to exec(). At that point the objects can communication with each other in many different ways.

QWidgets send QEvents to other QObjects in response to user actions such as mouse clicks and keyboard events. Each QWidget can be specialized to handle keyboard and mouse events in its own way.

An event loop is a program structure that permits events to be prioritized, enqueued, and dispatched to objects. The event loop generally continues running until a terminating event occurs.

Signals and Slots

When the main thread of a c++ program call qApp->exec(), it enters into an event loop, where messages are handled and dispatched. While qApp is executing its event loop, it is possible for QObjects to send messages to one another.

A signal is a message that is presented in a class definition like a void function declaration, It has a parameter list but no body. Asignal is part of the interface of a class. It looks like a function but it cannot be called – it must be emitted by an object of that class. A signal is implicitly protected, and so are all the identifiers that follow it in the class definition until another access specifier appears.

A slot is a void member function. It is called as a normal member function. A signal of one object can be connected to the slots of one or more other objects, provided the objects exist and the parameter lists are assignment compatible from the signal to the slot.

Any QObject that has a signal can emit that signal, this will result in an indirect call to all connected slots.

Q_OBJECT and moc: A Checklist
QObject supports features not normally available in c++ objects. These include…

Children
Signals & Slots
MetaObjects, metaproperties, metamethods
qobject_cast
The way these additional features are made available is via “generated code”. The generated code (Meta Object Compiler) is stored in moc files.

This means that some errors can occur from the compiler/linker when moc is not able to find or process our classes. To avoid this we have some guidelines for writing c++ code and qmake project files…

Each class definition should go in its own .h file
Its implementation should go in a corresponding .cpp file
The header file should be #ifndef wrapped to avoid multiple inclusion
Each source (.cpp) file should be listed in the SOURCES variable of the project file, otherwise it will not be compiled
The header file should be listed in the HEADERS variable of the .pro file – without this moc will not preprocess the file
The Q_OBJECT macro must appear inside the class definition, so that moc will know to generate code for it.
Values & Objects
c++ types can be divided into two categories…

Value Types – simple and occupy contiguous memory space, and can be copied or compared quickly
Object Types – typically more complicated and maintain some sort of identity, copying is rare and expensive.
tr() and Internalization
For writing programs that can be translated into many languages, QT Linguist and QT translation tools have already solved the problem of how to organize and where to put the translated strings.

To prepare code for translation we use the tr() function.

tr() serves two purposes…

It makes it possible for Qt’s lupdate tool to extract all of the translated string literals
If a translation is available, and the language has been selected, the strings will actually be translated into the selected language at runtime.