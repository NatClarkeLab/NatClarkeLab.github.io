---
layout: default
title: Research
---

<div class="container-xxl py-4">
  <!-- HERO -->
  <header class="mb-4">
    <h1 class="mb-2">Research</h1>
    <p class="lead text-muted mb-0">How cells learned to stick together—questions, systems, and the tools we build to study them.</p>
  </header>

  <!-- In-page pills nav -->
  <nav class="mb-4">
    <ul class="pills">
      <li><a href="#systems">Systems & Questions</a></li>
      <li><a href="#tools">Tools & Methods</a></li>
    </ul>
  </nav>

  <!-- SYSTEMS & QUESTIONS -->
  <section id="systems" class="mb-5">
    <h2 class="h4 mb-3">Systems & Questions</h2>
    <div class="research-grid">
      {% assign systems = site.research | where: "area", "systems" | sort: "order" %}
      {% for item in systems %}
        <a class="research-card" href="{{ item.url | relative_url }}">
          <div class="research-card__img" style="background-image:url('{{ item.image }}')"></div>
          <div class="research-card__body">
            <h3 class="h5 mb-1">{{ item.title }}</h3>
            <p class="text-muted mb-0">{{ item.summary }}</p>
          </div>
        </a>
      {% endfor %}
    </div>
  </section>

  <!-- TOOLS & METHODS -->
  <section id="tools" class="mb-4">
    <h2 class="h4 mb-3">Tools & Methods</h2>
    <div class="research-grid">
      {% assign tools = site.research | where: "area", "tools" | sort: "order" %}
      {% for item in tools %}
        <a class="research-card" href="{{ item.url | relative_url }}">
          <div class="research-card__img" style="background-image:url('{{ item.image }}')"></div>
          <div class="research-card__body">
            <h3 class="h5 mb-1">{{ item.title }}</h3>
            <p class="text-muted mb-0">{{ item.summary }}</p>
          </div>
        </a>
      {% endfor %}
    </div>
  </section>
</div>
