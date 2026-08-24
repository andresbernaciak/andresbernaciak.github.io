---
layout: page
title: Posts
permalink: /posts/
---

# Writing

Notes on applied AI, value creation, operating problems, and what I learn while building.

## Current

{% for post in site.posts %}
  {% assign post_year = post.date | date: "%Y" %}
  {% unless post_year == "2020" %}
### [{{ post.title }}]({{ post.url | relative_url }})

*{{ post.date | date: "%B %-d, %Y" }}*

{{ post.excerpt | strip_html | truncatewords: 35 }}

  {% endunless %}
{% endfor %}

## Archive: Data Science Journey, 2020

These posts were originally published in 2020 while I was teaching myself data science and software development. I've kept them as part of the site's history and as a record of an earlier stage in my technical learning.

{% for post in site.posts %}
  {% assign post_year = post.date | date: "%Y" %}
  {% if post_year == "2020" %}
### [{{ post.title }}]({{ post.url | relative_url }})

*{{ post.date | date: "%B %-d, %Y" }}*

{{ post.excerpt | strip_html | truncatewords: 35 }}

  {% endif %}
{% endfor %}
