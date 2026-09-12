---
layout: page
title: About
---
<div class="about-grid">
  <div class="about-main">
    <p>{{ site.data.profile.bio }}</p>

    <div class="btn-row">
      <a class="btn btn-secondary" href="{{ '/contact/' | relative_url }}">Get in touch</a>
      {% if site.data.profile.contact.scholar %}
      <a class="btn btn-secondary" href="{{ site.data.profile.contact.scholar }}" target="_blank" rel="noopener">Google Scholar ↗</a>
      {% endif %}
    </div>
  </div>

  <aside class="about-rail">
    <p class="eyebrow"><span class="eyebrow-index">§</span>Education</p>
    {% for edu in site.data.profile.education %}
    <div class="edu-card">
      <h2 class="edu-degree">{{ edu.degree }}</h2>
      <p class="edu-school">{{ edu.institution }}</p>
      <p class="edu-years">{{ edu.years }}</p>
      <ul class="edu-facts">
        {% if edu.gpa %}<li><span class="fact-label">GPA</span>{{ edu.gpa }}</li>{% endif %}
        {% if edu.supervisor %}<li><span class="fact-label">Supervisor</span>{{ edu.supervisor }}</li>{% endif %}
        {% if edu.thesis_title %}<li><span class="fact-label">Thesis</span>{{ edu.thesis_title }}</li>{% endif %}
        {% if edu.project_title %}<li><span class="fact-label">Project</span>{{ edu.project_title }}</li>{% endif %}
      </ul>
    </div>
    {% endfor %}
  </aside>
</div>

<section class="section">
  <p class="eyebrow"><span class="eyebrow-index">¶</span>Experience</p>
  <h2>Research Experience</h2>
  <ul class="plain-list">
    {% for exp in site.data.profile.experience %}
    <li class="experience-item">
      <div class="experience-role">{{ exp.role }}</div>
      <div class="experience-lab">{{ exp.lab }} · {{ exp.institution }}</div>
      <div class="experience-meta">{{ exp.dates }}</div>
      <ul class="exp-points">
        {% assign raw_lines = exp.description | newline_to_br | split: '<br />' %}
        {% for line in raw_lines %}
          {% assign l = line | strip %}
          {% if l != '' %}
            {% assign first_two = l | slice: 0, 2 %}
            {% if first_two == '- ' %}{% assign l = l | remove_first: '- ' %}{% endif %}
            <li>{{ l }}</li>
          {% endif %}
        {% endfor %}
      </ul>
      {% if exp.publications %}
      <div class="experience-publications">
        <p class="pub-block-title">Publications</p>
        <ul class="pub-list">
          {% for pub in exp.publications %}
          <li><em>{{ pub.title }}</em>, {{ pub.venue }}, {{ pub.year }}</li>
          {% endfor %}
        </ul>
      </div>
      {% endif %}
      {% if exp.tags %}
      <ul class="tag-list experience-tags">
        {% for tag in exp.tags %}
        <li class="tag">{{ tag }}</li>
        {% endfor %}
      </ul>
      {% endif %}
    </li>
    {% endfor %}
  </ul>
</section>

<section class="section">
  <p class="eyebrow"><span class="eyebrow-index">†</span>Teaching</p>
  <h2>Teaching Experience</h2>
  {% if site.data.profile.teaching_experience %}
  <ul class="card-grid">
    {% for ta in site.data.profile.teaching_experience %}
    <li class="card ta-card">
      <div class="card-meta">
        <span>{{ ta.term }}</span>
      </div>
      <h3 class="card-title">{{ ta.course }}</h3>
      <p class="ta-professor">{{ ta.professor }}</p>
    </li>
    {% endfor %}
  </ul>
  {% endif %}
</section>
