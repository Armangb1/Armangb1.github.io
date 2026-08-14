---
layout: page
title: Achievements
---
{% if site.achievements.size == 0 %}
<p class="muted">Achievements are on the way — check back soon.</p>
{% else %}
<ul class="card-grid">
  {% assign achievements = site.achievements | sort: 'date' | reverse %}
  {% for achievement in achievements %}
  <li class="card">
    <a class="card-title" href="{{ achievement.url | relative_url }}">{{ achievement.title }}</a>
    {% if achievement.date %}<p class="entry-date">{{ achievement.date | date: "%B %Y" }}</p>{% endif %}
    <p class="card-desc">{{ achievement.description | default: achievement.excerpt }}</p>
  </li>
  {% endfor %}
</ul>
{% endif %}
