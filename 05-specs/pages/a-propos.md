# Page À propos — Spec

**Statut** : [EN RÉVISION — ADR-003] Cette spec devient le **contenu de la modale À propos** (D-018 one page, 2026-04-25)  
**Dernière mise à jour** : 2026-04-25 — I-15 résolue (photo portrait D-020) ; D-018 : page → modale  
**Produit par** : Agent IA — issue #25  
**URL cible** : N/A — **contenu affiché en modale** depuis la homepage (D-018)  
**Template Divi** : Popup Divi 5 (D-019)  
**Lié à** : `ADR-002`, `04-architecture/01-arborescence-site.md`

---

## Objectif de la page

Humaniser le service, bâtir la confiance par la présentation de Julien HACHE (parcours, valeurs, agrément SAP), et convertir un visiteur hésitant.

**Esprit** : proximité et sincérité — page sobre, sans surcharge. [FAIT]

---

## Structure de la page

| # | Bloc | Type Divi |
|---|------|-----------|
| 1 | Header / navigation | Theme Builder — header global |
| 2 | Hero À propos | Section 2 colonnes (photo + intro) |
| 3 | Parcours / présentation | Section 1 colonne ou 2 colonnes |
| 4 | Valeurs et approche | Section 3 colonnes, fond très clair |
| 5 | Agrément SAP et certifications | Section fond blanc, 2 colonnes |
| 6 | Grand CTA | Section fond bleu nuit (réutilisation homepage) |
| 7 | Footer | Theme Builder — footer global |

---

## Bloc 2 — Hero

**Type Divi** : Section fond clair, 2 colonnes 40/60.

| Élément | Contenu | Statut |
|---------|---------|--------|
| Colonne gauche | Photo de Julien HACHE | [FAIT — `adp-app/assets/design/julien-hache-portrait.png` (D-020, 2026-04-25) — 810×552 px, recadrage possible] |
| H1 (colonne droite) | "Julien Hache — Astuces De Pomme" | [RECOMMANDÉ] |
| Sous-titre | "Technicien Apple indépendant, à votre domicile dans la région lilloise." | [RECOMMANDÉ] |

---

## Bloc 3 — Parcours / présentation

**Type Divi** : Section 1 colonne, texte centré ou justifié, fond blanc.

| Élément | Contenu | Statut |
|---------|---------|--------|
| H2 | "Qui suis-je ?" | [RECOMMANDÉ] |
| Texte bio | À fournir par Julien HACHE — parcours, expérience, déclencheur de création d'entreprise | [INCONNUE — placeholder acceptable (D-016) — Julien HACHE remplace après livraison préprod] |

> [INCONNUE — I-16] Texte biographique à rédiger par Julien HACHE (ou dictée + reformulation). Longueur cible : 150 à 300 mots. **Placeholder en intégration** : texte de substitution générique indiquant l'emplacement réservé.

---

## Bloc 4 — Valeurs et approche

**Type Divi** : Section fond très clair, 3 colonnes, icônes rondes.

| Colonne | Titre | Texte proposé | Statut |
|---------|-------|---------------|--------|
| 1 | Clarté | "J'explique sans jargon. Vous comprenez ce qui se passe sur votre appareil." | [RECOMMANDÉ] |
| 2 | Proximité | "J'interviens chez vous, à votre heure. Le service vient à vous." | [RECOMMANDÉ] |
| 3 | Honnêteté | "Si la réparation n'est pas rentable, je vous le dis. Votre intérêt avant tout." | [RECOMMANDÉ] |

> Valeurs proposées — à valider et reformuler par Julien HACHE si elles ne correspondent pas à son ressenti. [HYPOTHÈSE]

---

## Bloc 5 — Agrément SAP et confiance

**Type Divi** : Section fond blanc, 2 colonnes.

| Élément | Contenu | Statut |
|---------|---------|--------|
| H2 | "Un service agréé" | [RECOMMANDÉ] |
| Texte | "Astuces De Pomme est déclaré en tant que service à la personne (agrément N° 502282080, acte 2020-063 délivré le 11/09/2020). Cet agrément vous permet de bénéficier d'un crédit d'impôt de 50 % sur l'ensemble de mes prestations." | [FAIT — sources CGV + llms.txt legacy] |
| Mention légale | "Dans les limites prévues à l'article 199 sexdecies du code général des impôts." | [FAIT — I-14 résolu] |
| Badge/logo SAP | Badge visuel services à la personne | [RECOMMANDÉ — à créer ou sourcer] |
| SIRET | 50228208000022 — APE 8559B | [FAIT — données legacy] |

---

## Bloc 6 — Grand CTA

[FAIT] Identique au Bloc 8 de la homepage — réutiliser le module Divi Library.

---

## SEO

| Élément | Valeur proposée | Statut |
|---------|----------------|--------|
| Balise title | "À propos de Julien Hache — Astuces De Pomme" | [RECOMMANDÉ] |
| Meta description | "Julien Hache, technicien Apple indépendant agréé services à la personne, intervient à domicile dans la région lilloise pour vous aider avec vos appareils Apple." | [RECOMMANDÉ] |
| H1 | "Julien Hache — Astuces De Pomme" | [RECOMMANDÉ] |
| Mot-clé principal | technicien apple domicile lille | [HYPOTHÈSE] |

---

## Comportement mobile

- Bloc 2 : photo en pleine largeur, puis texte. [RECOMMANDÉ]
- Bloc 4 : 3 colonnes → empilement vertical. [FAIT]
- Bloc 5 : 2 colonnes → empilement. [FAIT]

---

## Dépendances

| Dépendance | Type | Bloque |
|-----------|------|--------|
| Photo Julien HACHE (I-15) | Asset client | Bloc 2 — [FAIT] `julien-hache-portrait.png` disponible (D-020) |
| Texte bio (I-16) | Contenu client | Bloc 3 — placeholder acceptable (D-016) |
| Module "Grand CTA" en Divi Library | Composant réutilisable | Bloc 6 |

---

## Inconnues

| ID | Inconnue | Impact | Statut |
|----|----------|--------|--------|
| I-15 | Photo de Julien HACHE (portrait) | Bloc 2 hero | [RÉSOLU — `adp-app/assets/design/julien-hache-portrait.png` (D-020, 2026-04-25)] |
| I-16 | Texte biographique / histoire / valeurs | Bloc 3 | [INCONNUE — placeholder acceptable (D-016) — Julien HACHE remplace après livraison préprod] |

> [À ARBITRER] Si Julien HACHE ne souhaite pas rédiger de bio longue, le Bloc 3 peut être remplacé par une présentation plus courte (3 phrases + 3 valeurs en cartes). La page reste valide.

---

## Signalement agent

- **Tâche accomplie** : spec complète de `/a-propos/` — structure, contenu proposé, données légales SAP renseignées depuis les sources legacy
- **Hypothèses posées** : 3 valeurs (clarté, proximité, honnêteté) — à valider ; format bio 150-300 mots
- **Inconnues rencontrées** : I-15 (photo) résolue (D-020) ; I-16 (bio) placeholder D-016
- **Points à arbitrer** : niveau de détail bio ; **D-018 (site one page)** : cette page devient probablement une section de la homepage + modale "Voir plus" — spec à réviser dans ADR-003
- **Prochaine étape recommandée** : réviser la spec en fonction de ADR-003 (one page) ; intégrer I-16 avec placeholder
