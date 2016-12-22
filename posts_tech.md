---
layout: page
title: Software Development
tagline: my thoughts and comments
permalink: /tech/
category: Tech
---
{% include menu_placeholder %}
{% include setup %}

{% assign alphabeticalPosts = site.posts | sort:"title" %}

<ul>
  {% for post in alphabeticalPosts  %}
    {% if post.category == 'Tech' %}
    <li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
