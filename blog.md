---
layout: page
title: Blog
permalink: blog
---

{%- if site.posts.size > 0 -%}
<ul class="post-list">
    {%- for post in site.posts -%}
    <li>
    {%- assign date_format = site.minima.date_format | default: "%b %-d, %Y" -%}
    <span class="post-meta">{{ post.date | date: date_format }}</span>
    <h2>
        <a class="post-link" href="{{ post.url | relative_url }}">
        {{ post.title | escape }}
        </a>
    </h2>
        {% if post.featured-image %}
        <img src="{{ post.featured-image }}" class="blog-featured-image" alt="{{ post.featured-image-alt }}"><br />
        {% endif %}
        {{ post.excerpt }}
    </li>
    {%- endfor -%}
</ul>

<p class="feed-subscribe">
    <a href="{{ 'feed.xml' | relative_url }}">
    <svg class="svg-icon orange"><use xlink:href="{{ 'assets/minima-social-icons.svg#rss' | relative_url }}"></use></svg><span>Subscribe</span>
    </a>
</p>
{% else %}
There are no blog posts, yet.
{%- endif -%}
