# Composants Divi réutilisables

**Statut** : Mis à jour — D-018 one page (2026-04-25) ; popup Divi documenté
**Dernière mise à jour** : 2026-04-25 — D-018/D-019 : 3 méthodes popup Divi 5 documentées ; méthode recommandée identifiée
**Lié à** : `ADR-002-identite-visuelle.md`, `05-specs/pages/homepage.md`

---

## Principe de composantisation Divi

Divi permet de sauvegarder des sections, lignes ou modules comme "Saved Layouts" réutilisables globalement (Divi Library).

**Règle** : Un composant est sauvegardé en Divi Library s'il est réutilisé dans au moins 2 contextes (pages ou modales). En deçà, layout local.

> [MISE À JOUR — D-018] En architecture one page, "au moins 3 pages" n'est plus pertinent. La règle s'applique désormais aux réutilisations entre la homepage, les modales et les pages légales.

> [FAIT — règle projet] Les éléments visuels structurants Divi doivent être exportés en JSON et documentés. Git reste la source de vérité du code, mais les exports Divi JSON servent de référence pour Theme Builder, Theme Options, Divi Library, layouts importants et presets.

---

## Procédure — Export Divi JSON

### Éléments à exporter

| Élément | Référence attendue |
|--------|---------------------|
| Theme Builder | export JSON dédié |
| Theme Options | export JSON dédié |
| Divi Library | export JSON dédié |
| Layouts importants | export JSON dédié |
| Presets globaux | export JSON ou documentation explicite si couplés à des layouts |

### Règles

- exporter après toute modification structurante
- nommer les exports avec date ISO + périmètre
- documenter le périmètre exact de l'export
- ne pas considérer un export JSON comme substitut à Git pour du CSS/JS/PHP

Exemples de nommage :
- `2026-04-24-theme-builder.json`
- `2026-04-24-divi-library-homepage.json`
- `2026-04-24-theme-options.json`

---

## Composants globaux (Theme Builder)

Ces éléments sont construits dans le Theme Builder et s'appliquent à toutes les pages. [FAIT — consigne brief]

| Composant | Notes |
|-----------|-------|
| Header global | Fond sombre — logo + menu + bouton CTA — sticky discret |
| Footer global | 4 colonnes — clair — copyright |

### Header — détail de structure

| Zone | Contenu |
|------|---------|
| Gauche | Logo rond / monogramme blanc + "Astuces De Pomme" + "Services à la personne" |
| Centre / droite | Menu : Accueil · Prestations · Formations · À propos · Avis · Contact |
| Extrême droite | Bouton bleu "Prendre rendez-vous" |

**Modules Divi** : Logo, Menu, Button — dans une ligne 3 zones. [FAIT]

---

## Composants Divi Library (réutilisables entre pages)

Ces sections sont sauvegardées en Divi Library pour être réutilisées. [FAIT — consigne brief]

| Composant | Utilisé sur | Module Divi | Priorité |
|-----------|------------|-------------|----------|
| Carte service / prestation | Homepage blocs 3 + 5, /prestations/ | Blurb | Haute |
| Bandeau "50% crédit d'impôt" | Homepage bloc 4, /prestations/ [HYPOTHÈSE] | Section custom | Haute |
| Pill / badge thématique | Homepage bloc 6, /formations/ | Blurb stylé + CSS | Moyenne |
| Grand CTA de contact (sombre) | Homepage bloc 8, bas de /prestations/ [HYPOTHÈSE] | Call To Action ou Section custom | Haute |
| Bandeau infos pratiques | Homepage bloc 7, /contact/ [HYPOTHÈSE] | Section 4 colonnes | Moyenne |

---

## Modules Divi à utiliser (liste validée)

Ces modules sont les seuls à utiliser sauf besoin spécifique justifié. [FAIT — consigne brief]

| Module | Usage principal |
|--------|----------------|
| Text | Titres, paragraphes, H1/H2/H3 |
| Button | CTA principaux et secondaires ; déclencheurs de popup |
| Image | Visuel hero, photos, illustrations |
| Blurb | Cartes services + icône + titre + texte |
| Call To Action | Section CTA contact (bloc 8) |
| Divider | Séparateurs visuels |
| Icon | Pictos isolés |
| **Popup** | Modales Prestations, Formations, À propos, Avis, Contact (D-018/D-019) |

**Module Code** : uniquement si nécessaire pour les pills / effets non faisables autrement. [FAIT]

### Implémentation des popups Divi 5 — 3 méthodes disponibles

Source : documentation officielle Elegant Themes (article "How To Design Popups In Divi 5 — Three Different Ways"). [FAIT — 2026-04-25]

| Méthode | Fonctionnement | Éditabilité client | Adapté au projet |
|---------|----------------|-------------------|-----------------|
| **A — Interactions + Visibilité** | Contenu popup dans la page, masqué par réglages de visibilité, déclenché par Interactions Divi | **Oui — édit directement dans le Visual Builder** | **Recommandé (D-019)** |
| **B — Canvases + Interactions** | Popup dans un Canvas global (espace indépendant), déclenché par Interactions | Oui, mais le client doit naviguer dans les Canvases Divi | Alternative si la page devient trop longue |
| **C — Plugin Bloom** | Popups marketing dédiés, intégrations emailing, templates pré-conçus | Oui, via tableau de bord WordPress dédié | Non adapté — usage marketing uniquement, pas de contenu éditorial |

> **[FAIT — source Elegant Themes 2026-04-25]** La Méthode A (Interactions + Visibilité) est native Divi 5, sans plugin supplémentaire, et permet au client d'éditer le contenu des popups directement dans le Visual Builder. C'est la méthode retenue par défaut pour ce projet (D-019).

> **[À ARBITRER — TP-006]** Si le nombre de popups (5 : Prestations, Formations, À propos, Avis, Contact) rend la page d'accueil trop chargée dans le builder, basculer sur la Méthode B (Canvases globaux). La décision finale est prise lors de l'implémentation TP-006.

---

## CSS personnalisé à prévoir

Le CSS custom est **nécessaire** pour les éléments suivants. [FAIT — consigne brief]  
Convention de nommage : préfixe `adp-` obligatoire — voir `04-conventions-divi.md`. [FAIT — implémenté dans `adp-divi-child/assets/css/theme.css`]

| Cible CSS | Objectif | Statut |
|-----------|---------|--------|
| `.adp-card-service` | Uniformiser les coins arrondis (16-24px), hauteur égale | ✅ Implémenté |
| `.adp-card-service:hover` | Hover subtil (ombre légère ou légère remontée) | ✅ Implémenté |
| `.adp-pill-theme` | Forme capsule, contour léger, icône gauche | ✅ Implémenté |
| `.adp-btn-secondary` | Bouton contour clair + style de survol | ✅ Implémenté |
| Media queries mobile | Empilement propre, boutons pleine largeur | ✅ Implémenté |
| Header sticky | Transition discrète au scroll | À faire en Lot 3 |

---

## Charte Divi — Presets à créer

Les presets Divi permettent d'appliquer un style uniforme sans CSS inline. [RECOMMANDÉ]

| Preset | Appliqué à | Description |
|--------|-----------|-------------|
| Bouton principal | Module Button | Bleu principal, coins arrondis, texte blanc |
| Bouton secondaire | Module Button | Contour bleu clair, texte bleu, fond transparent |
| Titre H2 section | Module Text | Couleur principale, centré ou gauche, taille définie |
| Carte | Module Blurb | Fond blanc, ombre légère, coins 16-24px, padding généreux |

> [RÉSOLU PARTIEL — I-07] Palette V1 disponible : bleu marine `#1e3264` + bleu accent `#0070c8`. Tons complémentaires proposés et versionnés dans `adp-divi-child/theme.css` : texte `#23344d`, fond section `#f4f8fc`, bordure `#d7e1ec` — à valider lors de la recette Divi. Source : `01-cadrage/05-assets-design.md`.

---

## Conventions de nommage Divi

| Type | Convention | Exemple |
|------|------------|---------|
| Template global | `TB - <zone> - <scope>` | `TB - Header - Global` |
| Template page | `TPL - <page>` | `TPL - Homepage` |
| Section réutilisable | `LIB - <usage> - <variante>` | `LIB - CTA - Dark` |
| Preset module | `PRESET - <module> - <usage>` | `PRESET - Button - Primary` |
| Layout d'export | `<date>-<perimetre>` | `2026-04-24-homepage-v1` |

### Règles

- nommage en ASCII simple
- préfixe obligatoire pour distinguer template, library et preset
- éviter les noms vagues du type `section test`, `copie finale`, `nouveau header`
- garder les noms stables pour limiter les ambiguïtés entre export, import et documentation

---

## Conventions CSS projet

Le CSS structurant reste versionné dans Git, idéalement dans le thème enfant ou les assets projet, pas comme unique source dans Divi.

| Sujet | Convention |
|------|------------|
| Format de classe | kebab-case |
| Préfixe projet recommandé | `adp-` |
| Classe de composant | `adp-card-service`, `adp-pill-theme` |
| Classe utilitaire limitée | `adp-u-*` si nécessaire |
| Éviter | noms génériques (`.blue`, `.box2`, `.custom-section`) |

### Règles

- une classe exprime un rôle, pas une couleur temporaire
- le CSS global passe par Git
- les snippets CSS ponctuels dans Divi doivent rester exceptionnels et documentés
- tout comportement JS ou CSS critique ne doit pas dépendre uniquement d'un champ visuel Divi

---

## Templates de pages Divi

> **[FAIT — ADR-003 / D-018]** L'architecture one page réduit le nombre de templates réels. La homepage absorbe toutes les sections. Les pages Prestations, Formations, À propos deviennent du contenu de popup.

| Template | Pages | Statut |
|----------|-------|--------|
| Template Accueil (one page) | `/` | **[FAIT]** Spec homepage révisée puis intégrée dans `adp-app` |
| Popup Prestations | Modale depuis homepage | Contenu = spec `prestations.md` — implémentation TP-006 |
| Popup Formations | Modale depuis homepage | Contenu = spec `formations.md` — implémentation TP-006 |
| Popup À propos | Modale depuis homepage | Contenu = spec `a-propos.md` — implémentation TP-006 |
| Popup Avis | Modale depuis navigation | Spec rédigée — implémentation TP-006 |
| Popup Contact | Modale depuis header/navigation | Spec rédigée — implémentation TP-006 |
| Template 404 | Toute URL inexistante | À créer — Lot 3 |

---

## Ce que ce document ne contient pas

- Les specs de pages individuelles (voir `05-specs/pages/`)
- La palette hex complète (voir `ADR-002-identite-visuelle.md`)
- Les plugins WP (voir `01-cadrage/02-architecture-cible.md`)
