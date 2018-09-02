---
layout: post
title: Formal Languages, Inductive Proofs and Regular Expressions
tags: 
category: University
---
So I am slogging away at my UNISA stuff. I have just finished doing the initial once non stop read through the first 11 chapters of my COS 201 Textbook - “Introduction to Computer Theory 2nd Edition” by Daniel Cohen. It has been an interesting couple of days, with familiar concepts coming up as well as some new territory. In this posting I am going to cover the first couple of chapters of the book.

Let start with Formal Languages…

What exactly is a formal language? Pretty much a no duh question for me but still a good one to ask – a formal language is a language that is defined in a precise mathematical way.

Does that mean that the English language is a formal language? I would say no – and my main motivation for this is that one can have an English sentence that is correct grammatically that is also ambiguous.

For example the ambiguous sentence: "I once shot an elephant in my pyjamas.”

For this and possibly many other reasons that I am unaware of, English is termed a “Natural Language”.

So why the importance of formal languages in computer science? Again a no duh question in my mind… If we want computers to be effective and useful tools then we need them to be able to evaluate a series of commands in some form of language that when interpreted by the device no confusion will exist as to what we were requesting. Imagine the mayhem that would exist if a computer misinterpreted a command to print a document and instead decided to delete it.

So what is a Formal Language made up of…

For my study purposes a language is made up of a finite alphabet.

For a formal language to exist there needs to be a specification on the language that will describe whether a string of characters has membership in the language or not. There are two basic ways to do this:

By a “machine” that will recognize strings of the language (e.g. Finite Automata).
By a rule that describes how strings of a language can be formed (e.g. Regular Expressions).
When we use the phrase “string of characters”, we can also be referring to a “word”.

What is an Inductive Proof?

So I am not to far into my textbook and of course it starts referring to proofs and different types. I have had to go through several different approaches of proofs in the past, but I can never remember their formal names , so when I saw “inductive proof” I thought to myself – what the heck is that?

Google to the rescue…

An inductive proof is like a normal proof but it employs a neat trick which allows you to prove a statement about an arbitrary number n by first proving it is true when n is 1 and then assuming it is true for n=k and showing it is true for n=k+1.

The idea is that if you want to show that someone can climb to the nth floor of a fire escape, you need only show that you can climb the ladder up to the fire escape (n=1) and then show that you know how to climb the stairs from any level of the fire escape (n=k) to the next level (n=k+1).

Does this sound like a form of recursion?

No surprise then that in the same chapter they deal with recursive definitions. An example of a recursive definition for the language EVEN would the 3 rules below:

2 is in EVEN
If x is in EVEN then so is x+2
The only elements in the set EVEN are those that be produced by the rules above.
Nothing to exciting…

So if a definition for a language is done recursively, then it makes sense that the language can be proved using induction.

Regular Expressions

So I am wondering to myself what use is this all – in fact – I find this the biggest challenge to any university material is that it is quite hard to find the immediate practical applications of some theory in real life stuff. How great was my joy when I suddenly saw the word regular expression being introduced.

I had been introduced to regular expressions on Stack Overflow where I was trying to recognize if some text measurement put in by a user was in a valid form or not. For instance, the imperial system of measurement where you have feet and inches can be represented in so many different ways. I had eventually turned to regular expressions as an easy way to check if my parser could correctly parse the text or not and convert it to a normalize measurement.

So some rules about languages and regular expressions…

Any finite language can be represented by at least one if not more regular expressions
A regular expressions is almost a rule syntax for expressing how regular languages can be formed
regular expressions are cool
For a regular expression to be valid for a language it must be able to generate all the words in the language and no other words. This is important. It doesn’t help me if my regular expression parses 100% of my measurement texts but also lets one or two invalid texts to pass as well.

Okay, so this posting jumps around a bit – but introduces some very basic fundamentals for the subject which will be built on in later postings… Time to go and do some practical examples now…
