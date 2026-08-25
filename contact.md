---
layout: page
title: Contact
---
<p class="section-intro">Open to collaborations, research opportunities, and conversations — pick whichever channel works for you.</p>

<div class="contact-primary">
  <div>
    <p class="contact-primary-label">Primary email</p>
    <p class="contact-primary-address">
      <a href="mailto:{{ site.data.profile.contact.emails.first }}">{{ site.data.profile.contact.emails.first }}</a>
    </p>
  </div>
  <div class="contact-primary-side">
    <button class="copy-btn" type="button" data-copy="{{ site.data.profile.contact.emails.first }}" aria-live="polite">Copy address</button>
  </div>
</div>

<ul class="channel-grid">
  {% assign primary = site.data.profile.contact.emails.first %}
  {% for email in site.data.profile.contact.emails %}
    {% if email != primary %}
    <li>
      <a class="channel-card" href="mailto:{{ email }}">
        <span class="channel-icon">{% include icon-email.html %}</span>
        <span class="channel-body">
          <span class="channel-label">Alternate email</span>
          <span class="channel-value">{{ email }}</span>
        </span>
      </a>
    </li>
    {% endif %}
  {% endfor %}

  <li>
    <a class="channel-card" href="{{ site.data.profile.contact.github }}" target="_blank" rel="noopener">
      <span class="channel-icon">{% include icon-github.html %}</span>
      <span class="channel-body">
        <span class="channel-label">GitHub</span>
        <span class="channel-value">@{{ site.data.profile.contact.github | split: '/' | last }}</span>
      </span>
    </a>
  </li>

  <li>
    <a class="channel-card" href="{{ site.data.profile.contact.linkedin }}" target="_blank" rel="noopener">
      <span class="channel-icon">{% include icon-linkedin.html %}</span>
      <span class="channel-body">
        <span class="channel-label">LinkedIn</span>
        <span class="channel-value">@{{ site.data.profile.contact.linkedin | split: '/' | last }}</span>
      </span>
    </a>
  </li>

  {% if site.data.profile.contact.scholar %}
  <li>
    <a class="channel-card" href="{{ site.data.profile.contact.scholar }}" target="_blank" rel="noopener">
      <span class="channel-icon">{% include icon-scholar.html %}</span>
      <span class="channel-body">
        <span class="channel-label">Google Scholar</span>
        <span class="channel-value">scholar.google.com ↗</span>
      </span>
    </a>
  </li>
  {% endif %}
</ul>

<script>
  document.querySelectorAll('.copy-btn').forEach(function (btn) {
    var original = btn.textContent;
    btn.addEventListener('click', function () {
      var text = btn.getAttribute('data-copy');
      if (navigator.clipboard && navigator.clipboard.writeText) {
        navigator.clipboard.writeText(text).then(function () {
          btn.textContent = 'Copied ✓';
          setTimeout(function () { btn.textContent = original; }, 2000);
        });
      }
    });
  });
</script>
