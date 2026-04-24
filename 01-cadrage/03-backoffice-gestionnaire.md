# Backoffice et gestion de contenu

**Statut** : Hypothèses à valider — aucune information précise fournie  
**Dernière mise à jour** : 2026-04-24  
**Lié à** : `02-architecture-cible.md`, `04-architecture/02-types-contenus.md`

> **Note agent** : Ce document contient principalement des hypothèses raisonnables basées sur le contexte projet. Aucun fait vérifié sur l'organisation réelle du contenu n'est disponible à ce stade. Compléter après analyse legacy (TP-001) et arbitrages client.

---

## Types de contenus WordPress prévus

[HYPOTHÈSE — à confirmer après analyse legacy et brief client]

| Type | Rôle | Implémentation WP |
|------|------|-------------------|
| Articles (Posts) | Astuces, tutoriels, guides | Post type natif |
| Pages statiques | Accueil, À propos, Contact, CGU | Page type natif |
| Démarches | Guides démarches administratives | [À ARBITRER : post type natif ou CPT ?] |
| FAQ | Questions fréquentes | [À ARBITRER : page, CPT, plugin ?] |

> [À ARBITRER] : La création de Custom Post Types (CPT) pour "Démarches" et "FAQ" est à évaluer selon le volume et la structuration du contenu. Les CPT ajoutent de la flexibilité mais complexifient la maintenance.

---

## Taxonomies prévues

[HYPOTHÈSE — à valider selon le contenu legacy]

| Taxonomie | Type | Valeurs hypothétiques |
|-----------|------|----------------------|
| Catégories d'astuces | Hiérarchique (catégorie WP) | iPhone, Mac, iPad, Apple Watch, iCloud, Safari, Apple TV, Démarches |
| Tags | Plate (étiquette WP) | Libres, à nettoyer depuis le legacy |
| Niveau de difficulté | [HYPOTHÈSE] | Débutant, Intermédiaire, Avancé |

> **Note** : La structure réelle des catégories sera déterminée par l'analyse du legacy (TP-001 + TP-002). Ne pas créer des catégories sans données réelles.

---

## Workflow de publication

[HYPOTHÈSE — à valider avec le client]

| Étape | Rôle WP | Notes |
|-------|---------|-------|
| Brouillon | Auteur | Contenu en cours |
| Révision | Éditeur (si applicable) | [HYPOTHÈSE — client seul ou équipe ?] |
| Publication | Éditeur / Admin | Visible publiquement |
| Révision programmée | Admin | Mise à jour d'articles anciens |

---

## Rôles utilisateurs WordPress

[HYPOTHÈSE — à valider avec le client]

| Rôle WP | Personne | Droits |
|---------|---------|--------|
| Administrateur | Propriétaire / développeur | Accès total |
| Éditeur | Gestionnaire de contenu [HYPOTHÈSE] | Articles, pages, médias |
| Auteur | Contributeur externe [HYPOTHÈSE] | Ses propres articles |

> [À ARBITRER] : Le client gère-t-il seul le contenu ou y a-t-il plusieurs contributeurs ? Ceci impacte la configuration des rôles et la complexité de la formation.

---

## Gestion des médias

[HYPOTHÈSE basée sur pratiques standard]

| Point | Recommandation | Statut |
|-------|---------------|--------|
| Nommage des fichiers | kebab-case, descriptif | [RECOMMANDÉ] |
| Formats images | JPEG/WebP pour photos, PNG pour logos/icônes | [RECOMMANDÉ] |
| Taille maximale upload | À configurer selon hébergeur | [DÉPENDANCE] → I-01 |
| Optimisation auto | Plugin Smush ou Imagify | [RECOMMANDÉ] |
| Organisation bibliothèque | Par dossiers si plugin Media Library Folders | [HYPOTHÈSE] |

---

## Formulaires de contact

[HYPOTHÈSE — à valider selon les besoins client]

| Formulaire | Localisation prévue | Plugin recommandé |
|------------|--------------------|--------------------|
| Contact général | Page Contact | Contact Form 7 ou WPForms |
| Demande d'assistance | Page Contact ou sidebar | À spécifier |
| Newsletter [HYPOTHÈSE] | Footer, pages clés | [À ARBITRER — outil email marketing ?] |

> [À ARBITRER] : Y a-t-il un outil d'email marketing en place (Mailchimp, Brevo…) ? Si oui, l'intégration au formulaire est une dépendance.

---

## Exigences d'autonomie client

[HYPOTHÈSE — objectif implicite pour ce type de projet]

Le client doit pouvoir, sans aide technique :
- Créer et publier un article
- Modifier le contenu d'une page statique
- Ajouter un média
- Modifier un menu de navigation

> [À CONFIRMER] : Le client a-t-il déjà une expérience de WordPress ? Ceci impacte le niveau de simplification de l'interface et le besoin en formation.

---

## Ce que ce document ne contient pas

- Les specs de pages (voir `05-specs/pages/`)
- L'architecture des types de contenus WP (voir `04-architecture/02-types-contenus.md`)
- Les plugins (voir `01-cadrage/02-architecture-cible.md`)
