---
layout: page
title: Instruments
permalink: /fr/instruments/
ref: instruments
description: Le portefeuille technologique de MECDITRINA, sur les sites de Marseille et de Nice.
nav: true
nav_order: 1
---

{% assign ui = site.data.i18n[page.lang] %}

<p class="mx-section-intro">
  Le portefeuille rassemble des techniques validées, déjà utilisées en routine dans les laboratoires partenaires. L'accès se fait soit
  par collaboration directe avec l'équipe experte, soit via les plateformes existantes. Vous ne savez pas quelle technique convient à
  votre question ? <a href="{{ '/fr/contact/' | relative_url }}#request">Envoyez-nous une demande</a> : nous vous aiderons à choisir.
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
      <h2>{% include tr.liquid obj=d key='domain' %}</h2>
      <p>{% include tr.liquid obj=d key='summary' %}</p>
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
        <h3>{% include tr.liquid obj=t key='name' %}</h3>
        <p class="mx-measures">{% include tr.liquid obj=t key='measures' %}</p>
        {% if t.equipment %}<p class="mx-equipment">{% include tr.liquid obj=t key='equipment' %}</p>{% endif %}
      </div>
    {% endfor %}
  </div>
</section>

{% endfor %}

<section class="mx-section">
  <h2>Logiciel d'analyse de données</h2>
  <p>
    Les mesures mécaniques par AFM sont analysées avec <b>PyFMLab</b>, un logiciel open source développé à DyNaMo pour l'étude de
    l'élasticité et de la viscoélasticité des échantillons biologiques
    (<a href="https://doi.org/10.12688/openreseurope.16550.2" target="_blank" rel="noopener" lang="en">Lopez-Alonso et al., Open Res Eur 2023</a>).
  </p>
</section>
