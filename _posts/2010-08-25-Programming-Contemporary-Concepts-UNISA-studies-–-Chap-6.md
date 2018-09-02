---
layout: post
title: Programming Contemporary Concepts UNISA studies – Chap 6
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA COS 2144 tag should be considered study notes for my lectures...

This chapter introduces the concepts and shows some examples of how to define inheritance relationships between c++ classes, overriding methods, the vritual keyword, and simple examples show how polymorphism work.

Questions for this Section
What is inheritance for?
Explain polymorphism. What is it? How can you use it?
Explain the difference between dynamic binding and static binding?
How do you override a base class method?
What is a pure virtual function? What is it used for?
What is an abstract class? What is it used for? What can you do with a concrete class that you cannot do with an abstract class?
What does it mean for a base class function to be hidden? What can cause this to happen?
Which member functions cannot be inherited from the base class? Explain why.
Simple Derivation
Inheritance is a way of organizing classes. It allows different classes to share common code. (see wiki)

To employ inheritance, we place the common features of similar classes together in a base class and then derive other classes from it.

Each derived class inherits all the members of the base class and can override or extend each base class function as needed.

Refactoring is a process of improving the design of software without changing its underlying behaviour. One step of refactoring simply involves replacing similar code with calls to library functions or base class methods.

Member Initialization for Base Classes

When a child class is instantiated, the base class constructor will also be called. It is important to note the following…

Base class constructor gets initialized first, before the initialization of the derived class members
If you do not specify how the base class is initialized, the default constructor will be called
Derivation with Polymorphism
Polymorphism is a powerful feature of object oriented programming. (See Wiki)

By simply adding a keyword “virtual” to one of the member functions of a class, we have created a polymorphic type.

With polymorphism, indirect calls (via pointers & references) to methods are resolved at runtime. This is sometimes called dynamic, or late run-time binding.

Derivation from an Abstract Base Class
An abstract base class is used to encapsulate common features of concrete classes. An abstract class cannot be instantiated.

A concrete class represents a particular kind of entity, something that exists and can be instantiated.

Classes are groupings and so it can be useful to sometimes organize classes or group classes using an abstract class.

Features of a class that tell the compiler to enforce this rule are:

There is at least one pure virtual function.
There are no public constructors
A pure virtual function has the following declaration syntax…

virtual returnType functionName(parameterList)=0

For example the following class is an abstract class in c++…

class Shape {
    public:
        virtual double area() = 0;
        virtual QString getName() = 0;
        virtual QString getDimension() = 0;
        virtual ~Shape() {}
};
 

To illustrate polymorphism and inheritance from a base class look at the code snippet below..

#include <QtCore/QCoreApplication>
#include <QDebug>

class Shape {
    public:
        virtual double area() = 0;
        virtual QString getName() = 0;
        virtual QString getDimension() = 0;
        virtual ~Shape() {}
};

class Rectangle : public Shape {
public:
    Rectangle(double h, double w) : m_Height(h), m_Width(w) {}        

    QString getName()
    {
        return "Rectangle";
    }    
    
protected:
    double m_Height, m_Width;
};

void showName(Shape* shp)
{
    qDebug() << shp->getName();
}

int main(int argc, char *argv[])
{
    QCoreApplication a(argc, argv);    
    Rectangle rectangle(1.1,1.1);    
    showNameAndArea(&rectangle);    
    return a.exec();
}
The method call showName was polymorphic as it was expecting a Shape, and since Rectangle inherited from the shape class it was able to be passed through and be evaluated correctly.

Inheritance Design
Using UML modelling as a tool for designing inheritance and classes makes it easier to evaluate different designs without having to actually implement code.

Overloading, Hiding, and Overriding
Overloading – when two or more versions of a function “foo” exist in the same scope, we say that foo has been overloaded.

Overriding – when a virtual function from the base class also exists in the derived class, with the same signature, we say that the derived version overrides the base class version.

Hiding – a member function of a derived class with the same name as a function in the base class hides all functions in the base class with that name.

Constructors, Destructors, and Copy Assignment Operators
Three special kind of member functions are never inherited…

Copy Constructors
Copy assignment operators
Destructors
Constructors

For a class that inherits from another, the base class constructor must be called as part of its initialization process. The derived constructor may specify which base class constructor is called in its initialization list.

A class with no constructors is automatically given a compiler-generated default constructor that calls the default constructor for each of its base classes. If a class has some constructors but no default constructor, then it has no default initialization. In this case, any derived class constructor must make specific base class constructor call in its initialization list.

Order of Initialization

Initialization proceeds in the following order:

Base classes first, in the order in which they are listed in the class Head of the derived class
Data members, in declaration order
Copy Assignment Operators

A copy assignment operator will be generated automatically by the compiler for each class that does not have one explicitly defined for it. It calls its base class operator== and then performs member wise assignments in declaration order.

Other member function operators are inherited the same way as normal member functions.

Copy Constructors

Like the copy assignment operator, the copy constructor gets generated automatically for classes that do not have one defined. The compiler-generated copy constructor will carry out member-by-member initialization, much as one would expect.

Destructors

Destructors are not inherited. The compiler will generate a destructor if we do not define one explicitly. Base class destructors are automatically called on all derived objects regardless of whether a destructor is defined in the class. Members and base-class parts are destroyed in the reverse order of initialization.