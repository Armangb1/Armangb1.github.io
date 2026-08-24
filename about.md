---
layout: page
title: About
---
<p>{{ site.data.profile.bio }}</p>

<h2>Education</h2>
<ul class="plain-list">
  {% for edu in site.data.profile.education %}
  <li class="education-item">
    <div class="education-degree">{{ edu.degree }}</div>
    <div class="education-meta">
      {{ edu.institution }} · <span class="muted">{{ edu.years }}</span>
    </div>
    {% if edu.gpa %}
    <div class="education-detail">
      <span class="detail-label">GPA</span>{{ edu.gpa }}
    </div>
    {% endif %}
    {% if edu.supervisor %}
    <div class="education-detail">
      <span class="detail-label">Supervisor</span>{{ edu.supervisor }}
    </div>
    {% endif %}
    {% if edu.thesis_title %}
    <div class="education-detail">
      <span class="detail-label">Thesis</span>{{ edu.thesis_title }}
    </div>
    {% endif %}
    {% if edu.project_title %}
    <div class="education-detail">
      <span class="detail-label">Project</span>{{ edu.project_title }}
    </div>
    {% endif %}
  </li>
  {% endfor %}
</ul>

<p><a class="text-link" href="{{ '/contact/' | relative_url }}">Get in touch →</a></p>

<h2>Research Experience</h2>
<ul class="plain-list">
  {% for exp in site.data.profile.experience %}
  <li class="experience-item">
    <div class="experience-header">
      <div class="experience-role">{{ exp.role }}</div>
      <div class="experience-lab">{{ exp.lab }}</div>
    </div>
    <div class="experience-meta">
      {{ exp.institution }} · <span class="muted">{{ exp.dates }}</span>
    </div>
    <div class="experience-desc">{{ exp.description }}</div>
    {% if exp.publications %}
    <div class="experience-publications">
      <strong>Publications:</strong>
      <ul class="pub-list">
        {% for pub in exp.publications %}
        <li><em>{{ pub.title }}</em>, {{ pub.venue }}, {{ pub.year }}</li>
        {% endfor %}
      </ul>
    </div>
    {% endif %}
    {% if exp.tags %}
    <ul class="tag-list">
      {% for tag in exp.tags %}
      <li class="tag">{{ tag }}</li>
      {% endfor %}
    </ul>
    {% endif %}
  </li>
  {% endfor %}
</ul>
