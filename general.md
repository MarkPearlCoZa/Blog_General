---
layout: page
title: Software Development
tagline: my thoughts and comments
permalink: /blog/
---
{% include JB/setup %}
{% assign alphabeticalPosts = site.posts | sort:"title" %}

<ul>
  {% for post in site.posts %}
    {% if post.category == 'General' %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ul>

