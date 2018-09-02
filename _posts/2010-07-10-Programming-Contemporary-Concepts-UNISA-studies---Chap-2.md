---
layout: post
title: Programming Contemporary Concepts UNISA studies - Chap 2
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA COS 2144 tag should be considered study notes for my lectures...

Chapter 2

This chapter covered an

Introduction to classes and objects, and
How member functions operate on objects.
UML is introduced.
Static and const members are explained.
Constructors, destructors, copy operations, and
Friends are discussed.
Class Definitions

Section 2.1 & 2.2 briefly covered structs and classes. While these are age old… in case I ever forget.

A struct takes the format of

struct Fraction 
    {
        int number, denom;
        string description;
    };
 

The syntax for a class is very similar to a struct however classes can contain

data members
member functions
access specifiers
A class takes the following format

class Person 
{
    members
};

The section also speaks of instances or objects which are in essence variables of a class type (very basic stuff). When asked what the state of an object is, one is wanting to know the values of the data members of the object.

Classes in c++ are typically broken up into two separate files,

A header file which contains the definition of a class (.h extension)
A implementation file which contains the actual code (.cpp extension)
Something I never quite understood till recent years was the #include pre-processor directive.This is important to “chain” a program together however one would not want the header file to be included more than once and so the #ifndef - #define …. #endif preprocessor macros are used to prevent this.

Also, something that I had always done, but had never heard the terminology for before was the scope resolution operator.

A scope resolution operator is required to indicate the scope of a method when it is outside the definition file. e.g. if you were going to define a method in a cpp file, you would need to declare the scope of the method i.e.

Classname::Method…

The scope resolution operator tells the compiler that the scope of the class extends beyond the class definition and includes the code between the :: and the closing brace of the function definition.

The chapter then goes on to talk about scope, and how a class method has a class scope etc.

Member Access Specifies

Member access specifies specify what level of access each member is exposed to… they include…

public – accessed from anywhere in the program
protected – can be accessed inside the definition of a member function of its own class, or a member function of a derived class
private – can be accessed only by member functions of its own class
The chapter also has an interesting note on Accessibility vs Visibility. It explains that just because something may be visible does not mean it is accessible. The accessibility of a method is purely based on the member access specifier of the method.

a keyword also important to remember is block scope – which is the scope between two braces. For instance, the block scope of a variables within a method is between the open brace of the method and the closing brace.

Encapsulation

This section is still very basic but goes on to speak about encapsulation. Funny enough I have yet to find a memorable definition in a CS textbook on what encapsulation is.

I quite like the Wikipedia definition where immediately they give the other less scientific term – “information hiding”. Read the Wikipedia if you want a proper explanation on what encapsulation is.

Benefits of encapsulation include more robust code, reuse of common naming constructs on methods & variables without getting conflicts, etc.

Introduction to UML & UML Relationships

UML stands for Unified Modelling Language – it is a graphical representation of objects, and the interaction of objects with other objects, the system & the users.

It’s important to note that UML is not just class diagrams, although that is probably where they are most useful and most readily used in real world programming. UML is also very useful when one wants to see the relationship between various classes.

Friends of Classes

This is something I have never used before so it was interesting to see the mention of the friend mechanism. Basically the friend mechanism allows one to break accessibility rules of a class. i.e it would be possible to allows non-member functions access to private data???

Is this a good thing? Okay, so I am no expert, but I’m not to sure that I would want something that I have explicitly made private suddenly be able to be accessed outside of its scope?

So to see examples of the friend modifier go to the following post and this one on stack overflow.

I quite liked the example of S/O so I have posted a code snippet below…

class Child
{
  friend class Mother;
  
  public: 
  string name( void );
  
  protected:

  void setName( string newName );
};
 

In the above code snippet only the Child and the Mother can change the name…

Constructors

Some interesting things..

A constructor is sometimes abbreviated as ctor – I found this interesting as I was looking at reflector and saw some ctor names – now I know what they mean!
Constructors do not returns anything and do not have have return types.
If no constructor is specified in a class definition the compiler will provide an empty one.
Sub Objects

An object can contain another object is called a sub object. I am not quite sure what the author was trying to accomplish with this section?

Destructors

Sometimes abbreviated as a dtor
Automates clean-up actions just before an object is destroyed.
A destructor cannot be overloaded
If no destructor is defined, the compiler will create an empty one on compilation.
An interesting note was when is an object destroyed?

When a local object goes out of scope
When a object created by the new operator is specifically destroyed by the use of the operator delete
Just before the program terminates, all objects with static storage are destroyed.
The Keyword static

The keyword static can be applied to a variable declaration to give the variable static storage class.

A local static variable is created only once and is destroyed when the program terminates. A class works on a similar basis/

Something that I did fin interesting was that static class members are preferable to global variables because they do not pollute the global namespace. I have always wondered what the difference was between the two, since I was always told global variables were bad! now I know why!

Block-Scope static are statics that are defined inside a function or block of code and are initialized when they are executed for the first time. Static initialization is also fairly interesting.

A static object that is not defined in a block or function is initialized when its corresponding object module is loaded for the first time. Usually this is at program startup. The order in which modules are loaded is implementation specific.
Copy Constructors & Assignment Operators.

A copy constructor is a constructor that has a prototype like

ClassName(const ClassName & x);

The purpose of a copy constructor is to create an object that is an exact copy of an existing object of the same class.

An assignment operator for a class overload the symbol = and gives it a meaning that is specific to the class. For instance two instances of the class “Person” called PersonA & PersonB might have special requirements for them to be equivalent

i.e. if (PersonA == PersonB) …

Conversions

A constructor that can be calls with a single argument (of a different type) is a conversion constructor because it identifies a conversion from the argument type to the constructor’s class.

const Member Functions

The const keyword has a special meaning when applied to a class member function. It guarantees that the function will not change the state of the host object.

I quite liked this question posted on S/O regarding the const member function.