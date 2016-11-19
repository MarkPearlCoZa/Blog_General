---
layout: page
title: Software Development
tagline: my thoughts and comments
permalink: /tech/
---
{% include setup %}

{% assign alphabeticalPosts = site.posts | sort:"title" %}

<ul>
  {% for post in alphabeticalPosts  %}
    {% if post.category == 'Misc' %}
    <li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
