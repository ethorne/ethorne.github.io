---
layout: home
name:   posts
title:  Blog
---

<ul class="post-list">
{% for post in site.posts %}
  <li>
    <h2>
      <a class="post-link" href="{{ post.url | relative_url }}">
        {{ post.title }}
      </a>
    </h2>
  </li>
{% endfor %}
</ul>
