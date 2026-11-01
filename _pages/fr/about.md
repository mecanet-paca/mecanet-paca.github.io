---
layout: default
title: Accueil
permalink: /fr/
ref: home
description: Accès à des outils, à de l'expertise et à l'analyse de données en mécanobiologie pour les équipes de recherche de Provence-Alpes-Côte d'Azur.
announcements:
  limit: 3 # number of news items shown on the home page
---

<section class="mx-hero">
  {% include wordmark.liquid %}
  <p class="mx-acronym" lang="en"><b>MEC</b>hanobiology <b>D</b>evices and <b>I</b>nnovative <b>T</b>ools for <b>R</b>esearch <b>IN</b> c<b>A</b>ncer</p>
  <a class="mx-funder" href="{{ site.funder.url }}" target="_blank" rel="noopener">
    <span class="mx-funder-label">Financé par</span>
    {% if site.funder.logo %}
      <img class="mx-funder-logo" src="{{ '/assets/img/' | append: site.funder.logo | relative_url }}" alt="{{ site.funder.logo_alt | default: site.funder.name }}">
    {% else %}
      <span class="mx-funder-name">{{ site.funder.name }}</span>
    {% endif %}
    <span class="mx-funder-programme">{{ site.funder.programme }}</span>
  </a>
  <h1>Explorer les forces mécaniques du vivant</h1>
  <p class="mx-lead">
    Un réseau régional qui donne aux équipes de recherche accès à des outils, des compétences et des dispositifs de mécanobiologie
    pour mesurer et modéliser les forces mécaniques en biologie et en matière molle, avec l'appui de physiciens et de
    mécanobiologistes experts à Marseille et à Nice.
  </p>
  <div class="mx-actions">
    <a class="mx-btn mx-btn-primary" href="{{ '/fr/contact/' | relative_url }}#request"><i class="fa-solid fa-paper-plane"></i> Demander un accès</a>
    <a class="mx-btn mx-btn-secondary" href="{{ '/fr/instruments/' | relative_url }}">Découvrir les instruments</a>
  </div>
</section>

<section class="mx-section">
  <h2>Un service pour la recherche</h2>
  <p class="mx-section-intro">
    MECDITRINA réunit en un point d'entrée unique l'expertise en mécanobiologie déjà présente dans la région. Vous apportez la
    question biologique ; nous vous aidons à trouver la bonne technique, les bons experts et la bonne façon d'analyser les données.
  </p>
  <div class="mx-grid">
    <div class="mx-card">
      <span class="mx-icon"><i class="fa-solid fa-microscope"></i></span>
      <h3>Outils et dispositifs</h3>
      <ul>
        <li>Mesures de forces à différentes échelles</li>
        <li>Adaptés à des échantillons variés</li>
        <li>Conditions expérimentales et environnements variés</li>
      </ul>
    </div>
    <div class="mx-card">
      <span class="mx-icon lavender"><i class="fa-solid fa-user-gear"></i></span>
      <h3>Expertise et accompagnement</h3>
      <ul>
        <li>Conception expérimentale</li>
        <li>Conseil technique</li>
        <li>Aide aux mesures</li>
        <li>Approches sur mesure et formation</li>
      </ul>
    </div>
    <div class="mx-card">
      <span class="mx-icon peach"><i class="fa-solid fa-chart-line"></i></span>
      <h3>Analyse de données et modélisation</h3>
      <ul>
        <li>Analyse d'images et de forces</li>
        <li>Quantification</li>
        <li>Modélisation théorique</li>
        <li>Interprétation</li>
      </ul>
    </div>
  </div>
</section>

<section class="mx-section">
  <h2>Une grande diversité d'échantillons</h2>
  <ul class="mx-chips">
    <li><b>Protéines</b> · purifiées, complexes moléculaires</li>
    <li><b>Cellules</b> · adhérentes, en suspension, immunitaires, souches</li>
    <li><b>Tissus et organes</b> · organoïdes 3D, tissus ex vivo</li>
    <li><b>Histologie</b> · coupes de tissus</li>
    <li><b>Membranes</b> · membranes modèles, radeaux lipidiques, membranes cellulaires</li>
    <li><b>MEC et biomatériaux</b> · hydrogels, billes d'alginate, matrices 3D</li>
  </ul>
</section>

<section class="mx-section">
  <h2>Fonctionnement</h2>
  <p class="mx-section-intro">Un point d'entrée unique pour toutes les demandes, quels que soient la technique ou le site.</p>
  <ol class="mx-steps">
    <li><b>Soumettez votre demande</b><span>Décrivez votre question et vos échantillons via le formulaire en ligne.</span></li>
    <li><b>Nous l'examinons</b><span>L'ingénieure de projet analyse chaque demande sous 2 à 5 jours ouvrés.</span></li>
    <li><b>Nous vous orientons</b><span>Votre demande est orientée vers l'expert et la technique adaptés, après avis du comité de pilotage pour les projets complexes.</span></li>
    <li><b>Premières données</b><span>Les expériences démarrent avec l'équipe experte et donnent généralement de premières données en 1 à 3 mois, avec une formation vers l'autonomie.</span></li>
  </ol>
</section>

<section class="mx-section">
  <h2>Deux sites, un réseau</h2>
  <div class="mx-grid-2">
    <div class="mx-card">
      <div class="mx-badges"><span class="mx-badge marseille">Marseille</span></div>
      <h3>DyNaMo — campus de Luminy</h3>
      <p>Biophysique quantitative, avec une forte spécialisation en microscopie à force atomique : mécanique des cellules et des tissus, AFM haute vitesse, spectroscopie de force sur molécule unique et sur cellule unique.</p>
    </div>
    <div class="mx-card">
      <div class="mx-badges"><span class="mx-badge nice">Nice</span></div>
      <h3>IRCAN — Nice</h3>
      <p>Mécanobiologie cellulaire : microscopie à force de traction, étirement cellulaire et pinces magnétiques.</p>
    </div>
  </div>
</section>

<section class="mx-section">
  <h2>Actualités</h2>
  {% include news-list.liquid limit=true %}
</section>

<section class="mx-section mx-callout">
  <h2>À propos du nom</h2>
  <p>
    Mecditrina fait référence à Meditrina, déesse romaine associée à la guérison, en écho à l'ambition du projet de contribuer à
    de nouvelles approches contre le cancer et d'autres maladies. MECDITRINA est une action structurante du Canceropôle PACA
    (octobre 2026 – juin 2028).
  </p>
</section>
