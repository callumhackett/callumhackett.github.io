---
layout: page
title: Diary
---
<div>
    {% for post in site.posts %}
        <div class="date">{{ post.date | date_to_string }}</div>
        <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
    {% endfor %}
</div>