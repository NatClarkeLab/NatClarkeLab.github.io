---
layout: default
title: Research
---

<div class="container-xxl py-4">
  <header class="mb-4">
    <h1 class="mb-2">Research</h1>
    <p class="lead text-muted mb-0">We are broadly interested in cell adhesion mechanisms, and how they contribute to animal evolution and organismal complexity. These are a few of our current projects: </p>
  </header>

  <div class="research-list">
    {% assign items = site.research | sort: "order" %}
    {% if items == empty %}
      {% assign items = site.research | sort: "title" %}
    {% endif %}

    {% for item in items %}
    <article id="{{ item.title | slugify }}" class="research-item">
      {% if item.image %}
        <img class="research-thumb" src="{{ item.image | relative_url }}" alt="">
      {% endif %}
      <div class="research-body">
        <h3 class="h5 mb-1">{{ item.title }}</h3>
        {% if item.summary %}<p class="text-muted mb-2">{{ item.summary }}</p>{% endif %}
        {{ item.content }}
      </div>
    </article>
    {% endfor %}
  </div>
</div>
