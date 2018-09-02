---
layout: post
title: Programming Contemporary Concepts UNISA studies – Chap 3
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA COS 2144 tag should be considered study notes for my lectures...

This chapter introduces the QT development environment, including the compiler, linker, make, and qmake. It includes a first example using Qt, and introduces iterators and lists.

The chapter itself was fairly short – it mainly covered a basic equivalent to “hello world” and how to build projects.

One section that I did find interesting was the section on the #include

#Includes – what they do…

3 commonly used ways to #include a library header file…

#include <headerfile>
#include “headerfile”
#include “path/to/headerfile”
The <> indicate that the preprocessor must look sequentially in the directories listed in the include path for the file.

A quoted filename indicates that the preprocessor should look for the headerfile in the including file’s directory first.

The path information can be absolute or relative.

If multiple versions of the file exists, the search will stop as soon as the first occurrence of the file has been found..

Example Project

The chapter also covered a really basic project… I have listed the code below – pretty simple stuff, although still a few hoops to climb through…

#include <QtCore/QCoreApplication>
#include <QApplication>
#include <QString>
#include <QLabel>
#include <QWidget>
#include <QDebug>
#include <QTextStream>

int main(int argc, char *argv[])
{
    QApplication myapp(argc, argv);
    QWidget wid;
    qDebug() << "hello";
    QString message;
    QTextStream buf(&message);
    
    buf << "test widget";
    qDebug() << message;
    
    QLabel label(message);
    label.show();
    return myapp.exec();
}

Style Guidelines & Naming Conventions

There is a specific QT programming style… the following guidelines were given…

Class names begin with a capital letter: class Customer
Function names begin with a lowercase letter.
Periods/Full stops, underscores, dashes & funny characters should be avoided whenever possible.
Multi-word names have subsequent words capitalized: ThisIsAMultiWordName.
Constants should be in CAPS.
Each class name should be a noun or noun phrase
Each function name should be a verb or verb phrase
Each bool variable name should produce a reasonable approximation of a sentence when used in an if(() statement – e.g. bool isQualifiedl
for data members we use a common prefix : m_Color, m_Width
For each attribute we have naming conventions for their corresponding getters/setters e.g color() or getColor(), isChecked() or isValid
