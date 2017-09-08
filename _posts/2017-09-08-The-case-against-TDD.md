---
layout: post
title: The case against TDD
tags: 
category: Media
---

Eric Smith joined 8th Light to do higher quality work. TDD has won, the debate is over.

Uncle Bob has gone on record pacing back and forth saying "You are unprofessional if you haven't written a single line using TDD"  

Unix largely doesn't use TDD to be developed.
In order to be a professional, you work on an unprofessional operating system, developed on a platform that wasn't used TDD

TDD has 3 claims it makes, today's talk is the case against TDD.

* Code with tests has minimal bugs  
* TDD makes us faster, faster feedback (working on good code, and clean code)  
* TDD leads to better design (promotes the minimal amount to do)  

# TDD Reduces Defects

If you look at a subset of the tests for something that does something you have a lot more test lines of code than actual code  
Assume writing tests reduced your bug defect by 75%
You are still introducing bugs, just potentially in tests code
The mess is in your tests

# TDD Makes us faster

Your most complicated code is in your unit tests, the tests get more complicated than the actual code  
The more abstract you make test codes, the harder it is to understand    
That's why we copy/paste tests when we write new tests  

We spend an enourmous amount of time debugging the build system  
Tests become a maintenance problem  
Unit tests add easily twice as much code  
TDD doesn't really make you run faster, because you have moved the time to maintaining the tests

# TDD makes better design

Better design = more testable  
This is a circle loop  
DHH spoke about TDD pain  
Bob Martin says the second guy pays for the abstraction
Writing tests often forces the abstraction (the tests become the second guy)  

# So was this all a waste?

One of the things that happened with TDD was that it came out of the dynamic paradigm, you don't have any types so you need something... tdd
Static types are free tests, we threw them away because we didn't want to type them  
You can't forget to write the type checked... you can forget to write the tests
What if all maintenance pain was gone?

Design by contract is older than TDD and a lot of the design principles were used in TDD
The basic jist of DoC is that every method has pre conditions and post conditions  
QuickCheck or property based testing are great options  
There is still a need for unit tests, in certain places  

There is a scientific test that said writing tests leads to being more productive... what does this tell us? It tells us that we are crap at evaluating our field

TDD != Craftmanship  
* Testable != Good  
* Prove your Assertions  
* Don't be jerks  
* Remember that everything is a tradeoff, even good ones  

TDD is actually a Fad  
Fad doesn't mean it is bad  
Sometimes fads get overdone  

