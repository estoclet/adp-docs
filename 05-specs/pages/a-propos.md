# Page À propos — Spec

**Statut** : Brouillon — à valider par Eric STOCLET  
**Dernière mise à jour** : 2026-04-24  
**Produit par** : Agent IA — issue #25  
**URL cible** : `/a-propos/`  
**Template Divi** : Template À propos (sur mesure, hors Theme Builder)  
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
| Colonne gauche | Photo de Julien HACHE | [INCONNUE — I-15] |
| H1 (colonne droite) | "Julien Hache — Astuces De Pomme" | [RECOMMANDÉ] |
| Sous-titre | "Technicien Apple indépendant, à votre domicile dans la région lilloise." | [RECOMMANDÉ] |

---

## Bloc 3 — Parcours / présentation

**Type Divi** : Section 1 colonne, texte centré ou justifié, fond blanc.

| Élément | Contenu | Statut |
|---------|---------|--------|
| H2 | "Qui suis-je ?" | [RECOMMANDÉ] |
| Texte bio | À fournir par Julien HACHE — parcours, expérience, déclencheur de création d'entreprise | [INCONNUE — I-16] |

> [INCONNUE — I-16] Texte biographique à rédiger par Julien HACHE (ou dictée + reformulation). Longueur cible : 150 à 300 mots.

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
| Photo Julien HACHE (I-15) | Asset client | Bloc 2 — non bloquant pour V1 si absent |
| Texte bio (I-16) | Contenu client | Bloc 3 — bloquant pour finalisation |
| Module "Grand CTA" en Divi Library | Composant réutilisable | Bloc 6 |

---

## Inconnues bloquantes

| ID | Inconnue | Impact |
|----|----------|--------|
| I-15 | Photo de Julien HACHE (portrait) | Bloc 2 hero — un placeholder peut être utilisé en V1 |
| I-16 | Texte biographique / histoire / valeurs | Bloc 3 — **bloquant pour la finalisation** |

> [À ARBITRER] Si Julien HACHE ne souhaite pas rédiger de bio longue, le Bloc 3 peut être remplacé par une présentation plus courte (3 phrases + 3 valeurs en cartes). La page reste valide.

---

## Signalement agent

- **Tâche accomplie** : spec complète de `/a-propos/` — structure, contenu proposé, données légales SAP renseignées depuis les sources legacy
- **Hypothèses posées** : 3 valeurs (clarté, proximité, honnêteté) — à valider ; format bio 150-300 mots
- **Inconnues rencontrées** : I-15 (photo), I-16 (bio) — à recueillir auprès de Julien HACHE
- **Points à arbitrer** : niveau de détail bio, présence ou non d'une photo
- **Prochaine étape recommandée** : recueillir I-15 et I-16 auprès de Julien HACHE
