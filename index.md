---
layout: page
title: Software Development
tagline: my thoughts and comments
---
{% include JB/setup %}

## Categories 

{% for category in site.categories %}
        {{ category | first }}
        {% unless forloop.last %}
        {% endunless %}
{% endfor %}

## Recent Posts

<ul class="posts">
  {% for post in site.posts %}
    {% if post.category contains 'General' %}
        <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
  <a href='{{ BASE_PATH }}/allposts'>See all general posts...</a>
</ul>

## Tech Notes

<ul class="posts">
  {% for post in site.posts %}
    {% if post.category contains 'Tech' %}
        <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ul>

## Soft Stuff Notes

<ul class="posts">
  {% for post in site.posts %}
    {% if post.category contains 'Soft' %}
        <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
    {% endif %}
  {% endfor %}
</ul>
