---
layout: default
title: Publications
---

<div class="container-xxl py-4">
  <h1 class="mb-4">Publications</h1>
  <ul class="list-unstyled">
    {% assign pubs = site.publications | sort: 'year' | reverse %}
    {% for p in pubs %}
      <li class="mb-3">
        <strong>{{ p.title }}</strong><br>
        <em>{{ p.authors }}</em> ({{ p.year }}) — {{ p.journal }}
        {% if p.doi %} • <a href="https://doi.org/{{ p.doi }}">doi:{{ p.doi }}</a>{% endif %}
        {% if p.pdf %} • <a href="{{ p.pdf }}">PDF</a>{% endif %}
      </li>
    {% endfor %}
  </ul>
</div>
