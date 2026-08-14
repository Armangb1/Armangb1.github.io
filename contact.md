---
layout: page
title: Contact
---
<p class="lead">Open to collaborations, research opportunities, and conversations — pick whichever channel works for you.</p>

<div class="contact-grid">
  {% for email in site.data.profile.contact.emails %}
  <a class="contact-card" href="mailto:{{ email }}">
    <svg class="contact-icon" viewBox="0 0 16 16" fill="currentColor" aria-hidden="true">
      <path d="M1.75 3h12.5c.966 0 1.75.784 1.75 1.75v9.5A1.75 1.75 0 0 1 14.25 16H1.75A1.75 1.75 0 0 1 0 14.25v-9.5C0 3.784.784 3 1.75 3zM1.5 12.06V14.25c0 .138.112.25.25.25h12.5a.25.25 0 0 0 .25-.25v-2.19l-3.94-3.94-1.99 1.99a.75.75 0 0 1-1.06 0L5.44 7.87l-3.94 3.94zm0-1.94l3.25-3.25 2.31 2.31a.75.75 0 0 1 1.06 0l2.31-2.31 3.25 3.25V3.75a.25.25 0 0 0-.25-.25H1.75a.25.25 0 0 0-.25.25v6.37z"/>
    </svg>
    <span class="contact-body">
      <span class="contact-label">Email</span>
      <span class="contact-value">{{ email }}</span>
    </span>
  </a>
  {% endfor %}

  <a class="contact-card" href="{{ site.data.profile.contact.github }}" target="_blank" rel="noopener">
    <svg class="contact-icon" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
      <path d="M12 .297c-6.63 0-12 5.373-12 12 0 5.303 3.438 9.8 8.205 11.385.6.113.82-.258.82-.577 0-.285-.01-1.04-.015-2.04-3.338.724-4.042-1.61-4.042-1.61C4.422 18.07 3.633 17.7 3.633 17.7c-1.087-.744.084-.729.084-.729 1.205.084 1.838 1.236 1.838 1.236 1.07 1.835 2.809 1.305 3.495.998.108-.776.417-1.305.76-1.605-2.665-.3-5.466-1.332-5.466-5.93 0-1.31.465-2.38 1.235-3.22-.135-.303-.54-1.523.105-3.176 0 0 1.005-.322 3.3 1.23.96-.267 1.98-.399 3-.405 1.02.006 2.04.138 3 .405 2.28-1.552 3.285-1.23 3.285-1.23.645 1.653.24 2.873.12 3.176.765.84 1.23 1.91 1.23 3.22 0 4.61-2.805 5.625-5.475 5.92.42.36.81 1.096.81 2.22 0 1.606-.015 2.896-.015 3.286 0 .315.21.69.825.57C20.565 22.092 24 17.592 24 12.297c0-6.627-5.373-12-12-12"/>
    </svg>
    <span class="contact-body">
      <span class="contact-label">GitHub</span>
      <span class="contact-value">{{ site.data.profile.contact.github | remove: 'https://' }}</span>
    </span>
  </a>

  <a class="contact-card" href="{{ site.data.profile.contact.linkedin }}" target="_blank" rel="noopener">
    <svg class="contact-icon" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
      <path d="M20.447 20.452h-3.554v-5.569c0-1.328-.027-3.037-1.852-3.037-1.853 0-2.136 1.445-2.136 2.939v5.667H9.351V9h3.414v1.561h.046c.477-.9 1.637-1.85 3.37-1.85 3.601 0 4.267 2.37 4.267 5.455v6.286zM5.337 7.433c-1.144 0-2.063-.926-2.063-2.065 0-1.138.92-2.063 2.063-2.063 1.14 0 2.064.925 2.064 2.063 0 1.139-.925 2.065-2.064 2.065zm1.782 13.019H3.555V9h3.564v11.452zM22.225 0H1.771C.792 0 0 .774 0 1.729v20.542C0 23.227.792 24 1.771 24h20.451C23.2 24 24 23.227 24 22.271V1.729C24 .774 23.2 0 22.225 0z"/>
    </svg>
    <span class="contact-body">
      <span class="contact-label">LinkedIn</span>
      <span class="contact-value">{{ site.data.profile.contact.linkedin | remove: 'https://' }}</span>
    </span>
  </a>

  {% if site.data.profile.contact.scholar %}
  <a class="contact-card" href="{{ site.data.profile.contact.scholar }}" target="_blank" rel="noopener">
    <svg class="contact-icon" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
      <path d="M5.242 13.769L0 9.5 12 0l12 9.5-5.242 4.269-3.258-2.653L12 8.553l-3.5 2.563-3.258 2.653zm10.435 3.033l1.666-1.356 6.657 5.417-5.166 4.244L12 23.333l-6.834 2.73L0 21.772l6.657-5.417 1.666 1.356-3.75 3.053 4.958 2.1L12 21.684l2.469 1.18 4.958-2.1-3.75-3.052z"/>
    </svg>
    <span class="contact-body">
      <span class="contact-label">Google Scholar</span>
      <span class="contact-value">{{ site.data.profile.contact.scholar | remove: 'https://' }}</span>
    </span>
  </a>
  {% endif %}
</div>
