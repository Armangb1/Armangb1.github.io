---
layout: page
title: Projects
---
{% if site.projects.size == 0 %}
<p class="muted">Projects are on the way — check back soon.</p>
{% else %}
<ul class="card-grid">
  {% assign projects = site.projects | sort: 'date' | reverse %}
  {% for project in projects %}
  <li class="card">
    <a class="card-title" href="{{ project.url | relative_url }}">{{ project.title }}</a>
    <p class="card-desc">{{ project.description | default: project.excerpt }}</p>
    {% if project.tech %}
    <ul class="tag-list">
      {% for tech in project.tech %}<li class="tag">{{ tech }}</li>{% endfor %}
    </ul>
    {% endif %}
  </li>
  {% endfor %}
</ul>
{% endif %}
