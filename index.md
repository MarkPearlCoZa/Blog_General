---
layout: page
title: Software Development
tagline: my thoughts and comments
category: General
---
{% include menu_placeholder %}
{% include setup %}

{% assign previous_post_date = "0000" %}
{% assign general_posts = site.posts | where: "category", "General" %}

<ul>
  {% for post in  general_posts %}
    {% assign current_post_date =  post.date | date: "%m%y" %}

    {% if current_post_date != previous_post_date %}
        <br>
        <h2> {{ post.date | date: "%B, %Y" }} </h2>
    {% endif %}

    &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a><br>
    <div class="mobile visible-sm visible-xs"><br></div>

    {% assign previous_post_date = current_post_date %}
  {% endfor %}
</ul>
