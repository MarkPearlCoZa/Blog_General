---
layout: post
title: Standardising Keyboard Shortcuts between IDEs
tags: 
category: General
---

I'm a big believer in leveraging keyboard shortcuts when manipulating text. A big aha moment in my computer career was when I discovered the power of Vim. Once I got the essence of VIM I could navigate text without having to rely on my mouse or slow up/down page up/oage down keys. Coding and text manipulation went from a disjointed slow context switch driven frustraion (keyboard/mouse switching) to a fluent seamless experience where text entry/navigation was at the speed of thought.

As I've progressed, and as our industry has progressed, the need/desire to work in different operating systems and IDE's has increased. While writing this I have two machines on my desk, a Mac and a Windows machine. On each machine I have multiple IDE's - Visual Studio, Rider, Ruby Mine, VS Code, etc. Each IDE has it's own default key sequence which makes it a challenge to remember the keyboard shortcuts! If you work in one primary OS and IDE things are simple, as soon as you go into 2 or more environments things begin to get fuzzy and frustrating. At some point you give up and revert back to using the mouse to navigate menus!  

Taking a step back, from a keyboard shortcut lens, as an ideal I want the same keyboard shortcuts to do the same things in all IDE's!  

Over the years I've progressed on my efforts to standardise this. While I am not at the ideal state, I've reduced the cognitive load significantly. The secret... getting the most you can from a hardware reprogrammable keyboard. Let me explain...

I own a [Ultimate Hacking Keyboard also known as a UHK](https://ultimatehackingkeyboard.com/). UHK's have three key features that allow me to standardise keyboard shortcuts across IDE's, they are:

1) Keymaps  
2) Layers  
3) Macros  

For each IDE/OS combination I have a separate keymap. That means I have a keymap for Rider on Mac, and a keymap for Rider on Windows.

Each keymap has several layers: Base, Mod, Fn, Mouse. Don't get put out by the names of these layers - you can use a layer for anything. For myself, I have three main groupings of shortcuts which correlate to a layer: Normal Keyboard (Base), Navigation (Mod), Refactoring (Fn) and Test/Debug (Mouse).

Each key on a layer can be assigned an action. There are a range of actions including:
* specific keypress sequence  
* layer change  
* keymap change   
* trigger a macro  

To standardise keys, I've created a macro for each behaviour I want to trigger in each IDE. Let's look at the Debug Step Over behaviour.

In Visual Studio (Windows), the key sequence for this is F10. In Rider (Windows) it's F8. In Rider (Mac) it is back to F10. On my UHK regardless of IDE I press the far bottom right key (Mouse) plus the key on the second row, 5 from the right (O key). The benefit of this is were I to go into a new IDE, all I have to do is make a new keymap, copy my existing macros and change the key sequence behind the macro - the actual key on my keyboard remains the same... reduced cognitive load!

To give you an idea of what a keymap looks like, I've put a copy of my current "Rider for Windows" keymap below:

<img class="img-responsive" alt="UHK Rider Windows Base Mapping" src="{{ site.url }}/assets/images/Standardise-Keyboard-Shortcuts-Base.png">
  
<img class="img-responsive" alt="UHK Rider Windows Base Mapping" src="{{ site.url }}/assets/images/Standardise-Keyboard-Shortcuts-Navigation.png">
  
<img class="img-responsive" alt="UHK Rider Windows Base Mapping" src="{{ site.url }}/assets/images/Standardise-Keyboard-Shortcuts-Refactoring.png">
  
<img class="img-responsive" alt="UHK Rider Windows Base Mapping" src="{{ site.url }}/assets/images/Standardise-Keyboard-Shortcuts-Tests.png">
  
