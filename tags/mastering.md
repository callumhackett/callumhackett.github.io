---
# obligatory
layout: page
title: "mastering" # in HTML meta and tab title

# optional, no defaults
# permalink: # custom page URL, begin with /
# tags: # tags for blog posts; space separated
# nav_label: # label to appear in navbar; reference in _data/navbar.yml

# optional, overrides defaults
# type: # defaults to website, otherwise one of: article, music, video
# description: # in blog index, HTML meta and social media snippets
# image: # path to an image for social media shares, AR 1.9:1, typically 1200x630, begin with /
# image_alt: # description of the social image
---
{% include post_index.html filter=page.title %}