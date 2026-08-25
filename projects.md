---
layout: page
title: Projects
---
{% if site.projects.size == 0 %}
<div class="empty-state"><p>Projects are on the way — check back soon.</p></div>
{% else %}
<p class="page-count">{{ site.projects.size }} entries · newest first</p>
<ul class="card-grid">
  {% assign projects = site.projects | sort: 'date' | reverse %}
  {% for project in projects %}
    {% include project-card.html project=project index=forloop.index %}
  {% endfor %}
</ul>
{% endif %}
