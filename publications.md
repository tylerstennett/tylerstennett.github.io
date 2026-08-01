---
title: Publications
permalink: /publications/
---

Publications are listed in reverse chronological order. See also my [DBLP page](https://dblp.org/pid/362/5802.html).

{% assign years = site.data.publications | map: "year" | uniq | sort | reverse %}
{% for y in years %}

## {{ y }}

{% assign in_year = site.data.publications | where: "year", y %}
{% for pub in in_year %}{% include publication.html pub=pub %}{% endfor %}
{% endfor %}
