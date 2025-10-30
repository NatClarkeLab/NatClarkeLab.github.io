---
layout: default
title: Research
---

<div class="container-xxl py-4">
  <h1 class="mb-4">Research</h1>
  <div class="research-grid">
    {% assign items = site.research | sort: 'order' %}
    {% for item in items %}
    <a class="research-card" href="{{ item.url | relative_url }}" id="{{ item.title | slugify }}">
      <div class="research-card__img" style="background-image:url('{{ item.image }}')"></div>
      <div class="research-card__body">
        <h3 class="h5 mb-1">{{ item.title }}</h3>
        <p class="text-muted mb-0">{{ item.summary }}</p>
      </div>
    </a>
    {% endfor %}
  </div>
</div>
