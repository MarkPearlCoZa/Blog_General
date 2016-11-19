---
layout: page
title: Software Development
tagline: my thoughts and comments
permalink: /tech/
---
{% include setup %}

<div class="tab-pane active" id="blog">
    <ul>
      {% for post in alphabeticalPosts  %}
        {% if post.category == 'Tech' %}
        <li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
        {% endif %}
      {% endfor %}
    </ul>
</div>
