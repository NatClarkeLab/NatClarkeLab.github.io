---
layout: default
title: Team
permalink: /team/
---

<div class="container-xxl py-4">
  <h1 class="mb-4">Team</h1>

  {% assign people = site.team | where_exp: "m", "m.status != 'alumni'" | sort: "order" %}
  {% for m in people %}
  <article class="team-row">
    <div class="team-left">
      {% if m.photo %}
        <img class="team-photo" src="{{ m.photo | relative_url }}" alt="{{ m.name }}">
      {% endif %}

      <!-- Icon row under the photo (conditionally shows what's present) -->
      <div class="team-links">
        {% if m.email %}
          <a href="mailto:{{ m.email }}" class="team-icon" aria-label="Email" title="Email">
            <i class="bi bi-envelope-fill"></i>
          </a>
        {% endif %}

        {% if m.scholar %}
          <a href="{{ m.scholar }}" class="team-icon" aria-label="Google Scholar" title="Google Scholar" target="_blank" rel="noopener">
            <img src="https://cdn.simpleicons.org/googlescholar" alt="" />
          </a>
        {% endif %}

        {% if m.bluesky %}
          <a href="{{ m.bluesky }}" class="team-icon" aria-label="Bluesky" title="Bluesky" target="_blank" rel="noopener">
            <img src="https://cdn.simpleicons.org/bluesky" alt="" />
          </a>
        {% endif %}

        {% if m.website %}
          <a href="{{ m.website }}" class="team-icon" aria-label="Website" title="Website" target="_blank" rel="noopener">
            <i class="bi bi-link-45deg"></i>
          </a>
        {% endif %}
      </div>
    </div>

    <div class="team-right">
      <h3 class="h5 mb-1">{{ m.name }}</h3>
      {% if m.role %}<p class="text-muted mb-2">{{ m.role }}</p>{% endif %}
      {% if m.bio %}<p class="mb-0">{{ m.bio }}</p>{% endif %}
    </div>
  </article>
  {% endfor %}

  {% assign alumni = site.team | where: "status", "alumni" | sort: "name" %}
  {% if alumni and alumni != empty %}
    <hr class="my-5">
    <h2 class="h5 mb-3">Alumni</h2>
    <ul class="alumni-list">
      {% for a in alumni %}
        <li>
          <strong>{{ a.name }}</strong>{% if a.role %}, {{ a.role }}{% endif %}
          {% if a.next %} — <span class="text-muted">{{ a.next }}</span>{% endif %}
        </li>
      {% endfor %}
    </ul>
  {% endif %}
</div>
