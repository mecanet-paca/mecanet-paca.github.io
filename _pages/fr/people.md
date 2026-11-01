---
layout: page
title: Équipe
permalink: /fr/equipe/
ref: people
description: Les équipes et les experts de MECDITRINA.
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
          <p><b>{% include tr.liquid obj=c key='role' %}</b></p>
          {% if c.title %}<p class="mx-person-title">{% include tr.liquid obj=c key='title' %}</p>{% endif %}
          <p>{% include tr.liquid obj=c key='affiliation' %}</p>
        </div>
      </div>
    {% endfor %}
    <div class="mx-card mx-person">
      <span class="mx-avatar">{{ p.engineer.initials }}</span>
      <div>
        <h3>{{ p.engineer.name }}</h3>
        <p><b>{% include tr.liquid obj=p.engineer key='role' %}</b></p>
        {% if p.engineer.title %}<p class="mx-person-title">{% include tr.liquid obj=p.engineer key='title' %}</p>{% endif %}
        <p>{% include tr.liquid obj=p.engineer key='affiliation' %}</p>
      </div>
    </div>
  </div>
</section>

<section class="mx-section">
  <h2>Comité de pilotage</h2>
  <p class="mx-section-intro">
    Des spécialistes de chaque technique du portefeuille. Le comité examine les demandes complexes ou interdisciplinaires et oriente
    l'évolution du portefeuille.
  </p>
  {% if p.steering_committee.size > 0 %}
    <ul class="mx-chips">
      {% for m in p.steering_committee %}<li>{{ m }}</li>{% endfor %}
    </ul>
  {% else %}
    <p class="mx-note">Composition à venir.</p>
  {% endif %}
</section>

<section class="mx-section">
  <h2>Instituts partenaires</h2>
  <p class="mx-section-intro">Plus de 18 équipes de recherche réparties dans 10 instituts à Marseille, Nice et Sophia Antipolis.</p>
  <ul class="mx-list-plain">
    {% for i in p.institutes %}
      <li><b>{{ i.name }}</b> · {% include tr.liquid obj=i key='full' %}, {{ i.city }}</li>
    {% endfor %}
  </ul>
</section>

<section class="mx-section">
  <h2>Sélection de références</h2>
  <ul>
    {% for r in p.references %}
      <li lang="en">{{ r.text }} <a href="https://doi.org/{{ r.doi }}" target="_blank" rel="noopener">doi:{{ r.doi }}</a></li>
    {% endfor %}
  </ul>
</section>
