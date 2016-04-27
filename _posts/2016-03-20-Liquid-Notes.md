---
layout: post
title: Liquid Notes
tags: Useful
category: Tech
---

#### General ####

#### Tag for posts in a specific category ####

~~~
{% assign sorted_tags = site.tags | sort %}
{% for tag in sorted_tags %}
{% assign zz = tag[1] | where: "category", "Photoshop" | sort %}
{% if zz != empty %}

<li><span class="tag">{{ tag[0] }}</span>
<ul>
  {% for p in zz %}
  <li><a href="{{ p.url }}">{{ p.title }}</a></li>
  {% endfor %}
 </ul>
 </li>
 {% endif %}

 {% endfor %}
~~~

#### References ####

[Liquid Reference](https://shopify.github.io/liquid/)  
