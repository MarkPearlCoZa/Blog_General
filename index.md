---
layout: page
title: Software Development
tagline: my thoughts and comments
---
{% include setup %}

{% assign previous_post_date = "0000" %}
{% assign general_posts = site.posts | where: "category", "General" %}

<ul>
  {% for post in  general_posts %}
    {% assign current_post_date =  post.date | date: "%m%y" %}

    {% if current_post_date != previous_post_date %}
    <p> {{ post.date | date: "%B, %Y" }}</p>
    {% endif %}

    <li class="desktop hidden-sm hidden-xs"><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
    <div class="mobile visible-sm visible-xs"><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></div>
    {% assign previous_post_date = current_post_date %}
  {% endfor %}
</ul>
