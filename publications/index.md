---
layout: default
title: Publications
permalink: /publications/
---

<div class="container-xxl py-4">
  <h1 class="mb-3">Publications</h1>

  {%- comment -%}
  Collect pubs and detect if any footnote markers are present so we can show a legend.
  {%- endcomment -%}
  {% assign pubs = site.publications | sort: "title" %}
  {% assign pubs = pubs | sort: "year" | reverse %}

  {% assign has_star = "" %}
  {% assign has_dagger = "" %}
  {% for p in pubs %}
    {% if p.authors %}
      {% if p.authors.first and p.authors.size %}
        {% assign _a = p.authors | join: ", " %}
      {% else %}
        {% assign _a = p.authors %}
      {% endif %}
      {% if _a contains "*" %}{% assign has_star = "true" %}{% endif %}
      {% if _a contains "†" or _a contains "^" %}{% assign has_dagger = "true" %}{% endif %}
    {% endif %}
  {% endfor %}

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

      <!-- Authors: join list; convert ^ -> †, then superscript markers -->
      {% if p.authors %}
        {% if p.authors.first and p.authors.size %}
          {% assign authors_str = p.authors | join: ", " %}
        {% else %}
          {% assign authors_str = p.authors %}
        {% endif %}
        {% assign authors_str = authors_str | replace: "^", "†" %}
        {% assign authors_str = authors_str | replace: "†", "<sup>†</sup>" %}
        {% assign authors_str = authors_str | replace: "*", "<sup>*</sup>" %}
        <div class="pub-authors">{{ authors_str }}</div>
      {% endif %}

      <!-- Journal (italic) and year -->
      {% if p.journal %}
        <div class="pub-where"><em>{{ p.journal }}</em>{% if p.year %} ({{ p.year }}){% endif %}</div>
      {% endif %}

      <!-- Optional abstract (body content) -->
      {% if p.content and p.content != "" %}
        <details class="pub-abs">
          <summary>Abstract</summary>
          <div class="pub-abstract">
            {{ p.content }}
          </div>
        </details>
      {% endif %}

      <!-- Links row -->
      <div class="pub-links">
        {% if p.doi %}<a href="https://doi.org/{{ p.doi }}" target="_blank" rel="noopener">DOI</a>{% endif %}
        {% if p.pdf %}{% if p.doi %} · {% endif %}<a href="{{ p.pdf | relative_url }}" target="_blank" rel="noopener">PDF</a>{% endif %}
      </div>
    </li>

    {% if forloop.last %}</ul>{% endif %}
  {% endfor %}

  {%- comment -%}
  Footnote legend: only show if any marker was detected.
  {%- endcomment -%}
  {% if has_star == "true" or has_dagger == "true" %}
    <hr class="my-4">
    <p class="pub-footnote small text-muted mb-0">
      {% if has_star == "true" %}<span><sup>*</sup> denotes equal author contribution</span>{% endif %}
      {% if has_star == "true" and has_dagger == "true" %} &nbsp;•&nbsp; {% endif %}
      {% if has_dagger == "true" %}<span><sup>†</sup> undergraduate co-author</span>{% endif %}
    </p>
  {% endif %}
</div>
