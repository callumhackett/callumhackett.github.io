---
layout: page
title: Diary
permalink: diary
---
<div>
    {% for post in site.posts %}
        <div class="diary-summary">
            <div class="diary-date"><a href="{{ post.url }}">{{ post.date | date_to_long_string: "ordinal" }}</a></div>
            {{ post.excerpt }}
            <p><a href="{{ post.url }}"><span style="display: block; margin: -9px 0 0 0; font-size: 0.9em;">⊰ <em>continue</em> ⊱</span></a></p>
        </div>
    {% endfor %}
</div>