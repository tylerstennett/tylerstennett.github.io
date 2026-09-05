---
title: Posts
description: Accessible research notes about my papers and shorter updates about my work.
permalink: /posts/
---

<p class="page-intro">Longer, more readable notes about my research, followed by shorter updates and announcements.</p>

<section class="posts-section" aria-labelledby="research-notes-heading">
  <h2 class="eyebrow" id="research-notes-heading">Research Notes</h2>
  <div class="post-preview-list research-preview-list">
    {% assign research_notes = site.research | sort: "date" | reverse %}
    {% for note in research_notes %}
    <article class="post-preview research-preview">
      <p class="post-preview-meta">
        <time datetime="{{ note.date | date_to_xmlschema }}">{{ note.date | date: "%b %-d, %Y" }}</time>
        <span aria-hidden="true">&middot;</span>
        <span>{% include reading-time.html content=note.content %}</span>
        {% if note.venue %}<span aria-hidden="true">&middot;</span><span>{{ note.venue }}</span>{% endif %}
      </p>
      <h3><a href="{{ note.url | relative_url }}">{{ note.title }}</a></h3>
      <p>{{ note.takeaway }}</p>
      <a class="read-more" href="{{ note.url | relative_url }}">Read research note <span aria-hidden="true">&rarr;</span></a>
    </article>
    {% endfor %}
  </div>
</section>

<section class="posts-section" id="news" aria-labelledby="news-heading">
  <h2 class="eyebrow" id="news-heading">News</h2>
  <div class="post-preview-list news-preview-list">
    {% for post in site.posts %}
    <article class="post-preview news-preview">
      <p class="post-preview-meta"><time datetime="{{ post.date | date_to_xmlschema }}">{{ post.date | date: "%b %-d, %Y" }}</time></p>
      <h3><a href="{{ post.url | relative_url }}">{{ post.title }}</a></h3>
      <p>{{ post.excerpt | strip_html | normalize_whitespace | truncatewords: 24, "…" }}</p>
      <a class="read-more" href="{{ post.url | relative_url }}">Read announcement <span aria-hidden="true">&rarr;</span></a>
    </article>
    {% endfor %}
  </div>
</section>
