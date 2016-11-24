---
layout: page
title: Software Development
tagline: my thoughts and comments
---
{% include setup %}

{% assign generalPosts = site.posts %}
{% for post in generalPosts %}
    <div class="mobile visible-sm visible-xs"><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></div>
{% endfor %}

<ul>
  {% for post in site.posts %}
    {% if post.category == 'General' %}
    <li class="desktop hidden-sm hidden-xs"><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
    <div class="mobile visible-sm visible-xs"><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></div>
    {% endif %}
  {% endfor %}
</ul>
