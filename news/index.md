---
layout: default
title: News
permalink: /news/
---

<div class="container-xxl py-4">
  <h1 class="mb-3">News & Updates</h1>

  {% assign items = site.news | sort: "date" | reverse %}
  {% if items and items.size > 0 %}
    <ul class="news-list">
      {% for n in items %}
        <li class="news-item">
          <div class="news-head">
            <span class="news-date">{{ n.date | date: "%b %e, %Y" }}</span>
            <span class="news-title">{{ n.title }}</span>
          </div>
          {% if n.excerpt %}
            <p class="news-excerpt">{{ n.excerpt | strip_html }}</p>
          {% endif %}
          <div class="news-links">
            {% if n.link %}<a href="{{ n.link }}" target="_blank" rel="noopener">Link</a>{% endif %}
            {% if n.url and n.content != "" %}{% if n.link %} · {% endif %}<a href="{{ n.url | relative_url }}">Details</a>{% endif %}
          </div>
        </li>
      {% endfor %}
    </ul>
  {% else %}
    <p class="text-muted mb-0">No updates yet — check back soon.</p>
  {% endif %}
</div>
