---
layout: page
title: Software Development
tagline: my thoughts and comments
permalink: /blog/
---
{% include setup %}

<ul id="tabs" class="nav nav-tabs" data-tabs="tabs">
<li class="active"><a href="#blog" data-toggle="tab">Blog Posts</a></li>
<li><a href="#tech" data-toggle="tab">Tools & Technology</a></li>
<li><a href="#soft" data-toggle="tab">Teams & People</a></li>
<li><a href="#process" data-toggle="tab">Processes & Techniques</a></li>
<li><a href="#media" data-toggle="tab">Media</a></li>
<li><a href="#misc" data-toggle="tab">Misc</a></li>
</ul>

<div id="my-tab-content" class="tab-content">

    {% assign alphabeticalPosts = site.posts | sort:"title" %}

    <ul>
      {% for post in site.posts %}
        <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
      {% endfor %}
    </ul>

</div>

