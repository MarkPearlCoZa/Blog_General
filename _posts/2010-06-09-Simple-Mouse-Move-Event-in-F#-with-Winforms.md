---
layout: post
title: Simple Mouse Move Event in F# with Winforms
tags: 
category: General
---
 

This evening I had the pleasure of reading one of ThomasP’s blog posts on first class events. It was an excellent read, and I thought I would make a brief derivative of his post to explore some of the basics.

In Thomas’s post he has a form with an ellipse on it that when he clicks on the ellipse it pops up a message box with the button clicked… awesome. Something that got me on the post though was the code similar to the one below…

~~~
// React to Mouse Move events on the form
let evtMessages =
    frm.MouseMove      
     |> Event.map (fun mi ->                                
        mi.Location.ToString())
     |> Event.map (sprintf "Hey, you clicked on the ellipse.\nUsing: %s")
     |> Event.add (MessageBox.Show >> ignore)
~~~

The MessageBox is a function with a string passed into it. What if I wanted to rather change a mutable value holder instead, how would the syntax go for that? Immediately the thought came to me of anonymous functions. I’ve used them before to do something like this…

let HelloPerson personName = 
    "Hello " + personName |> fun(x) -> Console.WriteLine(x)    
So using the same approach I adapted the event code to instead of showing a Message Box with a string passed in to it, to rather change the forms header.

|> Event.map (sprintf "Your mouse position is %s")
|> Event.add(fun(x) -> frm.Text <- x)

Okay… it looks a bit weird with the –> x <- syntax, but makes sense and works… The next thing I wanted to do was change Thomas’s code sample from having an ellipse, and reacting to the position of the mouse and click, to rather trigger the event whenever the mouse moved. This simple involved removing some filtering code.

Finally I wanted the code to work as a FSharp Project without having to run through the F# interactive. To achieve this I just needed to find out how to trigger the window event loop. This can be achieved with the code below…

// Program eventloop
while frm.Created do
    Application.DoEvents()
 

So lets look at the complete code sample…

~~~
#light
open System
open System.Drawing
open System.Windows.Forms

// Create the main form
let frm = new Form(ClientSize=Size(600,400))

// React to Mouse Move events on the form
let evtMessages =
    frm.MouseMove      
     |> Event.map (fun mi ->                                
        mi.Location.ToString())     
     |> Event.map (sprintf "Your mouse position is %s")
     |> Event.add(fun(x) -> frm.Text <- x)

// Show the form
frm.Show()

// Program eventloop
while frm.Created do
    Application.DoEvents()
~~~