---
layout: default
title: Publications
permalink: /publications/
---

<div class="container-xxl py-4">
  <h1 class="mb-3">Publications</h1>

  {% comment %}
    Collect and sort: we sort by year (desc), then by title (asc) inside the year.
    If some items lack year, they’ll be grouped under "Undated".
  {% endcomment %}
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
      {%- comment -%}
        Title link preference: DOI first, else page URL.
      {%- endcomment -%}
      {% if p.doi %}
        <a class="pub-title" href="https://doi.org/{{ p.doi }}" target="_blank" rel="noopener">{{ p.title }}</a>
      {% else %}
        <a class="pub-title" href="{{ p.url | relative_url }}">{{ p.title }}</a>
      {% endif %}

      {%- comment -%}
        Authors: in your old files, authors is a YAML list:
          authors:
            - Name 1
            - Name 2
        We join with ", ". If someone stored a single string, we just print it.
      {%- endcomment -%}
      {% if p.authors %}
        {% if p.authors.first and p.authors.size %}
          {% assign authors_str = p.authors | join: ", " %}
        {% else %}
          {% assign authors_str = p.authors %}
        {% endif %}
        <div class="pub-authors">{{ authors_str }}</div>
      {% endif %}

      {%- comment -%}
        Journal and year line (journal italicized).
      {%- endcomment -%}
      {% if p.journal %}
        <div class="pub-where"><em>{{ p.journal }}</em>{% if p.year %} ({{ p.year }}){% endif %}</div>
      {% endif %}

      {%- comment -%}
        Tiny links row: DOI and PDF (if you later add "pdf:" to front matter).
      {%- endcomment -%}
      <div class="pub-links">
        {% if p.doi %}<a href="https://doi.org/{{ p.doi }}" target="_blank" rel="noopener">DOI</a>{% endif %}
        {% if p.pdf %} · <a href="{{ p.pdf | relative_url }}" target="_blank" rel="noopener">PDF</a>{% endif %}
      </div>
    </li>

    {% if forloop.last %}</ul>{% endif %}
  {% endfor %}
</div>

