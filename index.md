
---
layout: default
title: "Beranda"
---

# Berita Terbaru

Temukan informasi terbaru seputar teknologi,
budaya, dan hiburan digital.

<div class="grid">
{% for post in site.posts %}
  <article class="card">
    <a href="{{ post.url | relative_url }}">
      {% if post.image %}
      <img src="{{ post.image | relative_url }}"
           alt="{{ post.title | escape }}">
      {% endif %}
    </a>

    <div class="card-body">
      <p class="meta">
        {{ post.date | date: "%d %B %Y" }}
      </p>

      <h2>
        <a href="{{ post.url | relative_url }}">
          {{ post.title }}
        </a>
      </h2>

      <p>{{ post.description }}</p>
    </div>
  </article>
{% endfor %}
</div>
