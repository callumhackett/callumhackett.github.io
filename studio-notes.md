---
# obligatory
layout: page
title: Studio Notes # in HTML meta and tab title

# optional, no defaults
permalink: /studio-notes # custom page URL, begin with /

# optional, overrides defaults
# type: # defaults to website, otherwise one of: article, music, video
# description: # in blog index, HTML meta and social media snippets
image: /assets/images/social/studio_notes.jpg # path to an image for social media shares, AR 1.9:1, typically 1200x630, begin with /
social_image_alt: Studio Notes by Callum Hackett # description of the social image
# comments: true # uncomment for a Disqus thread; post dates and page titles should be unique and unchanged
---
*<a href="https://www.callumhackett.com/feed.xml">Link to posts feed</a> (for your reader of choice)*

<div id="blog-index">
    {% for post in site.posts %}
    <div id="blog-entry">
        <a href="{{ post.url }}"><img src="{{ post.image }}"/></a>
        <h1><a href="{{ post.url }}">{{ post.title }} — {% include post_date.html %}</a></h1>
        <div id="comments-count">
            <h3><a href="{{ post.url }}#disqus_thread" data-disqus-identifier="{{ post.date | date: "%Y-%m-%d" }}"></a> 💬</h3>
        </div>
        <p>{{ post.description | smartify }}</p>
    </div>
    {% endfor %}
</div>
<script id="dsq-count-scr" src="//callum-hackett.disqus.com/count.js" async></script>