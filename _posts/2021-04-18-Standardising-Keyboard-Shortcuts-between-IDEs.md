---
layout: post
title: Standardising Keyboard Shortcuts between IDEs
tags: 
category: General
---

I'm a big believer in leveraging keyboard shortcuts when manipulating text. A big aha moment in my computer career was when I discovered the power of Vim. I could now navigate text without having to rely on my mouse or slow up/down page up/oage down keys. When I began to leverage Vim emulation in the IDE, coding went from a disjointed context switch between keyboard/mouse to a fluent experience where text entry/navigation at the speed of thought.

As I've progressed, and as our industry has progressed, the need/desire to work in different operating systems and IDE's has increased. While writing this I have two machines on my desk, a Mac and a Windows machine. On each machine I have multiple IDE's - Visual Studio, Rider, Ruby Mine, VS Code, etc. The challenge with this remebering the keyboard shortcuts! Going to a method implementation in Visual Studio is a totally different keyboard sequence to doing the same thing in Rider. As soon as you hit more than 2-3 enviornments things begin to get fuzzy.

Taking a step back, from a keybaord shortcut lens, as an ideal I want the same keyboard shortcuts to do the same things in all IDEs!  

Over the years I've progressed on my efforts to standardise this. While I am not at the ideal state, I've reduced the cognitive load significantly. The secret... a hardware reprogrammable keyboard that can leverage macros. Let me explain...

I've owned a UHK for several years now. UHK's allow you to record a key sequence and save it as a macro. They also allow you to assign a macro to a specific key. With these two ingrediants I'm able to standardise my keyboard shortcuts across IDE's so that regardless of IDE I'm in I can use the same key to trigger the same behaviour.

For example, in Visual Studio I've programmed my FN+D key to take me to the implementation of a method. The same key sequence (FN+D) does this across Ruby Mine, Rider, VS Code and so on.

<img class="img-responsive" alt="UHK Rider Windows Base Mapping" src="{{ site.url }}/assets/images/Standardise-Keyboard-Shortcuts-Base.png">
<img class="img-responsive" alt="UHK Rider Windows Base Mapping" src="{{ site.url }}/assets/images/Standardise-Keyboard-Shortcuts-Navigation.png">
<img class="img-responsive" alt="UHK Rider Windows Base Mapping" src="{{ site.url }}/assets/images/Standardise-Keyboard-Shortcuts-Refactoring.png">
<img class="img-responsive" alt="UHK Rider Windows Base Mapping" src="{{ site.url }}/assets/images/Standardise-Keyboard-Shortcuts-Tests.png">

