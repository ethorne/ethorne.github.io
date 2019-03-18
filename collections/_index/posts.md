---
layout: home
name:   posts
title:  Blog
---

{% for post in site.posts %}
<a href="{{ post.url }}"> {{ pos.title }}</a>
{% endfor %}
