---
layout: default
title: 北冥鲲鹏
tagline: 
---
{% include JB/setup %}

{% for post in site.posts limit: 1 %}
<h1>
  <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
</h1>
<p class="text-right">
{% for tag in post.tags %}
  <a href="/tags.html#{{ tag }}" title="{{ tag }}" class="tag">
  <span class="label label-default">{{ tag }}</span>
  </a>
{% endfor %}
<time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time>
</p>
<div class="content">
{{ post.content }}
</div>
{% endfor %}

<hr/>
#### 今年稍早的文章
<ul class="posts">
 {% capture year %}{{ site.time | date:"%Y"}}{% endcapture %}
  {% for post in site.posts offset:1 %}
    {% capture y %}{{ post.date | date:"%Y"}}{% endcapture %}
    {% if year != y %}
    {% break %}
    {% endif %}
    <li>
      <time datetime="{{ post.date | date:"%Y-%m-%d" }}">{{ post.date | date:"%Y-%m-%d" }}</time>
      <a href="{{ BASE_PATH }}{{ post.url }}" title="{{ post.title }}">{{ post.title }}</a>
      </li>
  {% endfor %}
</ul>

[所有文章](/archive.html)



