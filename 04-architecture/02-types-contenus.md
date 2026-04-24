# Types de contenus WordPress

**Statut** : Arbitré V1 — architecture de contenu minimale retenue  
**Dernière mise à jour** : 2026-04-24  
**Lié à** : `01-arborescence-site.md`, `03-backoffice-gestionnaire.md`

> **Note agent** : Ce document liste les types de contenus WP à mettre en place. Les CPT (Custom Post Types) sont à créer uniquement si le contenu s'y prête. Ne pas sur-architecturer.

---

## Types de contenus natifs WP (utilisés tels quels)

| Type WP | Usage dans ADP | Notes |
|---------|---------------|-------|
| Post (article) | Astuces, tutoriels, guides | Type principal — taxonomie par catégorie |
| Page | Accueil, Contact, À propos, CGU | Contenu statique |
| Media | Images, captures d'écran, vidéos | Bibliothèque WP standard |

---

## Custom Post Types (CPT)

Décision V1 : **aucun CPT supplémentaire**.

| Sujet | Décision V1 | Justification |
|-------|-------------|---------------|
| Démarches administratives | catégorie d'articles, pas de CPT | volume attendu limité et complexité évitée |
| FAQ | pas de CPT, pas de page FAQ en V1 | pas de corpus suffisant à ce stade |

> **Règle V1** : rester sur `Post`, `Page` et `Media` tant qu'un besoin métier ou éditorial clair ne démontre pas la nécessité d'un CPT.

---

## Taxonomies

### Catégories (hiérarchiques)

| Catégorie | Slug | Niveau | Notes |
|-----------|------|--------|-------|
| iPhone | iphone | 1 | catégorie V1 |
| Mac | mac | 1 | catégorie V1 |
| iPad | ipad | 1 | catégorie V1 |
| iCloud | icloud | 1 | catégorie V1 |
| Démarches | demarches | 1 | catégorie V1 |

> **Règle V1** : pas de sous-catégories tant que le volume éditorial ne le justifie pas.

### Étiquettes (tags)

| Règle | Détail |
|-------|--------|
| Usage | thèmes transversaux réellement utiles seulement |
| Contrôle | liste contrôlée, pas de tags libres en production |
| Nettoyage | aucun tag legacy repris sans audit |

### Taxonomie personnalisée "Niveau de difficulté"

Décision V1 : **non retenue**.

Motif : ajoute de la charge éditoriale sans bénéfice démontré à ce stade.

---

## Champs personnalisés (Custom Fields / ACF)

[V1 retenue — champs minimaux]

| Champ | Type | Sur quel contenu | Utilité |
|-------|------|------------------|---------|
| `version_apple` | Texte | Post (article) | indiquer la version iOS/macOS concernée |
| `date_verification` | Date | Post (article) | indiquer la date de vérification du contenu |

> **Règle V1** : ne pas ajouter d'autres champs personnalisés sans besoin explicite de template ou de maintenance éditoriale.

---

## Ce que ce document ne contient pas

- L'arborescence des pages (voir `04-architecture/01-arborescence-site.md`)
- Les composants Divi (voir `04-architecture/03-composants-divi.md`)
- Les specs de pages (voir `05-specs/pages/`)
