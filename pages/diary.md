---
layout: page
title: Diary
---
<div>
    {% for post in site.posts %}
        <div class="diary-summary">
            <a href="{{ post.url }}"><img class="diary-image" src="/assets/images/{{ post.featured-image }}" /></a>
            <a href="{{ post.url }}"><div class="date">{{ post.date | date_to_string }}</div></a>
            <h2><a href="{{ post.url }}">{{ post.title }}</a></h2>
            <p>{{ post.description }}</p>
        </div>
    {% endfor %}
</div>