---
layout: post
title: Liquid Notes
tags: Web
category: Tech
---

#### General ####

#### Tag for posts in a specific category ####

~~~
 {% assign sorted_tags = site.tags | sort %}
 for tag in sorted_tags 
 assign zz = tag[1] | where: "category", "Photoshop" | sort 
 if zz != empty 

   for p in zz 
  {{ p.url }}{{ p.title }}
   endfor 
  endif 

  endfor 
~~~

#### References ####

[Liquid Reference](https://shopify.github.io/liquid/)  
[Cheat Sheet](http://cheat.markdunkley.com/)  
[Date Formatting Examples](ihttp://alanwsmith.com/jekyll-liquid-date-formatting-examples)  
