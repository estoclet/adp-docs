# Page Formations — Spec

**Statut** : [EN RÉVISION — ADR-003] Cette spec devient le **contenu de la modale Formations** (D-018 one page, 2026-04-25)  
**Dernière mise à jour** : 2026-04-25 — D-018 : page → modale ; spec en cours de révision  
**Produit par** : Agent IA — issue #25  
**URL cible** : N/A — **contenu affiché en modale** depuis la homepage (D-018)  
**Template Divi** : Popup Divi 5 (D-019)  
**Lié à** : `ADR-002`, `04-architecture/01-arborescence-site.md`, `05-specs/pages/homepage.md`, `05-specs/pages/prestations.md`

---

## Objectif de la page

Présenter l'offre de formation Apple de manière structurée par thématiques, rassurer sur l'approche pédagogique (personnalisée, à domicile, sans jargon), et convertir vers un rendez-vous.

---

## Structure de la page

| # | Bloc | Type Divi |
|---|------|-----------|
| 1 | Header / navigation | Theme Builder — header global |
| 2 | Hero formations | Section fond clair, 2 colonnes |
| 3 | Approche pédagogique | Section fond blanc, 3 colonnes |
| 4 | Thématiques (5 sections) | Section titre + cartes 2 × 3 ou liste |
| 5 | Infos pratiques | Section fond très clair, 3 à 4 colonnes |
| 6 | Grand CTA | Section fond bleu nuit (réutilisation homepage) |
| 7 | Footer | Theme Builder — footer global |

---

## Bloc 2 — Hero formations

**Type Divi** : Section fond clair, 2 colonnes 50/50. [FAIT]

| Élément | Contenu proposé | Statut |
|---------|-----------------|--------|
| H1 | "Formations Apple à domicile" | [RECOMMANDÉ] |
| Sous-titre | "Des séances personnalisées pour apprendre à votre rythme, chez vous, dans la région lilloise." | [RECOMMANDÉ] |
| CTA | Bouton bleu "Prendre rendez-vous" → modale Contact | [FAIT] |
| Visuel colonne droite | Photo/illustration ou icône formations | [INCONNUE — I-visuels] |

---

## Bloc 3 — Approche pédagogique

**Type Divi** : Section 3 colonnes, fond blanc, icônes rondes.

| Colonne | Titre | Texte proposé | Statut |
|---------|-------|---------------|--------|
| 1 | À votre domicile | "Je me déplace chez vous — pas besoin de vous déplacer ou d'apporter votre appareil." | [RECOMMANDÉ] |
| 2 | À votre rythme | "Chaque séance s'adapte à vos besoins du moment. Débutant ou utilisateur avancé — le contenu évolue avec vous." | [RECOMMANDÉ] |
| 3 | Sans jargon | "J'explique simplement, avec des exemples concrets tirés de votre usage réel." | [RECOMMANDÉ] |

---

## Bloc 4 — Thématiques de formation

**Type Divi** : Titre de section centré + 5 cartes (Blurb ou Text). [FAIT]
**Titre de section** : "Nos thématiques" (centré). [RECOMMANDÉ]

| # | Thématique | Description proposée | Statut |
|---|-----------|----------------------|--------|
| 1 | Communication | "Appels, FaceTime, Messages, Mail, partage de contacts et gestion de votre messagerie Apple." | [RECOMMANDÉ] |
| 2 | iCloud | "Sauvegardes automatiques, synchronisation Photos/Contacts/Documents, gestion de l'espace de stockage." | [RECOMMANDÉ] |
| 3 | Multimédia | "Photos, vidéos, musique, podcasts, streaming — créer, organiser et partager vos contenus." | [RECOMMANDÉ] |
| 4 | Sécurité | "Mot de passe, identifiant Apple, double authentification, vie privée et protection de vos données." | [RECOMMANDÉ] |
| 5 | Système & Réseau | "Paramètres système, mises à jour, Wi-Fi, Bluetooth, connexion d'équipements, Finder et raccourcis Mac." | [RECOMMANDÉ] |

> Les textes de chaque thématique sont des propositions — modifiables par Julien HACHE. [FAIT — carte blanche client]

---

## Bloc 5 — Infos pratiques

**Type Divi** : Section fond très clair, 3 colonnes. [FAIT]

| Colonne | Titre | Contenu | Statut |
|---------|-------|---------|--------|
| 1 | Tarif | 80€/h — soit **40€/h après crédit d'impôt** (service à la personne déclaré) | [FAIT] |
| 2 | Format | Séances de 1h à 2h à votre domicile — sur rendez-vous | [RECOMMANDÉ] |
| 3 | Zone | Région lilloise, 60 km autour d'Houplines | [FAIT — I-11 résolu] |

---

## Bloc 6 — Grand CTA

[FAIT] Identique au Bloc 8 de la homepage — réutiliser le module Divi Library.

---

## SEO

| Élément | Valeur proposée | Statut |
|---------|----------------|--------|
| Balise title | "Formations Apple à domicile · Mac, iPhone, iPad — Astuces De Pomme" | [RECOMMANDÉ] |
| Meta description | "Séances de formation Apple personnalisées à domicile dans la région lilloise. Mac, iPhone, iPad, iCloud. 50 % de crédit d'impôt." | [RECOMMANDÉ] |
| H1 | "Formations Apple à domicile" | [RECOMMANDÉ] |
| Mot-clé principal | formation apple domicile lille | [HYPOTHÈSE] |

---

## Comportement mobile

- Bloc 3 : les 3 colonnes s'empilent verticalement. [FAIT]
- Bloc 4 : cartes en 1 colonne. [FAIT]
- Bloc 5 : infos pratiques en 1 colonne. [FAIT]

---

## Dépendances

| Dépendance | Type | Bloque |
|-----------|------|--------|
| Header + Footer globaux | Theme Builder | Toute la page |
| Module "Grand CTA" en Divi Library | Composant réutilisable | Bloc 6 |
| Modale Contact | Composant global | CTA "Prendre rendez-vous" |

---

## Signalement agent

- **Tâche accomplie** : spec complète de `/formations/` — 5 thématiques avec descriptions proposées, approche pédagogique, infos pratiques, SEO
- **Hypothèses posées** : titres de thématiques identiques à la homepage (cohérence), descriptions rédigées à partir des infos disponibles, format séance 1h-2h
- **Inconnues rencontrées** : visuels d'illustration (pas bloquant pour V1), durée de séance à confirmer (I-17 partielle), horaires non nécessaires ici
- **Points à arbitrer** : aucun bloquant — tous les textes sont modifiables par Julien HACHE
- **Prochaine étape recommandée** : valider la structure et les textes, puis intégrer sous Divi
