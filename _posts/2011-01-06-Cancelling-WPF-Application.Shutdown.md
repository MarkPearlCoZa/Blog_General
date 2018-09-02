---
layout: post
title: Cancelling WPF Application.Shutdown
tags: 
category: General
---
Today I spent the better part of an hour trying to figure out what I had had done wrong. I had an application that when the user click’s “exit”, it should prompt if they want to save the last unsaved file, or cancel the exit. If the select cancel it should not exit the application. Everything seemed fine in my code, all I was doing was calling

Application.Current.Shutdown();

And then capturing the Closing event and setting cancel to true.. (see SO question here)

Long story short, If should not have been calling Application.Current.Shutdown() but rather Application.Current.MainWindow.Close().

grrrr… <I must read documentation properly>