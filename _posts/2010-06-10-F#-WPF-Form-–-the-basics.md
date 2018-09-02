---
layout: post
title: F# WPF Form – the basics
tags: 
category: General
---
I was listening to Dot Net Rocks show #560 about F# and during the podcast Richard Campbell brought up a good point with regards to F# and a GUI. In essence what I understood his point to be was that until one could write an end to end application in F#, it would be a hard sell to developers to take it on. In part I agree with him, while I am beginning to really enjoy learning F#, I can’t but help feel that I would be a lot further into the language if I could do my Windows Forms like I do in C# or VB.NET for the simple reason that in “playing” applications I spend the majority of the time in the UI layer…

So I have been keeping my eye out for some examples of creating a WPF form in a F# project and came across Tim’s F# Twitter Stream Sample, which had exactly this…. of course he actually had a bit more than a basic form… but it was enough for me to scrap the insides and glean what I needed.

So today I am going to make just the very basic WPF form with all the goodness of a XAML window.

Getting Started

First thing we need to do is create a new solution with a blank F# application project – I have made mine called FSharpWPF.

2010-06-10 07-40-18 PM

Once you have the project created you will need to change the project type from a Console Application to a Windows Application. You do this by right clicking on the project file and going to its properties…

2010-06-10 07-43-57 PM

Once that is done you will need to add the appropriate references. You do this by right clicking on the References in the Solution Explorer and clicking “Add Reference'”. You should add the appropriate .Net references below for WPF & XAMl to work.

2010-06-10 07-46-06 PM

Once these references are added you then need to add your XAML file to the project. You can do this by adding a new item to the project of type xml and simply changing the file extension from xml to xaml.

2010-06-10 07-49-29 PM

Once the xaml file has been added to the project you will need to add valid window XAML. Example of a very basic xaml file is shown below…

<Window xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        Title="F# WPF WPF Form" Height="350" Width="525">   
    <Grid>
    </Grid>
</Window>

Once your xaml file is done… you need to set the build action of the xaml file from “None” to “Resource” as depicted in the picture below.

2010-06-10 07-55-06 PM

If you do not set this you will get an IOException error when running the completed project with a message along the lines of “Cannot locate resource ‘window.xaml’

You then need to tie everything up by putting the correct F# code in the Program.fs to load the xaml window. In the Program.fs put the following code…

module Program

open System
open System.Collections.ObjectModel
open System.IO
open System.Windows
open System.Windows.Controls
open System.Windows.Markup


[<STAThread>]
[<EntryPoint>]
let main(_) =
    let w = Application.LoadComponent(new System.Uri("/FSharpWPF;component/Window.xaml", System.UriKind.Relative)) :?> Window
    (new Application()).Run(w)
Once all this is done you should be able to build and run your project. What you have done is created a WPF based window inside a FSharp project. It should look something like below…

2010-06-10 07-59-06 PM

Nothing to exciting, but sufficient to illustrate the very basic WPF form in F#. Hopefully in future posts I will build on this to expose button events etc.