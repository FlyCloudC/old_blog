---
layout: default
title: Home
nav: true
---
{% for page  in site.posts %}
<div>
{{ page.title }}
</div>
{% endfor %}