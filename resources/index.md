---
layout: default
title: Resources
---

<div class="container-xxl py-4">
  <h1 class="mb-3">Resources</h1>
  <p class="text-muted">Protocols, code, onboarding, teaching assets, and tools.</p>

  <ul class="list-unstyled" style="line-height:1.7;">
    {% assign items = site.resources | sort: "title" %}
    {% for r in items %}
      <li class="mb-1">
        <a href="{{ r.link | default: r.url }}">{{ r.title }}</a>
        {% if r.summary %}<span class="text-muted"> — {{ r.summary }}</span>{% endif %}
      </li>
    {% endfor %}
  </ul>
</div>
