---
# obligatory
layout: page
title: "mixing" # in HTML meta and tab title

# optional, no defaults
# permalink: # custom page URL, begin with /
# tags: ai # tags for blog posts; space separated
# nav_label: # label to appear in navbar; reference in _data/navbar.yml

# optional, overrides defaults
# type: # defaults to website, otherwise one of: article, music, video
# description: # in blog index, HTML meta and social media snippets
# image: # path to an image for social media shares, AR 1.9:1, typically 1200x630, begin with /
# image_alt: # description of the social image
---
{%- assign tag = page.title -%}
{% include post_index.html filter=tag %}