---
layout: page
title: Contact
permalink: /contact/
ref: contact
description: Request access to an instrument or to expertise, or simply ask a question.
nav: true
nav_order: 5
# Tally form ID: the last part of the form's share link (https://tally.so/r/XXXXXX → XXXXXX)
tally_form_id: 44WVjk
# Shared contact address shown on this page
contact_email: # functional mailbox, once created
---

<section class="mx-section" style="margin-top: 1rem">
  <h2>How to request access</h2>
  <ol class="mx-steps">
    <li><b>Fill in the form</b><span>Your question, your samples and the technique you have in mind, if any.</span></li>
    <li><b>Review within 2–5 working days</b><span>The project engineer reads every request and comes back to you.</span></li>
    <li><b>Routing</b><span>Simple requests are routed within a week; complex ones are discussed by the steering committee (2–3 weeks).</span></li>
    <li><b>Start</b><span>You are put in touch with the expert team to plan the experiments and, if relevant, training.</span></li>
  </ol>
</section>

<section class="mx-section" id="request">
  <h2>Request form</h2>
  {% if page.tally_form_id %}
    {% include tally-embed.liquid id=page.tally_form_id %}
    <p class="mx-note">
      Form not displaying? <a href="https://tally.so/r/{{ page.tally_form_id }}" target="_blank" rel="noopener">Open it in a new tab</a>.
      Submissions are stored by Tally (Tally BV, Belgium) on servers in the EU; Tally uses subprocessors, some outside the EU. Your data is used only to process your request; see our
      <a href="{{ '/legal/' | relative_url }}">data protection notice</a>.
    </p>
  {% else %}
    <div class="mx-callout">
      <p><b>The online request form opens soon.</b> In the meantime, please contact one of the coordinators below.</p>
    </div>
  {% endif %}
</section>

<section class="mx-section">
  <h2>Contacts and locations</h2>
  {% if page.contact_email %}
    <p>General contact: <a href="mailto:{{ page.contact_email }}">{{ page.contact_email }}</a></p>
  {% endif %}
  <div class="mx-grid-2">
    <div class="mx-card">
      <div class="mx-badges"><span class="mx-badge marseille">Marseille</span></div>
      <h3>DyNaMo</h3>
      <p>Inserm UMR 1325, Aix-Marseille University<br>Luminy campus, Marseille</p>
      <p class="mx-measures">Coordinator: Michael Sebbagh</p>
    </div>
    <div class="mx-card">
      <div class="mx-badges"><span class="mx-badge nice">Nice</span></div>
      <h3>IRCAN</h3>
      <p>Inserm U1081 / CNRS UMR 7284, Université Côte d'Azur<br>Nice</p>
      <p class="mx-measures">Coordinator: Etienne Boulter</p>
    </div>
  </div>
</section>
