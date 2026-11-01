---
layout: page
title: Contact
permalink: /fr/contact/
ref: contact
description: Demander l'accès à un instrument ou à une expertise, ou simplement poser une question.
nav: true
nav_order: 5
# Leave empty to use the English contact page's values; set only for a French-specific form or address
tally_form_id:
contact_email:
---

{% comment %} Fall back to the English contact page (ref: contact, lang: en) for empty values {% endcomment %}
{% assign en_contact = site.pages | where: 'ref', 'contact' | where: 'lang', 'en' | first %}
{% assign tally_form_id = page.tally_form_id | default: en_contact.tally_form_id %}
{% assign contact_email = page.contact_email | default: en_contact.contact_email %}

<section class="mx-section" style="margin-top: 1rem">
  <h2>Comment demander un accès</h2>
  <ol class="mx-steps">
    <li><b>Remplissez le formulaire</b><span>Votre question, vos échantillons et la technique envisagée, le cas échéant.</span></li>
    <li><b>Examen sous 2 à 5 jours ouvrés</b><span>L'ingénieure de projet lit chaque demande et revient vers vous.</span></li>
    <li><b>Orientation</b><span>Les demandes simples sont orientées sous une semaine ; les demandes complexes sont examinées par le comité de pilotage (2 à 3 semaines).</span></li>
    <li><b>Démarrage</b><span>Nous vous mettons en relation avec l'équipe experte pour planifier les expériences et, si besoin, une formation.</span></li>
  </ol>
</section>

<section class="mx-section" id="request">
  <h2>Formulaire de demande</h2>
  {% if tally_form_id %}
    {% include tally-embed.liquid id=tally_form_id %}
    <p class="mx-note">
      Le formulaire ne s'affiche pas ? <a href="https://tally.so/r/{{ tally_form_id }}" target="_blank" rel="noopener">Ouvrez-le dans un nouvel onglet</a>.
      Les réponses sont stockées par Tally (Tally BV, Belgique) sur des serveurs situés dans l'UE ; Tally fait appel à des sous-traitants, dont certains hors UE. Vos données sont utilisées uniquement pour traiter votre demande ; voir nos
      <a href="{{ '/fr/mentions-legales/' | relative_url }}">mentions relatives à la protection des données</a>.
    </p>
  {% else %}
    <div class="mx-callout">
      <p><b>Le formulaire de demande en ligne ouvrira prochainement.</b> En attendant, contactez l'un des coordinateurs ci-dessous.</p>
    </div>
  {% endif %}
</section>

<section class="mx-section">
  <h2>Contacts et sites</h2>
  {% if contact_email %}
    <p>Contact général : <a href="mailto:{{ contact_email }}">{{ contact_email }}</a></p>
  {% endif %}
  <div class="mx-grid-2">
    <div class="mx-card">
      <div class="mx-badges"><span class="mx-badge marseille">Marseille</span></div>
      <h3>DyNaMo</h3>
      <p>Inserm UMR 1325, Aix-Marseille Université<br>Campus de Luminy, Marseille</p>
      <p class="mx-measures">Coordinateur : Michael Sebbagh</p>
    </div>
    <div class="mx-card">
      <div class="mx-badges"><span class="mx-badge nice">Nice</span></div>
      <h3>IRCAN</h3>
      <p>Inserm U1081 / CNRS UMR 7284, Université Côte d'Azur<br>Nice</p>
      <p class="mx-measures">Coordinateur : Etienne Boulter</p>
    </div>
  </div>
</section>
