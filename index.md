---
layout: default
title: Home
nav: true
---
{% for page  in site.posts %}
<div class="article">
  <a href="{{ post.url | prepend: site.baseurl }}">
    <h2>{{ page.title }}</h2>
    <p>{{ page.content | strip_html | truncate:200 }}</p>
  </a>
</div>
{% endfor %}