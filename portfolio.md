---
layout: default
title: Portfolio
permalink: /portfolio/
---

{% assign profile = site.data.profile %}

<div class="hero hero--portfolio">
  <p class="hero__kicker">Portfolio</p>
  <h1 class="hero__title">Indie apps &amp; projects</h1>
  <p class="hero__lead">
    A curated snapshot of what I build: practical tools, clean UX, and clear privacy pages.
  </p>
  <div class="hero__actions">
    <a class="btn btn--primary" href="{{ '/' | relative_url }}">Apps</a>
    <a class="btn btn--ghost" href="{{ '/about/' | relative_url }}">About</a>
    {% if profile.github_username %}
      <a class="btn btn--ghost" href="https://github.com/{{ profile.github_username }}" target="_blank" rel="noopener noreferrer">GitHub</a>
    {% endif %}
  </div>
</div>

<section class="section">
  <div class="section__header">
    <h2 class="section__title">Bio</h2>
    <p class="section__sub">A quick intro, plus where to find my work.</p>
  </div>

  <div class="profile">
    <div class="profile__main">
      <h3 class="profile__name">{{ profile.name | default: '—' }}</h3>
      {% if profile.headline %}
        <p class="profile__headline">{{ profile.headline }}</p>
      {% endif %}
      {% if profile.bio %}
        <p class="profile__bio">{{ profile.bio }}</p>
      {% endif %}
    </div>

    <div class="profile__side" aria-label="Links">
      {% if profile.location and profile.location != "" %}
        <div class="profile__row">
          <span class="profile__label">Location</span>
          <span class="profile__value">{{ profile.location }}</span>
        </div>
      {% endif %}

      {% if profile.github_username %}
        <div class="profile__row">
          <span class="profile__label">GitHub</span>
          <a class="profile__value profile__link" href="https://github.com/{{ profile.github_username }}" target="_blank" rel="noopener noreferrer">@{{ profile.github_username }}</a>
        </div>
      {% endif %}
    </div>
  </div>
</section>

<section class="section">
  <div class="section__header">
    <h2 class="section__title">Skills</h2>
    <p class="section__sub">The stack I use most often.</p>
  </div>

  {% assign skills = site.data.skills | default: empty %}
  {% if skills and skills.size > 0 %}
    <div class="skill-grid" role="list">
      {% for s in skills %}
        <div class="skill-card" role="listitem">
          <h3 class="skill-card__title">{{ s.group }}</h3>
          {% if s.items and s.items.size > 0 %}
            <div class="tag-row" aria-label="Skills">
              {% for item in s.items %}
                <span class="tag tag--skill">{{ item }}</span>
              {% endfor %}
            </div>
          {% endif %}
        </div>
      {% endfor %}
    </div>
  {% else %}
    <div class="empty-state">
      <p class="empty-state__title">No skills yet</p>
      <p class="empty-state__body">
        Add items in <code>_data/skills.yml</code> to populate this section.
      </p>
    </div>
  {% endif %}
</section>

<section class="section">
  <div class="section__header">
    <h2 class="section__title">Featured</h2>
    <p class="section__sub">Quick links to the main public pages for each app.</p>
  </div>

  {% assign projects = site.data.projects | default: empty %}
  {% if projects and projects.size > 0 %}
    <div class="project-grid" role="list">
      {% for p in projects %}
        <a class="project-card" role="listitem" href="{{ p.href | relative_url }}">
          <div class="project-card__top">
            <span class="project-card__kind">{{ p.kind }}</span>
            <span class="project-card__arrow" aria-hidden="true">↗</span>
          </div>
          <h3 class="project-card__title">{{ p.title }}</h3>
          <p class="project-card__blurb">{{ p.blurb }}</p>
          {% if p.tags and p.tags.size > 0 %}
            <div class="tag-row" aria-label="Tags">
              {% for t in p.tags %}
                <span class="tag">{{ t }}</span>
              {% endfor %}
            </div>
          {% endif %}
        </a>
      {% endfor %}
    </div>
  {% else %}
    <div class="empty-state">
      <p class="empty-state__title">No projects yet</p>
      <p class="empty-state__body">
        Add items in <code>_data/projects.yml</code> to populate this section.
      </p>
    </div>
  {% endif %}
</section>

<section class="section section--split">
  <div class="note">
    <h2 class="section__title">What you’ll find here</h2>
    <ul class="checklist">
      <li>Project cards with short blurbs</li>
      <li>Direct links to app pages and policies</li>
      <li>A single place to share your work</li>
    </ul>
  </div>

  <div class="note note--muted">
    <h2 class="section__title">Want this to be more “portfolio”?</h2>
    <p class="section__sub">
      Tell me what sections you want (skills, timeline, screenshots, App Store links, GitHub, contact) and I’ll tailor it.
    </p>
  </div>
</section>
