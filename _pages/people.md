---
layout: page
title: People
permalink: /people/
ref: people
description: The teams and experts behind MECDITRINA.
nav: true
nav_order: 4
---

{% assign p = site.data.people %}

<section class="mx-section" style="margin-top: 1rem">
  <h2>Coordination</h2>
  <div class="mx-grid-2">
    {% for c in p.coordinators %}
      <div class="mx-card mx-person">
        <span class="mx-avatar">{{ c.initials }}</span>
        <div>
          <h3>{{ c.name }}</h3>
          <p><b>{{ c.role }}</b></p>
          {% if c.title %}<p class="mx-person-title">{{ c.title }}</p>{% endif %}
          <p>{{ c.affiliation }}</p>
        </div>
      </div>
    {% endfor %}
    <div class="mx-card mx-person">
      <span class="mx-avatar">{{ p.engineer.initials }}</span>
      <div>
        <h3>{{ p.engineer.name }}</h3>
        <p><b>{{ p.engineer.role }}</b></p>
        {% if p.engineer.title %}<p class="mx-person-title">{{ p.engineer.title }}</p>{% endif %}
        <p>{{ p.engineer.affiliation }}</p>
      </div>
    </div>
  </div>
</section>

<section class="mx-section">
  <h2>Steering committee</h2>
  <p class="mx-section-intro">
    Specialists of every technique in the portfolio. The committee reviews complex or interdisciplinary requests and guides how the
    portfolio evolves.
  </p>
  {% if p.steering_committee.size > 0 %}
    <ul class="mx-chips">
      {% for m in p.steering_committee %}<li>{{ m }}</li>{% endfor %}
    </ul>
  {% else %}
    <p class="mx-note">Composition to be announced.</p>
  {% endif %}
</section>

<section class="mx-section">
  <h2>Partner institutes</h2>
  <p class="mx-section-intro">More than 18 research teams across 10 institutes in Marseille, Nice and Sophia Antipolis.</p>
  <ul class="mx-list-plain">
    {% for i in p.institutes %}
      <li><b>{{ i.name }}</b> · {{ i.full }}, {{ i.city }}</li>
    {% endfor %}
  </ul>
</section>

<section class="mx-section">
  <h2>Selected references</h2>
  <ul>
    {% for r in p.references %}
      <li>{{ r.text }} <a href="https://doi.org/{{ r.doi }}" target="_blank" rel="noopener">doi:{{ r.doi }}</a></li>
    {% endfor %}
  </ul>
</section>
