---
layout: post
title: Middleman Notes
tags: html
category: Tech
---

#### Get path of current page ###

You have access to the current_page variable. current_page.path is the source path of this resource (relative to the source directory, without template extensions) and current_page.url is the path without the directory index (so foo/index.html becomes just foo).

~~~
<%= current_page.path %>
# -> index.html
~~~

~~~
<%= current_page.url %>
# -> /
~~~



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
