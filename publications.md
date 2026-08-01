---
title: Publications
permalink: /publications/
---

A semi-up-to-date list of my publications, newest first. For the latest and greatest, check out my [Google Scholar](https://scholar.google.com/citations?user=t2rIsdIAAAAJ&hl=en)!

{% assign years = site.data.publications | map: "year" | uniq | sort | reverse %}
{% for y in years %}

## {{ y }}

{% assign in_year = site.data.publications | where: "year", y %}
{% for pub in in_year %}{% include publication.html pub=pub %}{% endfor %}
{% endfor %}
