---
layout: home
name:   career
title:  Career
---
<div class="vertical-block-container">
{% for pos in site.career %}
  <div class="block" style="order: {{ pos.order }}">
    <a href="{{ pos.url }}"> {{ pos.jobTitle }} at {{ pos.company }}</a>
  </div>
{% endfor %}
</div>
