---
layout: page
title: Mentions légales
permalink: /fr/mentions-legales/
ref: legal
description: Mentions légales et traitement des données envoyées via ce site.
---

## Éditeur

Ce site est édité par les coordinateurs de MECDITRINA, action structurante financée par le Canceropôle PACA.

Directeurs de la publication, coordinateurs de MECDITRINA :

- Etienne Boulter, IRCAN (Inserm U1081 / CNRS UMR 7284, Université Côte d'Azur), Faculté de Médecine, 28 avenue de Valombrose, 06107 Nice Cedex 2, France.
- Michael Sebbagh, DyNaMo U1325, Inserm & Aix-Marseille Université, Bâtiment Inserm TPR2 bloc 5, Case 909, 163 avenue de Luminy, 13009 Marseille, France.

Contact : les directeurs de la publication, aux adresses professionnelles ci-dessus.

## Hébergement

GitHub Pages, service fourni par GitHub, Inc., 88 Colin P. Kelly Jr. Street, San Francisco, CA 94107, États-Unis.
Pour servir le site, GitHub traite des données techniques de connexion, dont l'adresse IP des visiteurs ; voir la
[déclaration de confidentialité de GitHub](https://docs.github.com/en/site-policy/privacy-policies/github-general-privacy-statement) (en anglais).
Ce site est statique : il ne dépose aucun cookie et ne collecte par lui-même aucune donnée personnelle.
Votre préférence d'affichage clair/sombre est enregistrée uniquement dans votre navigateur (localStorage) et ne nous est jamais transmise.

## Formulaire de demande

Les demandes envoyées via le formulaire de la [page contact](/fr/contact/) sont recueillies avec Tally. Les réponses sont stockées par Tally (Tally BV, Belgique) sur des serveurs situés dans l'UE ; Tally fait appel à des sous-traitants, dont certains hors UE. Voir la [politique de confidentialité](https://tally.so/help/privacy-policy) et la [liste des sous-traitants](https://tally.so/help/gdpr) de Tally (en anglais).

{% assign contact_page = site.pages | where: "ref", "contact" | where: "lang", page.lang | first %}
{% assign en_contact_page = site.pages | where: "ref", "contact" | where: "lang", "en" | first %}
{% if contact_page.tally_form_id or en_contact_page.tally_form_id %}
Le formulaire de la page contact ne se charge qu'après un clic sur « Afficher le formulaire de demande » ; rien n'est demandé à Tally avant ce clic. Son chargement établit aussi une connexion avec certains sous-traitants de Tally, par exemple pour la surveillance des erreurs.
{% endif %}

- **Finalité :** traiter votre demande d'accès aux instruments ou à l'expertise, et produire des statistiques d'activité anonymes pour le financeur.
- **Données collectées :** nom, institut, adresse e-mail, numéro de téléphone (facultatif), les systèmes qui vous intéressent et la description de vos besoins.
- **Destinataires :** l'équipe de coordination du projet et, pour les demandes complexes, le comité de pilotage.
- **Durée de conservation :** les données de demande identifiantes sont conservées jusqu'à la fin du projet (juin 2028), puis anonymisées. Les statistiques anonymisées sont conservées pour le compte rendu au Canceropôle PACA.
- **Vos droits :** vous pouvez accéder à vos données, les rectifier ou les supprimer, ou vous opposer à leur traitement, en écrivant aux directeurs de la publication. Vous pouvez également introduire une réclamation auprès de la CNIL (cnil.fr).
