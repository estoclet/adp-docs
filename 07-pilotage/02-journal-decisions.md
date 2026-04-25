# Journal des décisions

**Statut** : Actif — à alimenter au fil du projet  
**Maintenu par** : Eric STOCLET (chef de projet)  
**Dernière mise à jour** : 2026-04-25

> **Rôle** : Ce fichier trace toutes les décisions prises oralement, par message ou de façon informelle, qui n'ont pas (encore) fait l'objet d'un ADR formel. C'est le filet de sécurité contre la perte de mémoire collective.  
> **Règle agent** : Les agents ne modifient pas ce fichier. Seul le chef de projet l'alimente.

---

## Décisions enregistrées

| # | Date | Décideur(s) | Décision | Contexte | ADR ? |
|---|------|------------|---------|---------|-------|
| D-001 | 2026-04-24 | Julien HACHE + Eric STOCLET | Conservation de WordPress + Divi pour la refonte | Briefing initial | → ADR-001 |
| D-002 | 2026-04-24 | Eric STOCLET | Création du dossier `adp-docs/` comme colonne vertébrale documentaire | Initialisation projet | — |
| D-003 | 2026-04-24 | Eric STOCLET | Site legacy conservé dans `adp-legacy/` pour analyse | Initialisation projet | — |
| D-004 | 2026-04-23 | Julien HACHE + Eric STOCLET | Validation du brief complet de la page d'accueil (9 blocs, charte visuelle, navigation) | Réunion client | → ADR-002 |
| D-005 | 2026-04-23 | Julien HACHE | Navigation principale validée : Accueil · Prestations · Formations · À propos · Avis · Blog · Contact | Réunion client | — |
| D-009 | 2026-04-24 | Julien HACHE | Le site V1 ne comportera pas de blog ; le menu principal devient : Accueil · Prestations · Formations · À propos · Avis · Contact | Ajustement du cadrage après revue du backlog | — |
| D-010 | 2026-04-24 | Julien HACHE | Les recommandations d'architecture V1 sont validées : pas de CPT, pas de taxonomies éditoriales publiques, pas de FAQ en V1 | Arbitrages architecture / contenus | — |
| D-011 | 2026-04-24 | Julien HACHE | Le socle plugins V1 retient AIOSEO, UpdraftPlus, Redirection, `WPForms Lite`, `Complianz` et `Imagify` | Arbitrages WordPress / mutualisé OVH | — |
| D-006 | 2026-04-23 | Julien HACHE | Périmètre étendu confirmé : Assistance Apple + Formation + Réseau/Wi-Fi + Démarches + Services à la personne | Réunion client | — |
| D-007 | 2026-04-23 | Julien HACHE | Tarification : 80€/h avant déduction, 40€/h après crédit d'impôt | Réunion client | — |
| D-008 | 2026-04-23 | Julien HACHE | Téléphone de contact : 06 51 31 15 37 | Réunion client | — |
| D-012 | 2026-04-24 | Eric STOCLET (carte blanche client) | Police `Inter` retenue pour V1 — fallback `DM Sans` | Julien HACHE laisse le choix au projet ; Inter choisie pour sa lisibilité et sa compatibilité Google Fonts | — |
| D-013 | 2026-04-24 | Eric STOCLET | Divi 5.3.3 installé depuis le zip fourni par Julien HACHE et versionné dans Git (`adp-app/web/wp-content/themes/Divi/`) | Téléchargement direct depuis Elegant Themes impossible sans intervention du client ; zip fourni le 2026-04-24 ; versionnement garanti la reproductibilité de l'environnement | — |
| D-014 | 2026-04-24 | Eric STOCLET | Les pages à contenu léger (Avis, Contact, pages légales du footer) s'affichent en modale, sans page WordPress dédiée | Évite les routes orphelines et simplifie l'arborescence publique ; implémentation technique (Divi popup / plugin / CSS+JS) restant à arbitrer | — |
| D-015 | 2026-04-24 | Eric STOCLET | Le thème Divi parent est versionné dans Git pour garantir la reproductibilité de l'environnement local et préprod | Sans versionnement, toute réinstallation dépend de la disponibilité du zip ou du compte Elegant Themes ; le thème GPL autorise ce stockage | — |
| D-016 | 2026-04-25 | Eric STOCLET | Toutes les images et zones de texte manquantes (I-15/16/17/18/19, visuels pages secondaires) peuvent être couvertes par des placeholders en Lot 3 — Julien HACHE les remplacera après livraison en préprod | Déblocage du Lot 3 : évite d'attendre les contenus client pour démarrer l'intégration Divi | — |
| D-017 | 2026-04-25 | Eric STOCLET | Structure de permaliens WordPress corrigée de `/%year%/%monthnum%/%day%/%postname%/` à `/%postname%/` dans l'environnement local DDEV | Prérequis SEO ; la structure date-based est le défaut WordPress mais inadaptée à un site vitrine sans blog | — |
| D-018 | 2026-04-25 | Julien HACHE | Site one page : la homepage absorbe toutes les sections principales ; des liens "Voir plus" ouvrent des modales pour le contenu détaillé (Prestations, Formations, À propos) | Retour client 2026-04-25 — remplace la structure multi-pages initialement planifiée (D-004/D-005) ; renforce et étend D-014 (modales Avis/Contact) à l'ensemble du contenu secondaire | → ADR-003 |
| D-019 | 2026-04-25 | Eric STOCLET | Les modales sont éditables par Julien HACHE via **Divi 5 Méthode A (Interactions + Visibilité)** — contenu dans la page, éditable directement dans le Visual Builder | Confirmé par documentation Elegant Themes 2026-04-25 ; aucun plugin supplémentaire requis ; Méthode B (Canvases) en fallback si 5 popups surchargent le builder — voir `04-architecture/03-composants-divi.md` | — |
| D-020 | 2026-04-25 | Eric STOCLET | Photo portrait de Julien HACHE récupérée depuis le legacy prod (`wp-content/uploads/2021/09/`) et versionnée dans `adp-app/assets/design/julien-hache-portrait.png` | I-15 levée — image 810×552 px (screenshot, orientation paysage) ; un recadrage sera peut-être nécessaire selon l'intégration Divi | — |

---

## Modèle d'entrée

Pour ajouter une décision :

```
| D-XXX | [DATE] | [Qui a décidé] | [Quoi, en une phrase] | [Pourquoi / dans quel contexte] | [→ ADR-XXX si formalisé] |
```

---

## Décisions à formaliser en ADR

| Décision | Urgence | Statut |
|----------|---------|--------|
| ~~Choix de l'hébergeur (I-01)~~ | ~~Avant Lot 3~~ | [RÉSOLU — D-009, I-01 : VPS OVH confirmé] |
| ~~Stratégie domaine (I-03)~~ | ~~Avant Lot 4~~ | [RÉSOLU — I-03 : domaine conservé, pas de changement] |
| ~~Présence ou non d'un CPT "Démarches"~~ | ~~Avant Lot 2~~ | [RÉSOLU — D-010 : pas de CPT en V1, décision Julien HACHE 2026-04-24] |
| Implémentation technique des modales (ensemble du site — D-018) | Avant TP-006 | [À ARBITRER — D-019 : Divi 5 popup natif préférentiel si éditabilité confirmée ; voir `05-specs/pages/avis.md`] |
| **Architecture one page (D-018)** | **Avant TP-005** | **[→ ADR-003 à créer — D-018 modifie D-004/D-005 ; homepage spec à réviser]** |
