# Backoffice et gestion de contenu

**Statut** : Base V1 cadrée — à compléter selon usages réels  
**Dernière mise à jour** : 2026-04-24  
**Lié à** : `02-architecture-cible.md`, `04-architecture/02-types-contenus.md`

> **Note agent** : Ce document contient principalement des hypothèses raisonnables basées sur le contexte projet. Aucun fait vérifié sur l'organisation réelle du contenu n'est disponible à ce stade. Compléter après analyse legacy (TP-001) et arbitrages client.

---

## Types de contenus WordPress prévus

[HYPOTHÈSE — à confirmer après analyse legacy et brief client]

| Type | Rôle | Implémentation WP |
|------|------|-------------------|
| Articles (Posts) | Hors V1 | type natif conservé mais non exploité publiquement |
| Pages statiques | Accueil, À propos, Contact, CGU | Page type natif |
| Démarches | Contenu de service / information | pages ou sections de pages en V1 |
| FAQ | Questions fréquentes | Hors V1 |

> **Décision V1** : aucun CPT additionnel n'est prévu au démarrage.

---

## Taxonomies prévues

[HYPOTHÈSE — à valider selon le contenu legacy]

| Taxonomie | Type | Valeurs hypothétiques |
|-----------|------|----------------------|
| Catégories d'astuces | Hors V1 | — |
| Tags | Hors V1 | — |
| Niveau de difficulté | Non retenu en V1 | —

> **Règle V1** : démarrer simple, sans sous-catégories ni taxonomie additionnelle tant que le volume réel ne l'impose pas.

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
| Taille maximale upload | À vérifier dans le panneau OVH — hébergement mutualisé Pro, limite PHP `upload_max_filesize` | [FAIT — I-01 résolu, valeur exacte à lire dans les paramètres OVH] |
| Optimisation auto | Plugin Smush ou Imagify | [RECOMMANDÉ] |
| Organisation bibliothèque | Par dossiers si plugin Media Library Folders | [HYPOTHÈSE] |

> [FAIT — règle projet] `wp-content/uploads`, les backups, caches, logs, secrets et exports contenant des données personnelles ne doivent pas être versionnés dans Git.

---

## Référentiels de vérité projet

| Sujet | Référence projet | Statut |
|------|------------------|--------|
| Code, thème enfant, scripts, documentation | Git | [FAIT — règle projet] |
| Contenus WordPress | exports WXR / WP-CLI | [FAIT — règle projet] |
| Structure Divi globale | exports Divi JSON | [FAIT — règle projet] |
| Médias | synchronisation séparée | [FAIT — règle projet] |

---

## Procédure — Export / import WordPress WXR via WP-CLI

### Export WXR

| Étape | Commande / action | Notes |
|------|--------------------|-------|
| Export complet contenu | `wp export --dir=<chemin-export>` | Produit un WXR XML |
| Export ciblé pages | `wp export --post_type=page --dir=<chemin-export>` | Utile pour migration partielle |
| Export ciblé articles | `wp export --post_type=post --dir=<chemin-export>` | utile seulement si un blog est réintroduit plus tard |
| Export avec date | nommer le dossier/fichier avec date ISO | ex. `2026-04-24-wxr/` |

### Import WXR

| Étape | Commande / action | Notes |
|------|--------------------|-------|
| Installer l'importer si nécessaire | `wp plugin install wordpress-importer --activate` | À utiliser sur env de travail |
| Importer un WXR | `wp import <fichier.xml> --authors=create` | Adapter selon contexte |
| Vérifier pages et contenus | contrôle WP-CLI + backoffice | obligatoire après import |

### Règles

- exporter les contenus avant migration significative
- documenter l'origine, la date et le périmètre de l'export
- ne pas versionner dans Git un export contenant des données personnelles non minimisées

---

## Procédure — Synchronisation des médias

Les médias sont synchronisés séparément du code et des exports structurants.

| Méthode | Usage | Notes |
|--------|------|-------|
| Backup hébergeur | restauration / snapshot | dépend de l'hébergeur |
| `rsync` | synchronisation contrôlée de `uploads/` | recommandé pour copie ciblée |
| archive ponctuelle | transfert manuel | acceptable pour petit volume |

### Règles

- ne pas versionner `wp-content/uploads`
- documenter la source, la date et le périmètre de toute synchro média
- vérifier les droits fichiers et la cohérence des URLs après synchronisation
- traiter les médias comme des données séparées du code

---

## Politique de modification en production

Toute modification en production doit être tracée et classée :

| Classe | Exemples | Règle |
|-------|----------|-------|
| Contenu simple | texte de page, image de contenu, article | autorisé si traçable |
| Configuration | option WP, menu, réglage non critique | autorisé si documenté |
| Code | CSS, JS, PHP, scripts, thème enfant | exceptionnel, réintégration Git obligatoire |
| Modification risquée | plugins, templates globaux, presets, structure Divi, migration de contenu, réglages critiques | validation humaine préalable |

### Limites d'autonomie client

Le client peut modifier :
- les textes
- les images de contenu

Le client ne modifie pas sans procédure :
- les templates globaux
- les presets
- les réglages Divi structurants
- le CSS global
- le PHP
- les plugins

---

## Checklists avant / après déploiement

### Avant déploiement

- [ ] code à jour dans Git
- [ ] exports Divi JSON à jour pour les éléments structurants modifiés
- [ ] export WXR/WP-CLI prêt si le contenu est concerné
- [ ] médias synchronisés ou plan de synchro confirmé
- [ ] secrets, backups, caches, logs et données personnelles exclus du versionnement
- [ ] vérification des URLs, du canonical et de l'environnement cible
- [ ] validation humaine obtenue pour toute modification risquée

### Après déploiement

- [ ] contrôle visuel des templates globaux
- [ ] contrôle des pages critiques
- [ ] vérification des menus et taxonomies si contenu importé
- [ ] vérification des médias et liens d'images
- [ ] vérification des redirections, sitemap, robots.txt
- [ ] vérification des formulaires et CTA
- [ ] si modification de code : confirmation que Git reflète exactement l'état déployé

---

## Formulaires de contact

[PROPOSITION V1 — à arbitrer si besoin]

| Formulaire | Localisation prévue | Plugin recommandé |
|------------|--------------------|--------------------|
| Contact général | Page Contact | WPForms Lite |
| Demande d'assistance | Page Contact ou sidebar | À spécifier |
| Newsletter [HYPOTHÈSE] | Footer, pages clés | [À ARBITRER — outil email marketing ?] |

> **Recommandation projet** : privilégier un seul formulaire simple en V1. Ne pas introduire de formulaire supplémentaire ni d'intégration marketing tant que le besoin n'est pas confirmé.

---

## Exigences d'autonomie client

[HYPOTHÈSE — objectif implicite pour ce type de projet]

Le client doit pouvoir, sans aide technique :
- Modifier le contenu d'une page statique
- Ajouter un média
- Modifier un menu de navigation

> [À CONFIRMER] : Le client a-t-il déjà une expérience de WordPress ? Ceci impacte le niveau de simplification de l'interface et le besoin en formation.

> [FAIT — règle projet] Cette autonomie ne couvre pas les templates globaux, presets, réglages Divi structurants, CSS global, PHP ni plugins sans procédure dédiée.

---

## Ce que ce document ne contient pas

- Les specs de pages (voir `05-specs/pages/`)
- L'architecture des types de contenus WP (voir `04-architecture/02-types-contenus.md`)
- Les plugins (voir `01-cadrage/02-architecture-cible.md`)
