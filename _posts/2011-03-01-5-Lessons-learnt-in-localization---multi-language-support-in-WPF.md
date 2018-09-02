---
layout: post
title: 5 Lessons learnt in localization - multi language support in WPF
tags: 
category: General
---
For the last few months I have been secretly working away at the second version of an application that we initially released a few years ago. It’s called MaxCut and it is a free panel/cut optimizer for the woodwork, glass and metal industry. One of the motivations for writing MaxCut was to get an end to end experience in developing an application for general consumption.

From the early days of v1 of MaxCut I would get the odd email thanking me for the software and then listing a few suggestions on how to improve it. Two of the most dominant suggestions that we received were…

Support for imperial measurements (the original program only supported the metric system)
Multi language support (we had someone who volunteered to translate the program into Japanese for us).
I am not going to dive into the Imperial to Metric support in todays blog post, but I would like to cover a few brief lessons we learned in adding support for multi-language functionality in the software. I have sectioned them below under different lessons.

Lesson 1 – Build multi-language support in from the start

So the first lesson I learnt was if you know you are going to do multi language support – build it in from the very beginning! One of the power points of WPF/Silverlight is data binding in XAML and so while it wasn’t to painful to retro fit multi language support into the programing, it was still time consuming and a bit tedious to go through mounds and mounds of views and would have been a minor job to have implemented this while the form was being designed.

Lesson 2 – Accommodate for varying word lengths using Grids

The next lesson was a little harder to learn and was learnt a bit further down the road in the development cycle. We developed everything in English, assuming that other languages would have similar character length words for equivalent meanings… don’t!. A word that is short in your language may be of varying character lengths in other languages. Some language like Dutch and German allow for concatenation of nouns which has the potential to create really long words.

We picked up a few places where our views had been structured incorrectly so that if a word was to long it would get clipped off or cut out. To get around this we began using the WPF grid extensively with column widths that would automatically expand if they needed to. Generally speaking the grid replacement got round this hurdle, and if in future you have a choice between a stack panel or a grid – think twice before going for the easier option… often the grid will be a bit more work to setup, but will be more flexible.

Lesson 3 – Separate the separators

Our initial run through moving the words to a resource dictionary led us to make what I thought was one potential mistake. If we had a label like the following…

“length : “

In the resource dictionary we put it as a single entry. This is fine until you start using a word more than once. For instance in our scenario we used the word “length’ frequently. with different variations of the word with grammar and separators included in the resource we ended up having what I would consider a bloated dictionary. When we removed the separators from the words and put them as their own resources we saw a dramatic reduction in dictionary size… so something that looked like this…

“length : “

“length. “

“length?”

Was reduced to…

“length”

“:”

“?”

“.”

While this may not seem like a reduction at first glance, consider that the separators “:?.” are used everywhere and suddenly you see a real reduction in bloat.

Lesson 4 – Centralize the Language Dictionary

This lesson was learnt at the very end of the project after we had already had a release candidate out in the wild. Because our translations would be done on a volunteer basis and remotely, we wanted it to be really simple for someone to translate our program into another language. As a common design practice we had tiered the application so that we had a business logic layer, a ui layer, etc. The problem was in several of these layers we had resource files specific for that layer. What this resulted in was us having multiple resource files that we would need to send to our translators. To add to our problems, some of the wordings were duplicated in different resource files, which would result in additional frustration from our translators as they felt they were duplicating work. Eventually the workaround was to make a separate project in VS2010 with just the language translations. We then exposed the dictionary as public within this project and made it as a reference to the other projects within the solution. This solved out problem as now we had a central dictionary and could remove any duplication's.

Lesson 5 – Make a dummy translation file to test that you haven’t missed anything

The final lesson learnt about multi language support in WPF was when checking if you had forgotten to translate anything in the inline code, make a test resource file with dummy data. Ideally you want the data for each word to be identical. In our instance we made one which had all the resource key values pointing to a value of test. This allowed us point the language file to our test resource file and very quickly browse through the program and see if we had missed any linking.

The alternative to this approach is to have two language files and swap between the two while running the program to make sure that you haven’t missed anything, but the downside of dual language file approach is that it is much a lot harder spotting a mistake if everything is different – almost like playing Where’s Wally / Waldo. It is much easier spotting variance in uniformity – meaning when you put the “test’ keyword for everything, anything that didn’t say “test” stuck out like a sore thumb.

So these are my top five lessons learnt on implementing multi language support in WPF. Feel free to make any suggestions in the comments section if you feel maybe something is more important than one of these or if I got it wrong!