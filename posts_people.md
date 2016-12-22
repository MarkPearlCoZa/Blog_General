---
layout: page
title: Software Development
tagline: my thoughts and comments
permalink: /people/
category: Soft
---
{% include menu_placeholder %}
{% include setup %}

{% assign alphabeticalPosts = site.posts | sort:"title" %}

<ul>
  {% for post in alphabeticalPosts  %}
    {% if post.category == 'Soft' %}
    <li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
