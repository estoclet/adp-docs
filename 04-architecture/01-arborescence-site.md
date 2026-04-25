# Arborescence cible du site

**Statut** : Structure en cours de révision — décision D-018 (site one page, 2026-04-25) — voir note ci-dessous
**Dernière mise à jour** : 2026-04-25 — D-018 : site one page, modales "Voir plus" pour tout le contenu secondaire
**Lié à** : `ADR-002`, `04-architecture/02-types-contenus.md`, `05-specs/pages/`

> **Note agent** : La navigation principale a été validée en réunion client (2026-04-23), puis ajustée le 2026-04-24 avec suppression du blog à la demande du client.
>
> **[DÉCISION D-018 — 2026-04-25]** Julien HACHE a confirmé un **site one page** : la homepage absorbe toutes les sections principales, et des liens "Voir plus" ouvrent des **modales** pour le contenu détaillé (Prestations, Formations, À propos). Ce document et la spec homepage doivent être révisés en conséquence. Un ADR-003 est à créer avant TP-005. Les URLs de pages secondaires (prestations/, formations/, a-propos/) restent utiles comme ancres ou redirections SEO — décision à prendre lors de l'ADR-003.

---

## Navigation principale (validée)

Les 6 items du menu principal sont **fermes** : [FAIT — ajustement client 2026-04-24]

> **[EN RÉVISION — D-018]** : Le mode d'affichage des items "Prestations", "Formations" et "À propos" change. Ils deviennent des **ancres** vers des sections de la homepage + des modales "Voir plus". Les URLs de pages dédiées peuvent être conservées comme ancres ou redirections SEO — à arbitrer dans ADR-003.

| Item menu | URL / Ancre cible | Type WP | Mode d'affichage | Statut |
|-----------|-------------------|---------|-----------------|--------|
| Accueil | `/` | Page | Page normale | [FAIT] — Spec → `05-specs/pages/homepage.md` |
| Prestations | `/#prestations` | Section homepage | Ancre + modale "Voir plus" | [EN RÉVISION — D-018] |
| Formations | `/#formations` | Section homepage | Ancre + modale "Voir plus" | [EN RÉVISION — D-018] |
| À propos | `/#a-propos` | Section homepage | Ancre + modale "Voir plus" | [EN RÉVISION — D-018] |
| Avis | — | Modale | **Modale** (contenu léger) | [FAIT] — Spec → `05-specs/pages/avis.md` |
| Contact | — | Modale | **Modale** (contenu léger) | [FAIT] — Spec → `05-specs/pages/contact.md` |

**Pattern modale étendu (D-018)** : [FAIT — décision Julien HACHE 2026-04-25] L'ensemble du contenu secondaire du site (Prestations, Formations, À propos) s'affiche désormais en modale depuis la homepage. La solution technique (Divi 5 popup natif préférentiel — D-019) est à valider lors de l'implémentation.

**Condition d'éditabilité (D-019)** : Les modales doivent être éditables par Julien HACHE en autonomie dans le backoffice Divi. [HYPOTHÈSE — à vérifier lors de TP-006]

**CTA header** : "Prendre rendez-vous" [FAIT]

---

## Arborescence complète proposée

```
astucesdepomme.com/
│
├── /                              Accueil [FAIT]
│
├── /prestations/                  Page hub des prestations [FAIT — page unique V1]
│   ├── #assistance                Section Assistance Apple
│   ├── #formation                 Section Formation
│   ├── #reseau                    Section Réseau & Wi-Fi
│   ├── #demarches                 Section Démarches administratives
│   ├── #sauvegardes               Section Sauvegardes & Installation
│   └── #conseil                   Section Conseil
│
├── /formations/                   Page de formation [FAIT — page unique V1]
│   └── Sections thématiques        Communication, iCloud, Multimédia, Sécurité, Système & Réseau
│
├── /a-propos/                     Page À propos [FAIT — libellé menu]
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
    └── /tarifs-prestations/       [FAIT — page publiée + arbitrage V1 acté]
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
