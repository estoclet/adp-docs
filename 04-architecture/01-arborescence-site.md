# Arborescence cible du site

**Statut** : [FAIT] Révisé ADR-003 (D-018 one page)  
**Dernière mise à jour** : 2026-04-27 — D-018 : site one page, modales "Voir plus" pour tout le contenu secondaire  
**Lié à** : `ADR-003`, `04-architecture/02-types-contenus.md`, `05-specs/pages/`

---

## Navigation principale (validée)

Les 6 items du menu principal sont **fermes**. Dans l'architecture one-page, ils pointent vers des ancres sur la homepage ou déclenchent des modales.

| Item menu | URL / Ancre cible | Type WP | Mode d'affichage | Statut |
|-----------|-------------------|---------|-----------------|--------|
| Accueil | `/` | Page | Page normale | [FAIT] |
| Prestations | `/#prestations` | Section homepage | Ancre + modale `#modal-prestations` | [FAIT] |
| Formations | `/#formations` | Section homepage | Ancre + modale `#modal-formations` | [FAIT] |
| À propos | `/#a-propos` | Section homepage | Ancre + modale `#modal-a-propos` | [FAIT] |
| Avis | `/#modal-avis` | Modale | **Modale** (via ancre ou interaction) | [FAIT] |
| Contact | `/#modal-contact` | Modale | **Modale** (via ancre ou interaction) | [FAIT] |

**Pattern modale étendu (D-018)** : [FAIT] L'ensemble du contenu secondaire du site (Prestations, Formations, À propos) s'affiche désormais en modale depuis la homepage. Implémentation via Divi 5 popup natif (Méthode A — Interactions + Visibilité).

**Condition d'éditabilité (D-019)** : Les modales sont éditables par Julien HACHE en autonomie dans le Visual Builder (vérifié via documentation Divi 5).

---

## Arborescence complète (One-Page Hub)

```
astucesdepomme.com/
│
├── / (Homepage)                   Hub unique du site
│   ├── #prestations               Section Prestations (résumé)
│   │   └── #modal-prestations     Détail Assistance, Formation, Réseau, Démarches, etc.
│   │
│   ├── #formations                Section Formations (résumé)
│   │   └── #modal-formations      Détail pédagogie et thématiques
│   │
│   ├── #a-propos                  Section À propos (intro)
│   │   └── #modal-a-propos        Détail bio Julien Hache et Agrément SAP
│   │
│   ├── #modal-avis                Modale Avis (sélection GBP)
│   └── #modal-contact             Modale Contact (formulaire)
│
└── Pages légales (footer uniquement) → Pages WordPress dédiées
    ├── /cgv/                      [FAIT]
    ├── /infos-fiscales/           [FAIT]
    ├── /mentions-legales/         [FAIT]
    ├── /politique-confidentialite/ [FAIT]
    └── /tarifs-prestations/       [FAIT]
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
| Architecture globale | **Site one page** — homepage hub unique, navigation anchor-based, "Voir plus" → modales | D-018 (Julien HACHE 2026-04-25) — voir ADR-003 |
| Prestations | Section de la homepage + modale "Voir plus" (contenu détaillé) | D-018 — ID `#modal-prestations` |
| Formations | Section de la homepage + modale "Voir plus" (contenu détaillé) | D-018 — ID `#modal-formations` |
| À propos | Section de la homepage + modale "Voir plus" (bio, valeurs, agrément SAP) | D-018 — ID `#modal-a-propos` |
| `/avis/` | **Modale** (sélection d'avis GBP + lien fiche GBP) | D-014 — ID `#modal-avis` |
| Contact | **Modale** (formulaire + coordonnées) | D-014 — ID `#modal-contact` |
| Pages légales footer | Pages WordPress indexées — CGV, Mentions légales, Politique de confidentialité, Infos fiscales, Tarifs | Obligations légales + SEO — non affectées par D-018 |

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
