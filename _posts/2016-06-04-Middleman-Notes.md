---
layout: post
title: Middleman Notes
tags: html
category: Tech
---

#### Syntax for a link_to with html content and additional attributes ####

The following...

~~~
<% link_to('/yourlink.html', { :class => 'your-class another-class', :"data-icon" => 'd' }) do %>Link Text<% end %>
~~~

Will render the following html...

~~~
<a class="your-class another-class" data-icon="d" href="yourlink/">Link Text</a>
~~~

[See original thread](https://github.com/middleman/middleman/issues/881)  


#### References ####

[Understanding Middleman - the static site generator for faster prototyping](https://benfrain.com/understanding-middleman-the-static-site-generator-for-faster-prototyping/)  
[Github Middleman Project](https://github.com/middleman/middleman/)  
[Middleman App](https://middlemanapp.com/)  
