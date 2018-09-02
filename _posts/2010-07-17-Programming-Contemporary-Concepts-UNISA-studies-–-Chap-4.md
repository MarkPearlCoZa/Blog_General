---
layout: post
title: Programming Contemporary Concepts UNISA studies – Chap 4
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA COS 2144 tag should be considered study notes for my lectures...

Lists – whenever possible we use lists in favour of arrays. This chapter explains ways of grouping things together in lists and how to iterate through them.

Introduction to Containers

There are many occasions when it is necessary to deal with collections of things. The beginners approach is to use arrays, however in c++ arrays have several negative side effects that make them not to desirable. These include…

Array subscripts are not checked to make sure that they are not out of range. A programmer using an array has a responsibility to write extra code to do the range checking.
Arrays are either fixed in size or they must use dynamic memory from the heap. This requires the programmer to manually release the memory on the heap when the array is no longer needed.
Inserting, appending or or pre-pending elements to an array can be expensive.
Instead of arrays, the STL & QT provide access to lists that resize themselves when needed and also perform range checking. These are generic containers meaning that they can accept templates of the data type that they are to store.

Iterators

Anytime you have a container of things, you will need some way to iterate through the collection. An iterator is an object that provides indirect access to each element in a container. It is specifically designed to use in a loop.

In the chapter there were specific examples of the QList<QString> which may be worth noting however I will not include them in this summary

Relationships

This section of the book randomly jumps to UML diagrams showing a 1-1 relationship and a 1-many relationship.

It also speaks of composite relationships and aggregate relationships.

Composite relationships indicate that one object owns the other object, meaning if an object is a composite, it should not exist without the primary object.

Aggregate relationships indicate that the lifetimes of the objects on either end are the relationship are not related to each other and could independently be created or destroyed.
