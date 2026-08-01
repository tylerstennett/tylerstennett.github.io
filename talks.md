---
title: Talks
permalink: /talks/
---

<ul class="item-list">
{% assign talks = site.data.talks | sort: "date" | reverse %}
{% for talk in talks %}
  <li class="item">
    <div class="item-title">{{ talk.title }}</div>
    <div class="item-meta">{{ talk.event }} &middot; {{ talk.location }} &middot; <time datetime="{{ talk.date | date_to_xmlschema }}">{{ talk.date | date: "%B %Y" }}</time></div>
    {% if talk.links %}
    <div class="pub-links">
      {% for link in talk.links %}<a class="pill" href="{{ link[1] }}">{{ link[0] }}</a>{% endfor %}
    </div>
    {% endif %}
  </li>
{% endfor %}
</ul>
