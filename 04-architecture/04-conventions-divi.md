# Conventions Divi et CSS

**Statut** : Brouillon — principes fondateurs actifs, détails à compléter en Lot 3  
**Dernière mise à jour** : 2026-04-25 — thème enfant créé (v0.1.0), CSS tokens et classes documentées  
**Lié à** : `ADR-001`, `ADR-002`, `03-composants-divi.md`, `01-cadrage/02-architecture-cible.md`

> Ce document pose les principes qui s'appliquent dès maintenant.  
> Le thème enfant `adp-divi-child` v0.1.0 est actif — les classes CSS de base sont versionnées dans `adp-app/web/wp-content/themes/adp-divi-child/assets/css/theme.css`. [FAIT — commit `7a389ee`]

---

## Principes non négociables

### Pas de CSS dans les modules Divi
Le CSS custom ne s'écrit pas dans le champ "CSS personnalisé" de chaque module.  
Il vit dans le thème enfant (`style.css` ou fichiers inclus) ou dans les **Options du thème → CSS personnalisé**.

**Raison** : le CSS inline module-par-module est introuvable, non versionnable et impossible à maintenir.

### Un preset = un composant réutilisable
Chaque style répété plus de deux fois sur le site devient un preset Divi nommé.  
Un preset non nommé explicitement n'est pas un preset — c'est du style ponctuel.

### La Divi Library est la source de vérité des blocs réutilisables
Tout élément destiné à être réutilisé (header, footer, section CTA, carte de service) passe par la **Divi Library**, pas par copier-coller entre pages.

### Pas de modification directe des fichiers de thème parent
Le thème Divi parent est intouchable. Toute surcharge passe par le thème enfant. [FAIT — principe WordPress standard]

---

## Nommage des presets

Convention : `[composant]-[variante]` en minuscules, sans accent, tirets comme séparateurs.

| Exemple de preset | Signification |
|-------------------|---------------|
| `bouton-primaire` | CTA principal (fond coloré) |
| `bouton-secondaire` | CTA secondaire (contour) |
| `carte-service` | Bloc blurb service |
| `titre-section` | H2 de section |
| `bandeau-info` | Bande de réassurance |

[HYPOTHÈSE — à valider et compléter au démarrage du Lot 3]

---

## Nommage dans la Divi Library

Convention : `[Zone] — [Nom du bloc]`

| Exemple | Zone |
|---------|------|
| `Global — Header` | Template global |
| `Global — Footer` | Template global |
| `Homepage — Bloc Hero` | Section de page |
| `Homepage — Cartes services` | Section de page |
| `Réutilisable — CTA sombre` | Bloc multi-pages |

[HYPOTHÈSE — à ajuster selon les sections validées]

---

## Gestion des couleurs et typographies

- Les couleurs ne sont **jamais** saisies en dur dans les modules : elles passent par les **couleurs globales Divi** (palette définie dans les Réglages Divi).
- Les typographies passent par les **presets de texte Divi** ou le CSS du thème enfant.
- [RÉSOLU PARTIEL — I-07] Palette V1 : bleu marine `#1e3264` (extrait de `logo-dark.png`) + bleu accent `#0070c8` (extrait de `maquette_homepage.png`). Source : `01-cadrage/05-assets-design.md`. Tons complémentaires non définis — non nécessaires pour V1.
- [FAIT] Police validée : `Inter`. Carte blanche client — décision 2026-04-24. Fallback : `DM Sans`.

---

## Exports et versionnement Divi

Voir R-18 (`02-gouvernance-ia/01-regles-ia.md`) — rappel synthétique :

| Artefact | Export requis | Format |
|----------|--------------|--------|
| Theme Builder (header, footer) | Oui | JSON Divi |
| Theme Options | Oui | JSON Divi |
| Divi Library | Oui (blocs structurants) | JSON Divi |
| Presets globaux | Oui | JSON Divi |
| Pages individuelles | Au cas par cas | JSON Divi ou WXR |

Les exports sont stockés dans `adp-app/divi-exports/` [À CRÉER en Lot 3].

---

## CSS custom versionnée — état au 2026-04-25

Source de vérité : `adp-app/web/wp-content/themes/adp-divi-child/assets/css/theme.css` — commit `7a389ee`. [FAIT — vérifiable via git log adp-app]

### Tokens CSS (variables)

| Variable | Valeur | Usage |
|----------|--------|-------|
| `--adp-color-primary` | `#1e3264` | Bleu marine — couleur principale |
| `--adp-color-accent` | `#0070c8` | Bleu accent — CTA, liens actifs |
| `--adp-color-white` | `#ffffff` | Blanc pur — fonds, textes sur fond sombre |
| `--adp-color-text` | `#23344d` | Bleu-gris foncé — texte courant |
| `--adp-color-surface` | `#f4f8fc` | Bleu clair très désaturé — fonds de section |
| `--adp-color-border` | `#d7e1ec` | Gris-bleu clair — bordures discrètes |
| `--adp-radius-md` | `16px` | Rayon standard — cartes |
| `--adp-radius-lg` | `24px` | Rayon large — sections, blocs |
| `--adp-shadow-sm` | `0 12px 30px rgba(30,50,100,0.08)` | Ombre légère au repos |
| `--adp-shadow-hover` | `0 18px 40px rgba(30,50,100,0.12)` | Ombre au survol |
| `--adp-container-max` | `1280px` | Largeur max du contenu |

### Classes CSS disponibles

| Classe | Usage | Notes |
|--------|-------|-------|
| `.adp-card-service` | Carte service (blurb) | Rayon + ombre + hover lift |
| `.adp-pill-theme` | Badge thème (pilule) | Fond blanc, bordure, flex inline |
| `.adp-btn-secondary` | Bouton secondaire | Bordure accent, rayon pill |
| `.adp-button-full-mobile` | Bouton pleine largeur | Mobile uniquement (≤767px) |

> **Règle** : utiliser ces classes via le champ CSS du module Divi — ne pas recréer ces styles en CSS inline.  
> **Interdit** : créer de nouvelles classes sans préfixe `adp-`.

---

## Ce que ce document ne contient pas encore

- Conventions de responsive Divi (breakpoints, comportements mobile)
- Classes CSS custom à créer en Lot 3 pour les blocs non encore construits
