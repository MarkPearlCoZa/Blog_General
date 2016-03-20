---
layout: page
title: Software Development
tagline: my thoughts and comments
---
{% include JB/setup %}

## Recent Posts

{% assign posts_per_page = 15 %}
{% assign more_posts_to_show = false %}

<ul class="posts">
  {% for post in site.posts %}
    {% if forloop.index <= posts_per_page %}
        <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
    {% else %}
        {% assign more_posts_to_show = true %}
    {% endif %}
  {% endfor %}
  {% if more_posts_to_show == true %}
    <a href=''>See all posts...</a>
  {% endif %}
</ul>
