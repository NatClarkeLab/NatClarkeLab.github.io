---
layout: default
title: Publications
permalink: /publications/
---

<div class="container-xxl py-4">
  <h1 class="mb-3">Publications</h1>

  {% assign pubs = site.publications | sort: "title" %}
  {% assign pubs = pubs | sort: "year" | reverse %}

  {% assign current_year = "" %}
  {% for p in pubs %}
    {% assign year_label = p.year | default: "Undated" %}

    {% if year_label != current_year %}
      {% unless forloop.first %}</ul>{% endunless %}
      <h2 class="h5 mt-4">{{ year_label }}</h2>
      <ul class="pub-list">
      {% assign current_year = year_label %}
    {% endif %}

    <li class="pub-item">
      <!-- Title (bold, not a link) -->
      <span class="pub-title"><strong>{{ p.title }}</strong></span>

      <!-- Authors (handles YAML list or string) -->
      {% if p.authors %}
        {% if p.authors.first and p.authors.size %}
          {% assign authors_str = p.authors | join: ", " %}
        {% else %}
          {% assign authors_str = p.authors %}
        {% endif %}
        <div class="pub-authors">{{ authors_str }}</div>
      {% endif %}

      <!-- Journal (italic) and year -->
      {% if p.journal %}
        <div class="pub-where"><em>{{ p.journal }}</em>{% if p.year %} ({{ p.year }}){% endif %}</div>
      {% endif %}

      <!-- Links row (DOI/PDF) -->
      <div class="pub-links">
        {% if p.doi %}<a href="https://doi.org/{{ p.doi }}" target="_blank" rel="noopener">DOI</a>{% endif %}
        {% if p.pdf %}{% if p.doi %} · {% endif %}<a href="{{ p.pdf | relative_url }}" target="_blank" rel="noopener">PDF</a>{% endif %}
      </div>
    </li>

    {% if forloop.last %}</ul>{% endif %}
  {% endfor %}
</div>
