---
layout: post
title: Red Gate Ants Memory Profiler 7.1 – Initial thoughts and getting started
tags: 
category: Tech
---
I was really excited when I heard Red Gate wanted a review of their memory profiler done. I have been a fan of Red Gate products for years… being first exposed to their products via reflector a few years ago – as someone who has never done memory profiling before, I was also excited to go a bit deeper into .Net memory management.

Why Memory Profiler – Isn’t the point of .Net that it manages the memory for you?
Before getting into the nuts and bolts of the profiler, you might ask yourself – why use a memory profiler with .Net in the first place? Isn’t the purpose of .Net that it manages the memory for you?

To a large degree this is true – compared to the days of c++ where you were required to manage memory of nearly every object, .Net manages the lifespan of your objects in the background automatically. However even though your memory is managed, there are scenarios where the garbage collector in .Net gets it wrong which leads to less than optimal performance of an application. For me, this is where a product of regdate memory profiler is invaluable – allowing one to inspect behind the scenes of what is going on in ones application and take corrective actions if necessary.

Getting Started
My first attempt at looking at memory profiler was to create a new visual studio console app (vs2010 .Net v4) and run the “Profile Memory” option from the ANTS toolbar. Everything seemed to open fine and I was presented with a getting started window asking me whether I wanted to view some “Memory profiling video tutorials”, view “Strategies for memory profiling” or visit the “ANTS Memory Profiler forum”.

I decided to go blind in my first attempt, skip the tutorials and just muck around with the profiler. Closing the getting started window triggered the main profiler window to open and I was presented with a fairly simple view with a timeline graph and a “Take Memory Snapshot” button. After messing around with the snapshot section for a few minutes I soon realized that this is obviously not a hobbyist toy and one targeting the professional developer and that I needed to read the documentation if I was going to get any real value from the profiler.

So, reverting back to the getting started window I decided to view a few videos on the product.

The videos were very well put together and I would recommend everyone interested in memory profiler should watch them. One caveat – since I am from a country where we do not get the fastest bandwidth, I would I would get large pauses while playing the videos. It would be nice if there was a download section (If there is a download section and I missed it, please someone let me know so I can add a link).

After watching the video’s I felt better equipped to give the profiler another look. I created a simple WPF application – declared a custom class and instantiated various instances of it at different scoping levels to see if I could view them through the profiler. Sure enough – Memory Profiler showed me a full breakdown off my application – very cool….

Analytics
Now that I had got the basic navigation of memory profiler going – the scope of what Red Gate has put together began to dawn on me. Detecting memory problems is not a trivial matter in a .Net application and when profiling it’s not just the fact that one can see memory usages – that’s great, but what is even more important than that is that one can summarize what one is seeing (at a 10 000 foot view) or drill down to the smallest bit.

I am pleased to say that this is where I got really impressed with memory profiler. There are various ways to view memory being used by your application starting with a very effective summary screen – if one wants to drill down from the summary it is a matter of clicking on the relevant graph and inspecting.

Summary Screen

Clicking on an area breaks it down further – for example I found the class list view a very useful view to get an idea of what was happening (I grouped by namespace as I found this an easy way to identify objects initialized by my application directly).

Class List Screen

Another example of the effort put into the analytics of the app was the “Instance Categorizer” view. In a single screen one can easily see the reference relationships between classes and navigating these analytics is a pleasure.

Diagram

Taking it further
So, my initial feelings on Red Gates memory profiler is that it seems to be a powerful tool yet the power does not overwhelm you. The actual experience with the software is great and while I am a novice to memory profiling, Red Gate delivered what it promised… an ingeniously simple tool (with a lot of power packed in that word simple).

Keep an eye out for future posts as I get to grips with .Net memory management.