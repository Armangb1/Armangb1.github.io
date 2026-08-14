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
