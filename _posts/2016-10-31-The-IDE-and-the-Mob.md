---
layout: post
title: Preparing the Mob Development Environment 
tags: Mobbing
category: Unpublished
---

Before you start your first mob session, spend time setting up the mob development environment (MDE). Having an MDE that works well reduces the reluctance many people have of rotating into the typist role, which in return improves the overall experience a new mob has. 

In preparing the MDE there are a few things to consider:  

1. What editor/IDE to use  
2. Keyboard shorcut mappings
3. On screen code navigation  
4. Version control concerns
5. Timer  

## What editor/IDE to use?

*For the sake of being succint, when you see editor, replace it will integrated development environment where appropriate.*

For many teams the discussion on what editor to use as a mob will be a quick. Many teams use the same editor across the individuals in the team - if you are in this situation, this will be the editor you use as the mob.

For some teams, people in the team use different editors when working on their own. Bringing them together as a mob raises the question - what editor do you use when mob programming? If you are in this situation, I recommend you use the editor that the majority of the mob uses when working on their own. If you go this route be mindful of the individuals in the mob that are not using their editor of choice. Aknowledge that they may be under some initial pain.

As a mob, avoid learning a new editor as an initial mob activity unless there is a real need to do so. When a new mob starts there is always some social storming. After a few days of mob programming the storming subsides and momentum starts to grow. Learning a new editor, while trying to also solve a problem can cause unecessary confusion and frustration in the mob - both things you want to minimize when starting out.

## Keyboard Shortcut Mappings

individuals may have worked on the same solution in the past, you will discover your needs in an IDE as a mob are different from you you have very different nuances development environments, geared towards their preferred way of working.

### Identify individual keyboard shortcut prefereces 

Start off by identifying the various shortcut mappings individuals in your mob currently us. Don't assume that because everyone in the mob uses the same editor, you will all have the same keyboard shortcuts! Some editors provide multiple keyboard shortcut flavours. 

For instance, I have spent a large part of my professional career using Visual Studio with Resharper as a plugin. Resharper gives at least two options for key mappings - the classic Visual Studio key mappings as well as IntelliJ key mappings. 

### See if you can quick switch mappings

Find out if in your current editor it is possible to quickly switch between the various keyboard mappings that everyone in the group uses (by quickly I mean anything under 2 seconds, anything over that is going to frustrate you). Some editors allow quick switching, in which case you will probably not feel any pain with keyboard shortcuts.

### If you can't switch quickly, what do you do?

If your editor does not allow for switching quickly between keyboard shortcuts you are going to need decide on a mob standard. Picking the keyboard mapping that is easiest for the entire mob to adopt upfront is going to reduce the pain you feel.

### A word on vi and vim

I'm a vim fan. I've been using it for years. It has significantly changed the speed at which I can write and morph code. If you are a vi or vim fan, but some people in your mob are not, I would recommend for initial mob sessions to not try and teach them how to use this editor while mob programming. 

Being put in front of a group of co-workers and not being able to even type a single letter can be frustrating, embarassing and alienating. Rather pick a editor that everyone can be productive in from day one. With time, as your mob settles and gets comfortable with each other, you can look at showing them the light of vim. For the sake of the mob, you will have to go slower initially.

For emacs users, best you learn a proper editor like vim :-)

## Turn on absolute line numbers

When mob programming have absolute line numbers tuned on. Aboslute line numbers speed up 

### Absolute and relative line numbers are not the same thing

Absolute and relative line numbers are not the same thing. Absolute line numbers are absolute regardless of where the cursor is positioned. Relative line numbers change as you move the cursor up or down. 

Because there is still latency between the typist and the rest of the mob, telling the typist to go down 5 lines (relative navigation) may not work. They may have moved the cursor one or two lines down before processing your instruction, leading them to still being off by a few lines.

Instead, get used to working with absolute line numbers. Saying, move to line 45 is less error prone than move down 5 lines.

## Version Control

## Timer
