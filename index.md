
---
layout: default
title: "Beranda"
description: "Berita Update Byte menyajikan informasi terbaru seputar teknologi, budaya, dan perkembangan hiburan digital."
---

<section class="welcome">
  <h1>Selamat Datang di Berita Update Byte</h1>
  <p>
    Portal informasi yang membahas perkembangan
    teknologi, budaya, tren digital, dan dunia
    hiburan modern.
  </p>
</section>

{% assign featured = site.posts.first %}

{% if featured %}
<section class="news-section">
  <h2 class="section-title">Highlight Berita</h2>

  <article class="featured-news">
    <a href="{{ featured.url | relative_url }}">
      {% if featured.image %}
      <img
        src="{{ featured.image | relative_url }}"
        alt="{{ featured.image_alt | default: featured.title | escape }}"
        width="1280"
        height="720">
      {% endif %}
    </a>

    <div class="featured-content">
      <p class="meta">
        {{ featured.date | date: "%d-%m-%Y" }}
      </p>

      <h3>
        <a href="{{ featured.url | relative_url }}">
          {{ featured.title }}
        </a>
      </h3>

      <p>{{ featured.description }}</p>

      <a class="read-more"
         href="{{ featured.url | relative_url }}">
        Baca Selengkapnya
      </a>
    </div>
  </article>
</section>
{% endif %}

<section class="news-section">
  <h2 class="section-title">Artikel Terbaru</h2>

  <div class="grid">
    {% for post in site.posts limit:9 %}
    <article class="card">

      <a href="{{ post.url | relative_url }}">
        {% if post.image %}
        <img
          src="{{ post.image | relative_url }}"
          alt="{{ post.image_alt | default: post.title | escape }}"
          loading="lazy">
        {% endif %}
      </a>

      <div class="card-body">
        <p class="meta">
          {{ post.date | date: "%d-%m-%Y" }}
        </p>

        <h3>
          <a href="{{ post.url | relative_url }}">
            {{ post.title }}
          </a>
        </h3>

        <p>{{ post.description }}</p>

        <a class="read-more"
           href="{{ post.url | relative_url }}">
          Baca Selengkapnya
        </a>
      </div>

    </article>
    {% endfor %}
  </div>
</section>

<section class="news-section">
  <h2 class="section-title">Arsip Artikel</h2>

  {% assign archives = site.posts | group_by_exp: "post", "post.date | date: '%B %Y'" %}

  <div class="archive-list">
    {% for archive in archives %}
    <div class="archive-item">
      <strong>{{ archive.name }}</strong>
      <span>{{ archive.items.size }} Artikel</span>
    </div>
    {% endfor %}
  </div>
</section>

<section class="news-section">
  <h2 class="section-title">Artikel Pilihan</h2>

  <div class="grid">
    {% assign selected = site.posts | where: "featured", true %}

    {% for post in selected limit:3 %}
    <article class="card">
      {% if post.image %}
      <a href="{{ post.url | relative_url }}">
        <img
          src="{{ post.image | relative_url }}"
          alt="{{ post.title | escape }}"
          loading="lazy">
      </a>
      {% endif %}

      <div class="card-body">
        <h3>
          <a href="{{ post.url | relative_url }}">
            {{ post.title }}
          </a>
        </h3>
        <p>{{ post.description }}</p>
      </div>
    </article>
    {% endfor %}
  </div>
</section>
