---
# obligatory
layout: page
title: Studio Notes # in HTML meta and tab title

# optional, no defaults
permalink: /studio-notes # custom page URL, begin with /

# optional, overrides defaults
# type: # defaults to website, otherwise one of: article, music, video
# description: # in HTML meta and social media snippets
# og_image: # path to an image for social media shares, AR 1.9:1, typically 1200x630, begin with /
# twitter_image: # path to an image for twitter shares, AR 1:1, begin with /
# social_image_alt: # description of the social image
---
*<a href="https://www.callumhackett.com/feed.xml">Link to posts feed</a> (for your reader of choice)*

{% for post in site.posts %}
<div><img src="{{ post.og_image }}" width="30%" style="border-radius: 4px; float: left; margin-right: 20px;"/><h1><a href="{{ post.url }}">{{ post.date | date: "%d.%b.%y" }} — {{ post.title }}</a></h1>
<p>{{ post.description | smartify }}</p></div>
{% endfor %}