---
layout: default
title: Home
permalink: /
ref: home
description: Access to mechanobiology tools, expertise and data analysis for researchers in Provence-Alpes-Côte d'Azur.
announcements:
  limit: 3 # number of news items shown on the home page
---

<section class="mx-hero">
  {% include wordmark.liquid %}
  <p class="mx-acronym"><b>MEC</b>hanobiology <b>D</b>evices and <b>I</b>nnovative <b>T</b>ools for <b>R</b>esearch <b>IN</b> c<b>A</b>ncer</p>
  <a class="mx-funder" href="{{ site.funder.url }}" target="_blank" rel="noopener">
    <span class="mx-funder-label">Funded by</span>
    {% if site.funder.logo %}
      <img class="mx-funder-logo" src="{{ '/assets/img/' | append: site.funder.logo | relative_url }}" alt="{{ site.funder.logo_alt | default: site.funder.name }}">
    {% else %}
      <span class="mx-funder-name">{{ site.funder.name }}</span>
    {% endif %}
    <span class="mx-funder-programme">{{ site.funder.programme }}</span>
  </a>
  <h1>Exploring the mechanical forces of life</h1>
  <p class="mx-lead">
    A regional network giving researchers access to mechanobiology tools, skills and devices to measure and model
    mechanical forces in biology and soft matter, with support from expert physicists and mechanobiologists in Marseille and Nice.
  </p>
  <div class="mx-actions">
    <a class="mx-btn mx-btn-primary" href="{{ '/contact/' | relative_url }}#request"><i class="fa-solid fa-paper-plane"></i> Request access</a>
    <a class="mx-btn mx-btn-secondary" href="{{ '/instruments/' | relative_url }}">Explore the instruments</a>
  </div>
</section>

<section class="mx-section">
  <h2>A service for researchers</h2>
  <p class="mx-section-intro">
    MECDITRINA links the mechanobiology expertise already present across the region into a single entry point. You bring the
    biological question; we help you find the right technique, the right experts and the right way to analyse the data.
  </p>
  <div class="mx-grid">
    <div class="mx-card">
      <span class="mx-icon"><i class="fa-solid fa-microscope"></i></span>
      <h3>Tools and devices</h3>
      <ul>
        <li>Force measurements at different scales</li>
        <li>Adapted to diverse samples</li>
        <li>Various experimental conditions and environments</li>
      </ul>
    </div>
    <div class="mx-card">
      <span class="mx-icon lavender"><i class="fa-solid fa-user-gear"></i></span>
      <h3>Expertise and support</h3>
      <ul>
        <li>Experimental design</li>
        <li>Technical advice</li>
        <li>Help with measurements</li>
        <li>Tailored approaches and training</li>
      </ul>
    </div>
    <div class="mx-card">
      <span class="mx-icon peach"><i class="fa-solid fa-chart-line"></i></span>
      <h3>Data analysis and modelling</h3>
      <ul>
        <li>Image and force analysis</li>
        <li>Quantification</li>
        <li>Theoretical modelling</li>
        <li>Interpretation</li>
      </ul>
    </div>
  </div>
</section>

<section class="mx-section">
  <h2>A wide range of samples</h2>
  <ul class="mx-chips">
    <li><b>Proteins</b> · purified, molecular complexes</li>
    <li><b>Cells</b> · adherent, suspended, immune, stem cells</li>
    <li><b>Tissues and organs</b> · 3D organoids, ex vivo tissues</li>
    <li><b>Histology</b> · tissue sections</li>
    <li><b>Membranes</b> · model membranes, lipid rafts, cell membranes</li>
    <li><b>ECM and biomaterials</b> · hydrogels, alginate beads, 3D matrices</li>
  </ul>
</section>

<section class="mx-section">
  <h2>How it works</h2>
  <p class="mx-section-intro">One entry point for every request, whatever the technique or the site.</p>
  <ol class="mx-steps">
    <li><b>Submit your request</b><span>Describe your question and samples through the online form.</span></li>
    <li><b>We review it</b><span>The project engineer analyses each request within 2–5 working days.</span></li>
    <li><b>We connect you</b><span>You are routed to the right expert and technique, after steering-committee advice for complex projects.</span></li>
    <li><b>First data</b><span>Experiments start with the expert team, usually yielding first data within 1–3 months, with training towards autonomy.</span></li>
  </ol>
</section>

<section class="mx-section">
  <h2>Two hubs, one network</h2>
  <div class="mx-grid-2">
    <div class="mx-card">
      <div class="mx-badges"><span class="mx-badge marseille">Marseille</span></div>
      <h3>DyNaMo — Luminy campus</h3>
      <p>Quantitative biophysics, with a strong focus on atomic force microscopy: cell and tissue mechanics, high-speed AFM, single-molecule and single-cell force spectroscopy.</p>
    </div>
    <div class="mx-card">
      <div class="mx-badges"><span class="mx-badge nice">Nice</span></div>
      <h3>IRCAN — Nice</h3>
      <p>Cell-based mechanobiology: traction force microscopy, cell stretching and magnetic tweezers.</p>
    </div>
  </div>
</section>

<section class="mx-section">
  <h2>News</h2>
  {% include news-list.liquid limit=true %}
</section>

<section class="mx-section mx-callout">
  <h2>About the name</h2>
  <p>
    Mecditrina refers to Meditrina, a Roman goddess associated with healing, in line with the project's ambition to contribute
    to new approaches against cancer and other diseases. MECDITRINA is a structuring action of Canceropôle PACA (October 2026 – June 2028).
  </p>
</section>
