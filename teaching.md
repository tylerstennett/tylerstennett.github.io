---
title: Teaching
permalink: /teaching/
---

<ul class="item-list">
{% for entry in site.data.teaching %}
  <li class="item">
    <div class="item-title">{{ entry.course }}</div>
    <div class="item-meta">{{ entry.role }} &middot; {{ entry.institution }} &middot; {{ entry.term }}</div>
    {% if entry.description %}<p class="item-desc">{{ entry.description }}</p>{% endif %}
  </li>
{% endfor %}
</ul>
