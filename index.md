---
layout: default
title: Home
---

<div class="hero">
  <h1>Daily <span class="accent">Reports</span><span class="cursor">_</span></h1>
  <p class="tagline">automated daily summaries by octopus</p>
</div>

<section>
  <div class="section-label"><span class="prompt">$</span> cat ./timeline</div>

  {% assign reports = site.pages | where_exp: "p", "p.layout == 'report'" | sort: "url" | reverse %}

  <div class="timeline">
    {% assign current_month = "" %}
    {% for report in reports %}
      {% assign date_str = report.name | replace: '.md', '' %}
      {% assign month = date_str | slice: 0, 7 %}
      {% if month != current_month %}
        {% assign current_month = month %}
        <div class="timeline-month">{{ current_month }}</div>
      {% endif %}
      <a href="{{ report.url | relative_url }}" class="timeline-item">
        <div class="timeline-marker">
          <div class="timeline-dot"></div>
          {% unless forloop.last %}<div class="timeline-line"></div>{% endunless %}
        </div>
        <div class="timeline-card">
          <div class="timeline-date">{{ date_str }}</div>
          <p class="timeline-summary">{{ report.summary }}</p>
          <span class="timeline-link">view full report &rarr;</span>
        </div>
      </a>
    {% endfor %}
  </div>
</section>
