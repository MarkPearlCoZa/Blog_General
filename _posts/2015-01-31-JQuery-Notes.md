---
layout: post
title: JQuery Notes
tags: Libraries
category: Tech
---
### General ###

~~~
$('div'.addClass('foo');
~~~

This adds a css class to all the div tags on the page.  

~~~
$(document).ready(function() {
	$('button#myButton').click(function() {
		alert('Button was clicked');
	});
});  
~~~

#### Unobtrusive JavaScript ####

Unobtrusive javascript is the process of keeping the site's markup separate from its behavior (code).  

#### References ####

[The Mother Ship - JQuery](http://jquery.com/)  
