---
layout: page
title: Software Development
tagline: my thoughts and comments
---
{% include JB/setup %}

<p>Blog Posts</p>

<ul>
  {% for post in site.categories.general %}
    {% if post.url %}
        <li><a href="{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
