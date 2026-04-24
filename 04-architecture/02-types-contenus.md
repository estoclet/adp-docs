# Types de contenus WordPress

**Statut** : Arbitré V1 — architecture de contenu minimale retenue  
**Dernière mise à jour** : 2026-04-24  
**Lié à** : `01-arborescence-site.md`, `03-backoffice-gestionnaire.md`

> **Note agent** : Ce document liste les types de contenus WP à mettre en place. Les CPT (Custom Post Types) sont à créer uniquement si le contenu s'y prête. Ne pas sur-architecturer.

---

## Types de contenus natifs WP (utilisés tels quels)

| Type WP | Usage dans ADP | Notes |
|---------|---------------|-------|
| Post (article) | Hors V1 | type natif conservé mais non exploité publiquement |
| Page | Accueil, Contact, À propos, CGU | Contenu statique |
| Media | Images, captures d'écran, vidéos | Bibliothèque WP standard |

---

## Custom Post Types (CPT)

Décision V1 : **aucun CPT supplémentaire**.

| Sujet | Décision V1 | Justification |
|-------|-------------|---------------|
| Démarches administratives | page ou section éditoriale, pas de CPT | pas de blog exposé en V1 |
| FAQ | pas de CPT, pas de page FAQ en V1 | pas de corpus suffisant à ce stade |

> **Règle V1** : rester principalement sur `Page` et `Media`. Le type `Post` n'entre pas dans le périmètre public V1.

---

## Taxonomies

### Catégories (hiérarchiques)

Non retenues en V1 publique.

> **Décision V1** : aucune taxonomie éditoriale publique n'est à configurer tant que le site n'expose pas de blog.

### Étiquettes (tags)

Non retenues en V1 publique.

### Taxonomie personnalisée "Niveau de difficulté"

Décision V1 : **non retenue**.

Motif : ajoute de la charge éditoriale sans bénéfice démontré à ce stade.

---

## Champs personnalisés (Custom Fields / ACF)

[V1 retenue — champs minimaux]

| Champ | Type | Sur quel contenu | Utilité |
|-------|------|------------------|---------|
| `version_apple` | Texte | Hors V1 | à réactiver si un contenu éditorial est introduit plus tard |
| `date_verification` | Date | Hors V1 | à réactiver si un contenu éditorial est introduit plus tard |

> **Règle V1** : aucun champ personnalisé éditorial n'est requis tant que le site ne publie pas d'articles.

---

## Ce que ce document ne contient pas

- L'arborescence des pages (voir `04-architecture/01-arborescence-site.md`)
- Les composants Divi (voir `04-architecture/03-composants-divi.md`)
- Les specs de pages (voir `05-specs/pages/`)
