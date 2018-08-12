---
layout: post
title: Formatting Bound Data in WPF
tags: 
category: General
---
It suddenly got a whole lot easier in 3.5 SP1  

So, you are using WPF and getting all the goodness of binding to objects. You may have a decimal that you want to be displayed as a formatted currency, or a DateTime property that you want in a specific date format.  

Up to now, there were really two methods for achieving this.  

1) Format the data in code as a string and instead of binding to the data, bind to the formatted string data.  
2) Create a ValueConverter.  

So up to now I have always opted for method number two, while it is a bit of work, it seems natural to keep your “code” clean and have the formatting done via XAML. Well, in SP1 of .Net 3.5 they introduced Binding.StringFormat.  

Basically, you can specify the formatting in XAML without having to create a custom value converter.  

e.g.

~~~
Text="{Binding Path=Value, StringFormat='dd MMM yyyy'}"
~~~
