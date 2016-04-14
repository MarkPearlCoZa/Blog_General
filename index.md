---
layout: page
title: Software Development
tagline: my thoughts and comments
---
{% include JB/setup %}

<ul id="tabs" class="nav nav-tabs" data-tabs="tabs">
<li class="active"><a href="#blog" data-toggle="tab">Blog Posts</a></li>
<li><a href="#tech" data-toggle="tab">Tech Notes</a></li>
<li><a href="#soft" data-toggle="tab">Soft Notes</a></li>
<li><a href="#misc" data-toggle="tab">Misc</a></li>
</ul>
<div id="my-tab-content" class="tab-content">

	{% assign alphabeticalPosts = site.posts | sort:"title" %}

	<div class="tab-pane active" id="blog">
		<ul>
		  {% for post in site.posts %}
			{% if post.category == 'General' %}
			<li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
			{% endif %}
		  {% endfor %}
		</ul>
	</div>
	<div class="tab-pane" id="tech">
		<ul>
		  {% for post in alphabeticalPosts  %}
			{% if post.category == 'Tech' %}
			<li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
			{% endif %}
		  {% endfor %}
		</ul>
	</div>
	<div class="tab-pane" id="soft">
		<ul>
		  {% for post in alphabeticalPosts %}
			{% if post.category == 'Soft' %}
			<li><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
			{% endif %}
		  {% endfor %}
		</ul>
	</div>
	<div class="tab-pane" id="misc">
		<ul>
		  {% for post in site.posts %}
			{% if post.category == 'Misc' %}
			<li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
			{% endif %}
		  {% endfor %}
		</ul>
	</div>
</div>

