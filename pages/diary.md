---
layout: page
title: Diary
---
<div>
    {% for post in site.posts %}
        <div class="diary-summary">
            {{ post.excerpt }}
            <p><a href="{{ post.url }}"><span style="display: block; margin: -8px 0 0 0; font-size: 0.9em;"><em>continue</em> …</span></a></p>
        </div>
    {% endfor %}
</div>