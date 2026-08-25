---
layout: page
title: Achievements
---
{% if site.achievements.size == 0 %}
<div class="empty-state"><p>Achievements are on the way — check back soon.</p></div>
{% else %}
<p class="page-count">{{ site.achievements.size }} entries · newest first</p>
<ul class="timeline">
  {% assign achievements = site.achievements | sort: 'date' | reverse %}
  {% assign current_year = '' %}
  {% for achievement in achievements %}
    {% assign y = achievement.date | date: '%Y' %}
    {% if y != current_year %}
      {% assign current_year = y %}
      <li class="timeline-year"><span class="timeline-year-label">{{ y }}</span></li>
    {% endif %}
    <li class="timeline-item">
      {% if achievement.date %}<p class="timeline-date">{{ achievement.date | date: "%B %Y" }}</p>{% endif %}
      <h2 class="timeline-title"><a href="{{ achievement.url | relative_url }}">{{ achievement.title }}</a></h2>
      {% if achievement.category %}<span class="chip">{{ achievement.category }}</span>{% endif %}
      <p class="timeline-desc">{{ achievement.description | default: achievement.excerpt }}</p>
    </li>
  {% endfor %}
</ul>
{% endif %}
