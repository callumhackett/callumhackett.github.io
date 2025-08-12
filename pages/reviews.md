---
layout: page
title: Reviews
permalink: reviews
---
<div>
    {% assign sorted_posts = site.posts | sort: "title" %}
    {% for post in sorted_posts %}
        {% if post.tags contains "review" %}
            <div class="review-list">
                <a href="{{ post.url }}">{{ post.title }}</a><br />
                <p class="post-description">{{ post.description }}</p>
            </div>
        {% endif %}
    {% endfor %}
</div>