---
layout: post
title: Preparing the Mob Development Environment 
tags: Mobbing
category: General 
---

Before you start your first mob session, spend time setting up the mob development environment (MDE). Having an development environment that works well reduces the reluctance many people have of rotating into the typist role, which in return improves the overall experience a new mob has. 

In preparing the MDE there are a few things to consider:  

1. What editor/IDE to use  
2. Keyboard shortcut mappings
3. On screen code navigation  
4. Version control user account
5. Timer  

## What editor/IDE to use?

*For the sake of being succint, when you see editor, replace it will integrated development environment where appropriate.*

For many teams the discussion on what editor to use as a mob will be a quick. Many teams use the same editor across the individuals in the team - if you are in this situation, this will be the editor you use as the mob.

For some teams, people in the team use different editors when working on their own. Bringing them together as a mob raises the question - what editor do you use when mob programming? If you are in this situation, I recommend you use the editor that the majority of the mob uses when working on their own. If you do this, be mindful of the individuals in the mob that are not using their editor of choice. Acknowledge that they may be under some initial pain.

As a mob, avoid learning a new editor as an initial mob activity unless there is a real need to do so. When a new mob starts there is always some social storming. After a few days of mob programming the storming subsides and momentum starts to grow. Learning a new editor, while trying to also solve a problem can cause unnecessary confusion and frustration in the mob - both things you want to minimize when starting out.

### A word on vi and vim

I'm a vim fan. I've been using it for years. It has significantly changed the speed at which I can write and morph code. If you are a vi or vim fan, but some people in your mob are not, I would recommend for your first couple of mob sessions to avoid using this editor in the mob - the learning curve is just too steep. Rather, pick an editor that everyone can be productive in from day one. With time, as your mob settles, you can look at showing them the light of vim but for now, for the sake of the mob, you will have to go slower.

## Keyboard shortcut mappings

If you have members in your mob who have spent time committing keyboard shortcut mappings to memory, having a discussion on what shortcut mappings to use as a mob is important.

Start off by identifying the various shortcut mappings people in your mob currently use. Don't assume that because everyone in the mob used the same editor, you will all have the same keyboard shortcuts mappings! 

If everyone in your team uses the same mappings great! If however, you have different people in your mob using different keyboard shortcut mappings, you have a few options:  

- See if you can quick switch keyboard shortcut mappings in your editor
- Or standardize on a standard keyboard shortcut mapping when mob programming  

### Quick switch keyboard shortcut mappings

For some editors it is possible to quickly switch between the keyboard shortcut mappings (by quickly I mean anything under 2 seconds). If you are lucky enough that your editor supports this, this may be the best route to go to cater for the various shortcut needs of the people in your mob.

### If you can't switch quickly, what do you do?

If your editor does not allow for switching quickly between keyboard shortcut mappings you will need decide as a mob on a standard. Picking the keyboard mapping that is easiest for the entire mob to adopt upfront is going to reduce the pain you feel.

## On screen code navigation  

### Turn on absolute line numbers

When mob programming have absolute line numbers tuned on. Absolute line numbers speed up on screen code navigation.

### Absolute and relative line numbers are not the same thing

Absolute and relative line numbers are not the same thing. Absolute line numbers are absolute regardless of where the cursor is positioned. Relative line numbers change as you move the cursor up or down. 

Because there is latency between an instruction being given from the mob and the typist processing the instructions, telling the typist to go down 5 lines (relative navigation) does not work well. Often the typist has already moved the cursor before processing your instruction, leading them to still being off by a few lines.

Instead, get used to working with absolute line numbers. Saying, move to line 45 is less error prone than move down 5 lines.

## Version control user account

When mob programming, there is always the question of who do we check the code in as? Since the mob created the code, is it right to have a 'mob credential' that we commit the code against, or do we check it in as someone in the mob.

If it is easy for you to create a mob user account for your code commits, there are benefits of identifying what code was written as a group vs. individual. For instance, often the rules change for reviewing code when mob programming. If you are in a team that has a formal code review process, you may not see the need to formally review 'mob' code (since the review was done while the code was being written) but still see the need to formally review 'solo' code. Being able to easily identify mob code from solo code is beneficial in this case.

Be careful though, don't get caught up in too many discussions before proving mob programming as a practice your team will stick with. If it looks like there will be a lot of red tape, commit the code as one of the people in the mob and follow your normal review process. If the code was written well, it will fly through the review stage. Once mob programming becomes a permanent thing in your team you can re-look at differentiating the workflows and getting a mob version control credential.

## Timer

For new teams, having a visible mob session timer is important. It makes it clear when a mob should rotate the typist role and can help encourage flow. There are various timers you can use, from a cell phones to on screen timers. I have found the best results with an on screen timer that is visible to the mob at all times. This often helps the mob avoid discussions getting too 'deep', there is nothing like seeing a clock ticking down to help you get to the point.

