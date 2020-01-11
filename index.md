---
layout: default
title: Home
nav: true
---
{% for post in site.posts %}
<div class="article" onclick="window.open('{{ site.baseurl | post.url }}','_self')">
  <h2>{{ post.title }}</h2>
  <p>{{ post.content | strip_html | truncate:200 }}
</div>
{% endfor %}