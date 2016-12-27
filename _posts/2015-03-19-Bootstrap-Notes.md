---
layout: post
title: Bootstrap Notes
tags: Web
category: Tech
---

# Bootstrap 3 

## Basics 

Bootstrap works on a 12 column grid  

### Column Basics 

~~~
<div class='container'>
	<div class='row'>
		<div class='col-md-12'>...</div>
	</div>
</div>
~~~

### Empty Columns

~~~
<div class='col-md-1 col-md-offset-1'>
	...
</div>
~~~

### Working on smaller screens (small and extra small) 

Small screens...

~~~
col-sm-*
~~~

Extra small screens...

~~~
col-xs-*
~~~

### Removing an offset 

~~~
col-cs-offset-0
~~~

#### Hiding elements in 1 or more screen sizes 

~~~
hidden-xs
hidden-md
hidden-lg
~~~

#### Showing elements in 1 or more screen sizes 

~~~
visible-xs  
visible-md  
visible-lg  
~~~

#### Overiding Fonts 

~~~
<p class='lead'>Make your way to space...</p>
~~~

#### Centering Text 

~~~
<p class='text-center'>This text is centered</div>
~~~

.text-justify  
.text-right  
.text-center  
.text-left  

#### Adding Icons 

~~~
<i class='glyphicon glyphicon-briefcase'></i>
~~~

#### Increasing Font Size of Icons 

Add a custom css file, with your specific customizations

In the css file have the following...  
~~~
.features .glyphicon {
	font-size:32px;
	color:red;
}
~~~

~~~
<i class='features glyphicon-briefcase'></i>
~~~

----------------------------------------------------------------------------------------------------------------

# Bootstrap 4

## What's new

* Typographic units of measure now in rem  
* Extra breakpoint at 480px for smaller screens  
* A new sm grid tier   

### References 

[Bootstrap](http://getbootstrap.com/)  
[Example Code from Code School Slides](https://github.com/codeschool/BlastingOffWithBootstrapDemo)  
[Sample Site from Code School Site](http://codeschool.github.io/BlastingOffWithBootstrapDemo/)  
[Example Sites Using Bootstrap](http://expo.getbootstrap.com/)  
[Bootstrap Blog](http://blog.getbootstrap.com/)  
[Glyphicons](http://getbootstrap.com/components/#glyphicons)  
[Free Bootstrap Themes](http://startbootstrap.com/)  
[Customize Bootstrap Library](http://getbootstrap.com/customize/)  

[DNC Magazine Dec 2016](https://dncmagazine.blob.core.windows.net/edition27/DNCMag-Issue27.pdf)  
