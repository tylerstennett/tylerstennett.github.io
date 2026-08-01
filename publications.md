---
title: Publications
permalink: /publications/
---

Publications are listed in reverse chronological order. See also my *[Google Scholar profile]* and *[DBLP page]* (placeholders — add links).

{% assign years = site.data.publications | map: "year" | uniq | sort | reverse %}
{% for y in years %}

## {{ y }}

{% assign in_year = site.data.publications | where: "year", y %}
{% for pub in in_year %}{% include publication.html pub=pub %}{% endfor %}
{% endfor %}
