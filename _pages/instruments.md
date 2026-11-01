---
layout: page
title: Instruments
permalink: /instruments/
ref: instruments
description: The MECDITRINA technology portfolio, across the Marseille and Nice sites.
nav: true
nav_order: 1
---

{% assign ui = site.data.i18n[page.lang] %}

<p class="mx-section-intro">
  The portfolio gathers validated techniques already in routine use in the partner laboratories. Access is either through direct
  collaboration with the expert team or through the existing core facilities. Not sure which technique fits your question?
  <a href="{{ '/contact/' | relative_url }}#request">Send us a request</a>: we will help you choose.
</p>

<div class="mx-badges">
  <span class="mx-badge marseille">Marseille</span>
  <span class="mx-badge nice">Nice</span>
  <span class="mx-badge soon">{{ ui.status_deploying }}</span>
  <span class="mx-badge planned">{{ ui.status_planned }}</span>
</div>

{% for d in site.data.instruments %}

<section class="mx-domain">
  <div class="mx-domain-head">
    <span class="mx-icon {{ d.tint }}"><i class="fa-solid {{ d.icon }}"></i></span>
    <div>
      <h2>{{ d.domain }}</h2>
      <p>{{ d.summary }}</p>
    </div>
  </div>
  <div class="mx-grid">
    {% for t in d.techniques %}
      <div class="mx-card">
        <div class="mx-badges">
          {% for s in t.sites %}
            <span class="mx-badge {{ s }}">{{ s | capitalize }}</span>
          {% endfor %}
          {% if t.status == 'deploying' %}<span class="mx-badge soon">{{ ui.status_deploying }}</span>{% elsif t.status == 'planned' %}<span class="mx-badge planned">{{ ui.status_planned }}</span>{% endif %}
        </div>
        <h3>{{ t.name }}</h3>
        <p class="mx-measures">{{ t.measures }}</p>
        {% if t.equipment %}<p class="mx-equipment">{{ t.equipment }}</p>{% endif %}
      </div>
    {% endfor %}
  </div>
</section>

{% endfor %}

<section class="mx-section">
  <h2>Data analysis software</h2>
  <p>
    AFM mechanical measurements are analysed with <b>PyFMLab</b>, open-source software developed at DyNaMo for elasticity and
    viscoelasticity of biological samples
    (<a href="https://doi.org/10.12688/openreseurope.16550.2" target="_blank" rel="noopener">Lopez-Alonso et al., Open Res Eur 2023</a>).
  </p>
</section>
