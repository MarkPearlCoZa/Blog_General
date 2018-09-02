---
layout: post
title: Centralizing a resource file among multiple projects in one solution (C# and WPF)
tags: 
category: General
---
One of the challenges one faces when doing multi language support in WPF is when one has several projects in one solution (i.e. a business layer & ui layer) and you want multi language support. Typically each solution would have a resource file – meaning if you have 3 projects in a solution you will have 3 resource files.

Image1

 

For me this isn’t an ideal solution, as you normally want to send the resource files to a translator and the more resource files you have, the more fragmented the dictionary will be and the more complicated it will be for the translator.

This can easily be overcome by creating a single project that just holds your translation resources and then exposing it to the other projects as a reference as explained in the following steps.

Step 1

Step 1 -  Add a class library to your solution that will contain just the resource files.

Image2

Your solution will now have an additional project as illustrated below.

Image3

Step 2

Reference this project to the other projects.

Image4

Step 3

Move all the resources from the other resource files to the translation projects resource file.

Step 4

Set the translations projects resource files access modifier to public.

Image5

Step 5

Reference all other projects to use the translation resource file instead of their local resource file.

To do this in xaml you would need to expose the project as a namespace at the top of the xaml file… note that the example below is for a project called MaxCutLanguages – you need to put the correct project name in its place.

 

xmlns:MaxCutLanguages="clr-namespace:MaxCutLanguages;assembly=MaxCutLanguages"

 

And then in the actual xaml you need to replace any text with a reference to the resource file.

<TextBlock Text="{x:Static MaxCutLanguages:Properties.Resources.HelloWorld}"/>
End Result

You can now delete all the resource files in the other projects as you now have one centralized resource file.