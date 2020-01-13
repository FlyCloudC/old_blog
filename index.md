---
layout: default
title: Home
nav: true
---
{% for page  in site.posts %}
{{ page.title }}
{% endfor %}