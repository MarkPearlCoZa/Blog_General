---
layout: page
title: Software Development
tagline: my thoughts and comments
permalink: /blog/
---
{% include setup %}


<div id="my-tab-content" class="tab-content">

    {% assign alphabeticalPosts = site.posts | sort:"title" %}

    <ul>
      {% for post in site.posts %}
        <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
      {% endfor %}
    </ul>

</div>

