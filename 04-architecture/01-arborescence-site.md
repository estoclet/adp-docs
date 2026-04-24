# Arborescence cible du site

**Statut** : Navigation validée client — structure de contenu en cours
**Dernière mise à jour** : 2026-04-24
**Lié à** : `ADR-002`, `04-architecture/02-types-contenus.md`, `05-specs/pages/`

> **Note agent** : La navigation principale a été validée en réunion client (2026-04-23) — elle est ferme. Les sous-pages et leur contenu sont des hypothèses à valider.

---

## Navigation principale (validée)

Les 7 items du menu principal sont **fermes** : [FAIT — réunion 2026-04-23]

| Item menu | URL cible | Type WP | Statut page |
|-----------|-----------|---------|-------------|
| Accueil | `/` | Page | Spec complète → `05-specs/pages/homepage.md` |
| Prestations | `/prestations/` | Page | [À SPÉCIFIER] |
| Formations | `/formations/` | Page | [À SPÉCIFIER] |
| À propos | `/a-propos/` | Page | [À SPÉCIFIER] |
| Avis | `/avis/` | Page | [À SPÉCIFIER] |
| Blog | `/blog/` | Archive Posts WP | [À SPÉCIFIER] |
| Contact | `/contact/` | Page | [À SPÉCIFIER] |

**CTA header** : "Prendre rendez-vous" [FAIT]

---

## Arborescence complète proposée

```
astucesdepomme.com/
│
├── /                              Accueil [VALIDÉ]
│
├── /prestations/                  Page hub des prestations [VALIDÉ — libellé menu]
│   ├── #assistance                Section Assistance Apple
│   ├── #formation                 Section Formation
│   ├── #reseau                    Section Réseau & Wi-Fi
│   ├── #demarches                 Section Démarches administratives
│   ├── #sauvegardes               Section Sauvegardes & Installation
│   └── #conseil                   Section Conseil
│
├── /formations/                   Page ou hub des formations [VALIDÉ — libellé menu]
│   └── [détail par thématique ?]  Communication, iCloud, Multimédia, Sécurité, Système & Réseau
│
├── /a-propos/                     Page À propos [VALIDÉ — libellé menu]
│
├── /avis/                         Page Avis clients [VALIDÉ — libellé menu]
│
├── /blog/                         Archive Blog / Astuces [VALIDÉ — libellé menu]
│   └── /blog/{slug}/              Article individuel
│
├── /contact/                      Page Contact [VALIDÉ — libellé menu]
│
└── Pages légales (footer uniquement)
    ├── /tarifs-prestations/       [HYPOTHÈSE — présent dans footer]
    ├── /faq/                      [HYPOTHÈSE — présent dans footer]
    ├── /mentions-legales/         [FAIT — obligatoire RGPD]
    └── /politique-confidentialite/ [FAIT — obligatoire RGPD]
```

---

## Structure des URLs articles de blog

Convention proposée [HYPOTHÈSE — à valider] :

```
/blog/{slug-article}/
```

Exemples :
- `/blog/comment-reinitialiser-iphone/`
- `/blog/configurer-icloud-sur-mac/`

> **Règle** : Slugs en français, kebab-case, sans dates dans l'URL (les articles Apple sont mis à jour et une date dans l'URL les vieillit artificiellement).

---

## Points à arbitrer sur l'arborescence

| Question | Impact | [À ARBITRER] |
|----------|--------|-------------|
| /prestations/ : page unique avec ancres ou sous-pages ? | Architecture, SEO | Julien HACHE |
| /formations/ : page unique ou sous-pages par thématique ? | Volume de contenu, SEO | Julien HACHE |
| /avis/ : page statique ou intégration outil avis (Google, Trustpilot…) ? | Fonctionnel | Julien HACHE |
| /faq/ et /tarifs-prestations/ : pages indexées ou non ? | SEO | Julien HACHE |
| Blog = migration des astuces legacy ou nouveau contenu ? | Migration, Lot 4 | Eric STOCLET + analyse TP-001 |
| Catégories de blog : reprendre les catégories legacy ou restructurer ? | Taxonomie WP | Analyse legacy requise |

---

## Pages absentes du menu mais nécessaires

| Page | URL | Raison |
|------|-----|--------|
| Mentions légales | `/mentions-legales/` | Obligation légale |
| Politique de confidentialité | `/politique-confidentialite/` | RGPD |
| Tarifs & prestations | `/tarifs-prestations/` | Présente dans footer du brief |
| FAQ | `/faq/` | Présente dans footer du brief |
| Page 404 | — | Template à créer dans Divi |

---

## Ce que ce document ne contient pas

- Les specs de pages individuelles (voir `05-specs/pages/`)
- Les types de contenus WP (voir `04-architecture/02-types-contenus.md`)
- Le mapping des URLs legacy (voir `03-legacy/03-mapping-migration.md`)
