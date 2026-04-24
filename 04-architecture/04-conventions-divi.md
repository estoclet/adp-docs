# Conventions Divi et CSS

**Statut** : Brouillon — principes fondateurs actifs, détails à compléter en Lot 3  
**Dernière mise à jour** : 2026-04-24  
**Lié à** : `ADR-001`, `ADR-002`, `03-composants-divi.md`, `01-cadrage/02-architecture-cible.md`

> Ce document pose les principes qui s'appliquent dès maintenant.  
> Les conventions de détail (classes CSS custom, structure du thème enfant) seront complétées quand le thème enfant sera créé en Lot 3.

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
- [DÉPENDANCE] La palette exacte est bloquée par I-07 (hex à recueillir — Julien HACHE).
- [FAIT] La police n'est plus bloquante : carte blanche client. Préconisation projet actuelle : `Inter`, avec fallback `DM Sans`.

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

## Ce que ce document ne contient pas encore

- Structure détaillée du thème enfant (à créer en Lot 3)
- Liste exhaustive des classes CSS custom (à définir en Lot 3)
- Conventions de responsive Divi (breakpoints, comportements mobile)
