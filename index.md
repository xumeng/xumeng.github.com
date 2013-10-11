---
layout: page
title: 徐不猛的程序之道
tagline: 子曰：君子惠而不费，劳而不怨，欲而不贪，泰而不骄，威而不猛！
---
{% include JB/setup %}

###最新
<ul class="posts">
  {% for post in site.posts %}

    <li><h2 class="postTitleClass"><a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a></h2></li>
     <span class="subTitleClass">日期:{{ post.date | date_to_string }}</span><br>
    {{ post.content | truncate: 257 }}
     <p> <a href="{{ post.url }}/#more" class="more-link"><span class="readmore">阅读全文 &raquo; </span></a></p>
  {% endfor %}
</ul>
###分类
<ul>

    {% for category in site.categories %}
    <li><a href="/categories/{{ category | first }}/" title="看你妹">{{ category | first }} {{ category | last | size }}</a>
    </li>
    {% endfor %}
</ul>

