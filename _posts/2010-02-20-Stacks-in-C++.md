---
layout: post
title: Stacks in C++
tags: 
category: General
---
A stack is a LIFO (last in first out) data structure. A stack has at least two basic method calls – push & pop. Push, “pushes” an item on the top of the stack. Pop, removes the top most item off the stack.

Implementation of Stacks as Arrays

Because all elements on a stack are of the same type, one can use an array to implement a stack. The first element in a stack would be the first element in the array, the second on the stack would be the second on the array, etc.

Linked Implementation of Stacks

One limitation with an array implementation of a stack is that unless the array is dynamic, one would have to have a preset max stack size (based on the bounds of the array).

We saw with linked lists, that pointers allow us to dynamically grow or shrink a collection of data, and this principle can be applied to implement a dynamic stack size.

Application of Stacks

Stacks have many applications… a typical computer science example would be Postfix Expression Calculator, where the LIFO principle is maintained.