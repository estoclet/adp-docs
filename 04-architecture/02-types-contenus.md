# Types de contenus WordPress

**Statut** : Proposition — [À ARBITRER] après analyse legacy  
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

## Custom Post Types (CPT) à évaluer

[À ARBITRER] — Ne créer que si la valeur est démontrée.

| CPT proposé | Justification | Décision |
|-------------|--------------|----------|
| `demarche` (Démarche administrative) | Contenu structuré différemment des astuces ; mises à jour fréquentes ; potentiel de template dédié | [À ARBITRER] |
| `faq` (Question fréquente) | Si volume important de FAQ ; permet d'afficher des FAQ structurées (schema.org) | [À ARBITRER] |

> **Recommandation** : Si le volume de "Démarches" est inférieur à 20 contenus, utiliser le type Post avec une catégorie dédiée plutôt qu'un CPT. Moins de complexité, même résultat.

---

## Taxonomies

### Catégories (hiérarchiques)

| Catégorie | Slug | Niveau | Sous-catégories [HYPOTHÈSE] |
|-----------|------|--------|---------------------------|
| iPhone | iphone | 1 | iOS, Siri, Face ID, AirDrop… |
| Mac | mac | 1 | macOS, Finder, Time Machine… |
| iPad | ipad | 1 | iPadOS, Apple Pencil… |
| iCloud | icloud | 1 | Stockage, Partage, Photos… |
| Démarches | demarches | 1 | [Sous-cat à définir après analyse] |
| Apple Watch | apple-watch | 1 | [HYPOTHÈSE] |
| Safari | safari | 1 | [HYPOTHÈSE] |

> Les sous-catégories sont des hypothèses. Confirmer après analyse du legacy.

### Étiquettes (tags)

| Règle | Détail |
|-------|--------|
| Usage | Thèmes transversaux (ex: "sécurité", "confidentialité", "débutant") |
| Contrôle | Liste contrôlée — pas de tags libres en production |
| Nettoyage | Les tags du legacy sont à auditer et nettoyer |

### Taxonomie personnalisée "Niveau de difficulté" (hypothèse)

[HYPOTHÈSE — à évaluer selon besoins UX]

| Valeur | Slug | Définition |
|--------|------|------------|
| Débutant | debutant | Aucun prérequis technique |
| Intermédiaire | intermediaire | Quelques bases nécessaires |
| Avancé | avance | Utilisateurs expérimentés |

---

## Champs personnalisés (Custom Fields / ACF)

[HYPOTHÈSE — à évaluer selon les besoins des templates Divi]

| Champ | Type | Sur quel CPT/Post | Utilité |
|-------|------|-----------------|---------|
| `version_apple` | Texte | Post (astuce) | Indiquer la version iOS/macOS concernée |
| `date_verification` | Date | Post (astuce) | Indiquer quand l'article a été vérifié |
| `prerequis` | Textarea | Post (astuce) | Prérequis de l'astuce [HYPOTHÈSE] |

> **Note** : Les champs personnalisés nécessitent ACF (Advanced Custom Fields) ou équivalent. À valider avant développement.

---

## Ce que ce document ne contient pas

- L'arborescence des pages (voir `04-architecture/01-arborescence-site.md`)
- Les composants Divi (voir `04-architecture/03-composants-divi.md`)
- Les specs de pages (voir `05-specs/pages/`)
