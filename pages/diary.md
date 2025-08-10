---
layout: page
title: Diary
---
<div>
    {% for post in site.posts %}
        <div class="diary-summary">
            <a href="{{ post.url }}"><div class="date">{{ post.date | date_to_string }}</div></a>
            <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
            {{ post.excerpt }}
            <a href="{{ post.url }}"><span style="display: block; margin: -12px 0 0 0;"><em>continue</em> …</span></a>
        </div>
    {% endfor %}
</div>