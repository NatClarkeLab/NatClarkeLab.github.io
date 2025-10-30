---
layout: default
title: Members
---

<div class="container-xxl py-4">
  <h1 class="mb-4">Lab Members</h1>
  <div class="row row-cols-1 row-cols-sm-2 row-cols-lg-3 g-4">
    {% assign people = site.members | sort: 'order' %}
    {% for m in people %}
    <div class="col">
      <div class="card h-100">
        {% if m.photo %}<img class="card-img-top" src="{{ m.photo }}" alt="{{ m.name }}" loading="lazy">{% endif %}
        <div class="card-body">
          <h3 class="h5 mb-1">{{ m.name }}</h3>
          <p class="text-muted mb-2">{{ m.role }}</p>
          {% if m.email %}<a href="mailto:{{ m.email }}" class="card-link">Email</a>{% endif %}
          {% if m.website %}<a href="{{ m.website }}" class="card-link">Website</a>{% endif %}
        </div>
      </div>
    </div>
    {% endfor %}
  </div>
</div>
