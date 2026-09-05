---
title: CV
permalink: /cv/
updated: 2026-09-05
pdf: /assets/files/Tyler_Stennett_CV.pdf
---

{% assign cv_url = page.pdf | relative_url %}

<p class="page-intro">My full curriculum vitae: education, research experience, publications, awards, teaching, and service.</p>

<div class="cv-actions">
  <a class="button" href="{{ cv_url }}" download="Tyler_Stennett_CV.pdf">Download PDF</a>
  <a class="cv-open" href="{{ cv_url }}" target="_blank" rel="noopener">Open in new tab <span aria-hidden="true">&#8599;</span></a>
  <span class="cv-updated">Updated {{ page.updated | date: "%B %Y" }}</span>
</div>

<div class="cv-viewer">
  <object class="cv-embed" data="{{ cv_url }}#view=FitH&amp;toolbar=0&amp;navpanes=0" type="application/pdf" title="Tyler Stennett's CV">
    <p class="cv-fallback">This browser can't display PDFs inline. <a href="{{ cv_url }}">Download the PDF</a> instead.</p>
  </object>
</div>
