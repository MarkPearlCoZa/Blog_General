---
layout: post
title: Programming Contemporary Concepts UNISA studies begin – Chap 1
tags: 
category: University
---
Today I thought I would start the second semester of my UNISA studies, and after some psyching up I eventually pulled out the study guidelines and made a study schedule. By chance my Contemporary Concepts course is due first, thus this post.

Any ramblings and blog posts associated with the UNISA COS 2144 tag should be considered study notes for my lectures...

Chapter 1

Chapter 1 consists of 14 subsections, 9 of which are language applicable, and the other 5 possibly ramblings to fill material. The 9 sections that seemed to be worth reading covered the following…

Input & Output
Identifiers, Types and Literals
C++ Simple Types
C++ Standard Library Strings
Streams
The Keyword const
Pointers & Memory Access
const* and *const
Reference Variables
These are fairly basic principles, but to refresh my memory of the basics covered in the book on C++ (which I typically conveniently forget as soon as is possible) I have outlined them below…

Input & Output

#include <iostream> allows us to make basic predefined input & output stream objects which are

cin – standard input
cout – standard output
cerr – standard error
I haven’t used cerr before but it describes it as another output stream to the console screen that flushes more often and is normally used for error messages.

Since I have been looking into the forward pipe in F#, I did find it interesting that the syntax for cout/cin uses a shortcut.

e.g.

cout << “Test Output “;

is really shortened code for

cout.operator<<(“Test Output”);

Identifiers, Types, and Literals

Identifiers

Identifiers are names that are used in C++ programs for functions, parameters, variables, constants classes, and types.
An identifier cannot be a reserved keyword.
There is no specified limit to the length of the identifier (but certain C++ implementations restrict it to 31 characters)
Literals

A literal is a constant value that appears somewhere in a program.
Every literal has a type
e.g. of a literal – 5 would be a literal meaning an integer literal.
Types

There are several simple types supported in C++, they include Boolean, Character, Integer, Floats & Pointers
There is also a type that signifies the absence of type information called “void”.
There is a special operator called the sizeof() that returns the number of chars that a given expression requires for storage.
All pointers are the same size using the sizeof() method regardless of their type.
C++ Standard Library Strings

STL strings have many disadvantages when compared to QStrings (quoted by the author), but are easy to use and have a similar public interface that includes many functions to construct and modify strings.

Stream

Streams are object used for reading and writing. The STL defines <iostream>, while Qt defines <QTextStream> for equivalent functionality.

Flush and endl are additional manipulators that can be added to an output stream to change the way the output data is formatted, or to an input stream to change the way the input data is interpreted.

Areas where streams are useful include reading from or writing to…

files
network connections
strings
The Keyword const

Declaring an entity to be “const” tells the compiler to make it “read only”.

Compilers can take advantage of an object being readonly.

Pointers & Memory Access

C++ distinguishes itself from many other programming languages by permitting direct access to memory through the use of pointers.

A variable is an object with a name recognized by the compiler.
A object is a chunk of memory that can hold data (in a very general simplified sense).
The unary “&” operator also known as the address of operator when applied to any object returns the memory address of that object.
An object that holds the memory address of another object is called a pointer.
A pointer to a simple type uses exactly the same memory as a pointer to a large data type.
The unary “*” operator, also known as the dereference operator, when applied to a non-null pointer returns the object at the address stored by the pointer.
The operators new and delete allow dynamic allocation of memory at runtime.

The new operator allocates storage from the memory heap and returns a pointer to the newly allocated object.
The delete operator releases dynamically allocated memory and returns it to the memory heap.
const* and *const

?

Reference Variables

A reference provides a mechanism for assigning an alternative name to an lvalue. References are useful for avoiding copies when a copy is costly or unnecessary, for example, when passing a very large object as a parameter to a function.

The ampersand “&” following the type indicates that the identifier is a reference.

e.g.

int a = 10;

int& ra = a;
