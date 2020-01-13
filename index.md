---
layout: default
title: Home
nav: true
---
{% for page  in site.posts %}
<div class="article">
<h2>{{ page.title }}</h2>
</div>
{% endfor %}