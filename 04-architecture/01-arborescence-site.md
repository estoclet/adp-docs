# Arborescence cible du site

**Statut** : Navigation client mise à jour — structure V1 arbitrée, pattern modale acté
**Dernière mise à jour** : 2026-04-24
**Lié à** : `ADR-002`, `04-architecture/02-types-contenus.md`, `05-specs/pages/`

> **Note agent** : La navigation principale a été validée en réunion client (2026-04-23), puis ajustée le 2026-04-24 avec suppression du blog à la demande du client. Les sous-pages et leur contenu restent des hypothèses à valider.

---

## Navigation principale (validée)

Les 6 items du menu principal sont **fermes** : [FAIT — ajustement client 2026-04-24]

| Item menu | URL cible | Type WP | Mode d'affichage | Statut page |
|-----------|-----------|---------|-----------------|-------------|
| Accueil | `/` | Page | Page normale | Spec complète → `05-specs/pages/homepage.md` |
| Prestations | `/prestations/` | Page | Page normale | Spec → `05-specs/pages/prestations.md` |
| Formations | `/formations/` | Page | Page normale | Spec → `05-specs/pages/formations.md` |
| À propos | `/a-propos/` | Page | Page normale | Spec → `05-specs/pages/a-propos.md` |
| Avis | — | Modale | **Modale** (contenu léger) | Spec → `05-specs/pages/avis.md` |
| Contact | — | Modale | **Modale** (contenu léger) | Spec → `05-specs/pages/contact.md` |

**Pattern modale** : [FAIT — décision chef de projet 2026-04-24] Les pages à contenu léger (Avis, Contact, pages légales footer) s'affichent en modale plutôt qu'en page dédiée. La solution technique (Divi popup natif, plugin, ou CSS/JS) est à arbitrer — voir `05-specs/pages/avis.md` pour la table de comparaison des options.

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
├── /avis/                         → MODALE (contenu léger — sélection avis GBP)
│
├── /contact/                      → MODALE (contenu léger — formulaire + coordonnées)
│
└── Pages légales (footer uniquement) → MODALES
    ├── /cgv/                      [FAIT — conservée depuis le legacy]
    ├── /infos-fiscales/           [FAIT — conservée depuis le legacy]
    ├── /mentions-legales/         [FAIT — obligatoire RGPD]
    ├── /politique-confidentialite/ [FAIT — obligatoire RGPD]
    └── /tarifs-prestations/       [HYPOTHÈSE — présent dans footer]
```

---

## Blog

Décision client du 2026-04-24 : **pas de blog sur le site en V1**.

Conséquences :
- aucun item `Blog` dans la navigation principale
- aucune archive `/blog/` à créer en V1
- aucun template d'article blog à prévoir dans le lot de développement V1

---

## Arbitrages actés pour la V1

| Sujet | Décision actée | Impact |
|-------|----------------|--------|
| `/prestations/` | page unique avec ancres | simplicité, SEO local, mise en production plus rapide |
| `/formations/` | page unique avec sections thématiques | simplicité éditoriale, évite la sur-architecture |
| `/avis/` | **modale** (contenu léger) — sélection d'avis GBP + lien vers fiche GBP | décision chef de projet 2026-04-24 |
| Contact | **modale** (contenu léger) — formulaire + coordonnées | décision chef de projet 2026-04-24 |
| Pages légales footer | **modales** — CGV, Mentions légales, Politique de confidentialité, Infos fiscales | décision chef de projet 2026-04-24 |
| Homepage | intégration légère d'avis GBP sélectionnés ou d'un indicateur de note, sans widget lourd en V1 | réassurance sans dégrader les performances |
| `/faq/` | hors V1 | évite une page faible sans corpus réel |
| `/tarifs-prestations/` | page indexée | utile pour la conversion et le SEO |
| `/infos-fiscales/` | page indexée | utile pour le cadre fiscal et la réassurance |
| Blog | hors V1 | décision client explicite |

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
