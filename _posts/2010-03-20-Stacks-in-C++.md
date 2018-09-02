---
layout: post
title: Stacks in C++
tags: 
category: General
---
So some more basics… One of the things you will be taught at any college after conquering arrays is different derivatives of collections. Stack is one of the simplest of those and very useful…

A stack is a LIFO (last in first out) data structure and has at least two basic method calls – push & pop. Push, “pushes” an item on the top of the stack. Pop, removes the top most item off the stack.

Because all elements on a stack are of the same type, one can use an array to implement a stack or a linked list.

With the array based approach, the first element in a stack would be the first element in the array, the second on the stack would be the second on the array, etc.

One limitation with an array implementation of a stack is that unless the array is dynamic, one would have to have a preset max stack size (based on the bounds of the array).

Linked lists is another approach that gets past this boundary by allowing you to dynamically grow or shrink a collection of data.

Stacks have many applications… a typical computer science example would be Postfix Expression Calculator, where the LIFO principle is maintained.