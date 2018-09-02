---
layout: post
title: Attempts at TDD–Testing Private Methods
tags: 
category: General
---
I have recently being trying to implement TDD as a practice in writing code. Up to now I buy into many of the benefits of TDD but it is one thing agreeing that a practice is good and a totally different thing implementing the practice.

The approach I have taken was relatively simple,

Write a test to exercise the functionality you want in a method
Run test – it will fail
Implement method
Run test – it should pass
Repeat first step
Seems simple enough…  when it came to implementing the process a concern arose. I had written some tests for methods that ultimately I did not want to be publicly exposed. Most of the literature I have read up to now says you should only be testing public methods for unit tests – but during the development process I found these methods fairly tricky to write and so writing tests for them had helped in the development process. Now that I had made the methods private it seemed a step backward to delete the tests. With this concern in mind I emailed one of my friends who has more experience with TDD and this was his response…

My feeling is that as long as you are following SRP at a class level, test what is public. If your class has multiple responsibilities, then only testing public functions is going to leave things untested.


 

There is the option of marking methods an internal, then using the InternalsVisibleTo attribute in your AssemblyConfig to expose your internal methods to your test assembly. This is one option, but if  you are doing the SRP thing, then you probably don’t need it.


 

With your example, I would see the fact that you are trying to test some private methods as a potential code smell – could things be split into smaller classes? Of course sometimes the tests add no value on their own and do get thrown away as a normal course of doing TDD.

 

Even before I had received his response I had made an attempt to refactor my code and realized that the methods that I was testing privately would be better suited to being handled in a separate class. After moving this methods I was much happier with the structure of the classes and I found some reuse benefits – this just validated the fact that in this instance the tests for private methods were a code smell that I had broken the SRP.

Does anyone have additional/alternative views?