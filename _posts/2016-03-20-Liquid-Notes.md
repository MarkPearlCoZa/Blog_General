---
layout: post
title: Liquid Notes
tags: Useful
category: Tech
---

#### General ####

#### Tag for posts in a specific category ####

~~~
 assign sorted_tags = site.tags | sort 
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
