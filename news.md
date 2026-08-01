---
title: News
permalink: /news/
---

News and occasional longer posts. Subscribe via <a href="{{ '/feed.xml' | relative_url }}">RSS</a>.

<ul class="post-list">
{% for post in site.posts %}
  <li>
    <time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%b %-d, %Y" }}</time>
    <a href="{{ post.url | relative_url }}">{{ post.title }}</a>
    <p class="post-excerpt">{{ post.excerpt | strip_html | truncate: 160 }}</p>
  </li>
{% endfor %}
</ul>
