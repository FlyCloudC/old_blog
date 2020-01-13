---
layout: default
title: Home
nav: true
---
<div class="row">
  <section class="sidebar-sec">
    <div class="sidebar">
      <img class="avatar" width="100px" height="100px" src="https://graph.baidu.com/thumb/343366187,1313656684.jpg"></img>
      <p>一个普通又平凡的OIer</br>偶尔刷刷算法题</br>或者看一些杂七杂八的东西</p>
    </div>  
  </section>
  <section class="article-sec">
  {% for post in site.posts %}
    <div class="article">
      <a href="{{ post.url | prepend: site.baseurl }}">
        <h2>{{ post.title }}</h2>
        <p>{{ post.content | strip_html | truncate:200 }}</p>
      </a>
    </div>
  {% endfor %}
  </section>
</div>