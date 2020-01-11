---
layout: default
title: Home
nav: true
---
{% for page  in site.posts %}
<div class="article" onclick="window.open('{{ page.url | prepend: site.baseurl }}','_self')">
  <h2>{{ page.title }}</h2>
  <p>{{ page.content | strip_html | truncate:200 }}</p>
</div>
{% endfor %}