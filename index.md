---
layout: page
title: 徐不猛的程序之道
tagline: 子曰：君子惠而不费，劳而不怨，欲而不贪，泰而不骄，威而不猛！
---
{% include JB/setup %}


<ul class="posts">
  {% for post in site.posts %}
    <li><span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></li>
  {% endfor %}
</ul>
