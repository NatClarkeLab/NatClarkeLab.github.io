---
layout: default
title: Resources
---

<div class="container-xxl py-4">
  <h1 class="mb-4">Resources</h1>
  <p class="text-muted">Browse lab resources: protocols, code, onboarding, and teaching assets.</p>

## Tools & Apps

- **HCR Probe Generator** — Generate split-probe oPools from a FASTA sequence.  
  👉 [Open the app]({{ '/apps/hcr/' | relative_url }})

  <div class="resources-grid">
    {% assign items = site.resources | sort: "title" %}
    {% for r in items %}
      <a class="resource-card" href="{{ r.link | default: r.url }}">
        {% if r.icon %}<img class="resource-card__icon" src="{{ r.icon }}" alt="">{% endif %}
        <h3 class="h6 mb-1">{{ r.title }}</h3>
        <p class="small text-muted mb-0">{{ r.summary }}</p>
      </a>
    {% endfor %}
  </div>
</div>
