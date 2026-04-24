# Arborescence cible du site

**Statut** : Navigation validée client — structure V1 arbitrée
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
├── /prestations/                  Page hub des prestations [VALIDÉ — page unique V1]
│   ├── #assistance                Section Assistance Apple
│   ├── #formation                 Section Formation
│   ├── #reseau                    Section Réseau & Wi-Fi
│   ├── #demarches                 Section Démarches administratives
│   ├── #sauvegardes               Section Sauvegardes & Installation
│   └── #conseil                   Section Conseil
│
├── /formations/                   Page de formation [VALIDÉ — page unique V1]
│   └── Sections thématiques        Communication, iCloud, Multimédia, Sécurité, Système & Réseau
│
├── /a-propos/                     Page À propos [VALIDÉ — libellé menu]
│
├── /avis/                         Page Avis clients [VALIDÉ — page statique éditorialisée]
│   └── Sélection d'avis GBP       Avec lien vers la source externe
│
├── /blog/                         Archive Blog / Astuces [VALIDÉ — libellé menu]
│   └── /blog/{slug}/              Article individuel
│
├── /contact/                      Page Contact [VALIDÉ — libellé menu]
│
└── Pages légales (footer uniquement)
    ├── /tarifs-prestations/       [HYPOTHÈSE — présent dans footer]
    ├── /cgv/                      [FAIT — conservée depuis le legacy]
    ├── /infos-fiscales/           [FAIT — conservée depuis le legacy, distincte de `/tarifs-prestations/`]
    ├── /mentions-legales/         [FAIT — obligatoire RGPD]
    └── /politique-confidentialite/ [FAIT — obligatoire RGPD]
```

---

## Structure des URLs articles de blog

Convention retenue pour la V1 :

```
/blog/{slug-article}/
```

Exemples :
- `/blog/comment-reinitialiser-iphone/`
- `/blog/configurer-icloud-sur-mac/`

> **Règle** : Slugs en français, kebab-case, sans dates dans l'URL (les articles Apple sont mis à jour et une date dans l'URL les vieillit artificiellement).

---

## Arbitrages actés pour la V1

| Sujet | Décision actée | Impact |
|-------|----------------|--------|
| `/prestations/` | page unique avec ancres | simplicité, SEO local, mise en production plus rapide |
| `/formations/` | page unique avec sections thématiques | simplicité éditoriale, évite la sur-architecture |
| `/avis/` | page statique éditorialisée avec sélection d'avis GBP et lien externe | contrôle éditorial, dépendance technique réduite |
| Homepage | intégration légère d'avis GBP sélectionnés ou d'un indicateur de note, sans widget lourd en V1 | réassurance sans dégrader les performances |
| `/faq/` | hors V1 | évite une page faible sans corpus réel |
| `/tarifs-prestations/` | page indexée | utile pour la conversion et le SEO |
| `/infos-fiscales/` | page indexée | utile pour le cadre fiscal et la réassurance |
| Blog | présent dès la V1 | cohérent avec le menu principal et la stratégie de contenu |

---

## Pages absentes du menu mais nécessaires

| Page | URL | Raison |
|------|-----|--------|
| Mentions légales | `/mentions-legales/` | Obligation légale |
| Politique de confidentialité | `/politique-confidentialite/` | RGPD |
| Tarifs & prestations | `/tarifs-prestations/` | Présente dans footer du brief |
| CGV | `/cgv/` | Continuité contractuelle depuis le legacy |
| Informations fiscales | `/infos-fiscales/` | Page fiscale dédiée conservée, distincte de `/tarifs-prestations/` |
| Page 404 | — | Template à créer dans Divi |

---

## Ce que ce document ne contient pas

- Les specs de pages individuelles (voir `05-specs/pages/`)
- Les types de contenus WP (voir `04-architecture/02-types-contenus.md`)
- Le mapping des URLs legacy (voir `03-legacy/03-mapping-migration.md`)
