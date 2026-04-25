# Astuces De Pomme — Initialisation projet

**Statut** : Cadrage initial  
**Date** : 2026-04-25 — mis à jour (D-018 : site one page ; I-15 résolue : photo portrait récupérée)  
**Maintenu par** : Eric STOCLET (chef de projet)  
**Rôle** : Point d'entrée unique. Premier document à lire. Dernier à modifier.

---

## Ce qu'est ce projet

Refonte du site **Astuces De Pomme**, service de proximité couvrant :

- Assistance et dépannage Apple (iPhone, Mac, iPad, iCloud, réseau domestique)
- Formation autour de l'écosystème Apple
- Réseau & Wi-Fi (configuration, optimisation, sécurisation)
- Accompagnement aux démarches administratives en ligne
- Services à la personne (agrément déclaré — 50% crédit d'impôt)

**Tarification** : 80€/h → **40€/h après avantage fiscal** (crédit d'impôt services à la personne). [FAIT]
**Contact** : 06 51 31 15 37 [FAIT]

| Attribut | Valeur |
|----------|--------|
| Nom du projet | Refonte Astuces De Pomme |
| URL du site | https://astucesdepomme.com/ |
| Type | Refonte site web |
| Client | Julien HACHE |
| Chef de projet | Eric STOCLET |
| Cible utilisateurs | Particuliers [HYPOTHÈSE — à confirmer] |
| Enjeux principaux | Réassurance, lisibilité, conversion, image structurée |
| Répertoire nouveau site | `adp-app/` — remote : `git@github.com:estoclet/adp-app.git` |
| Site legacy (source) | `adp-legacy/` |
| Documentation projet | `adp-docs/` — remote : `git@github.com:estoclet/adp-docs.git` |

---

## Décisions déjà prises

Ces décisions sont **fermes**. Un agent ne doit pas les remettre en question sans ADR validé par un humain.

| # | Décision | Preuve |
|---|----------|--------|
| 1 | Stack technique : WordPress + Divi | Validé client — voir ADR-001 |
| 2 | Conserver l'existant dans `adp-legacy/` pour analyse | Confirmé en briefing |
| 3 | Développer le nouveau site dans `adp-app/` | Confirmé en briefing |
| 4 | Brief homepage validé (9 blocs, charte visuelle, navigation) | Réunion client 2026-04-23 — voir ADR-002 + `05-specs/pages/homepage.md` |
| 5 | Navigation : Accueil · Prestations · Formations · À propos · Avis · Contact | Réunion client 2026-04-23, ajustée le 2026-04-24 (blog retiré) |
| 6 | Périmètre : Assistance + Formation + Réseau + Démarches + Services à la personne | Réunion client 2026-04-23 |
| 7 | Tarif : 80€/h (40€ après crédit d'impôt) — téléphone : 06 51 31 15 37 | Réunion client 2026-04-23 |
| 8 | Environnement local : WordPress sous DDEV dans `adp-app/` — URL locale `http://adp.ddev.site` | Confirmé 2026-04-24 — issue #5 fermée |
| 9 | Préprod : VPS OVH — accès `ssh vps-adp` — chemin `/homez.31/astucesdib/www/dev/web` | Confirmé 2026-04-24 — issue #5 fermée |
| 10 | **Site one page** : la homepage absorbe toutes les sections ; des liens "Voir plus" ouvrent des modales (D-018) — ADR-003 à créer | Julien HACHE, 2026-04-25 |

---

## Inconnues bloquantes

Ces inconnues doivent être arbitrées par un humain avant que le travail concerné puisse avancer.

| # | Inconnue | Impact | Statut |
|---|----------|--------|--------|
| I-01 | ~~Hébergement cible~~ | Architecture, performance | [RÉSOLU — voir décisions 8 et 9] |
| I-02 | Volume réel du contenu legacy | Plan de migration | [RÉSOLU — TP-001 : 5 pages publiées, 0 articles, 82 médias originaux — voir `03-legacy/01-inventaire-legacy.md`] |
| I-03 | Nom de domaine : redirection ou changement ? | SEO, migration | [RÉSOLU — domaine conservé, pas de changement d'URL — voir `03-legacy/03-mapping-migration.md`] |
| I-04 | Budget et délais | Lotissement | [À ARBITRER] |
| I-05 | Plugins WP actifs sur le legacy | Compatibilité | [RÉSOLU — TP-001 : 4 plugins actifs (AIOSEO 4.9.6.2, cookie-dough-compliance 2.2.5, ga-google-analytics 20260421, UpdraftPlus 2.26.1.0) — voir `03-legacy/01-inventaire-legacy.md`] |
| I-06 | Accès BDD legacy pour export | Migration de contenu | [RÉSOLU — dump prod importé 2026-04-24, DDEV adp-legacy opérationnel sur `http://adp-legacy.ddev.site`] |
| I-07 | Palette hex exacte (extraire de la carte de visite) | Charte Divi | [RÉSOLU PARTIEL — tokens V1 fermes : `#1e3264`, `#0070c8`, `#ffffff` ; tons complémentaires proposés (`#23344d`, `#f4f8fc`, `#d7e1ec`) versionnés dans `adp-divi-child/theme.css` — à valider par Julien HACHE lors de la recette Divi — voir `01-cadrage/05-assets-design.md`] |
| I-08 | Persona cible détaillé | Architecture info, rédaction | [À ARBITRER] |
| I-09 | Logo / monogramme PNG fond transparent | Header, footer, CTA | [RÉSOLU — logo-dark.png + logo-white.png dans `adp-app/assets/design/` — 2026-04-24] |
| I-10 | Adresse email de contact | Homepage bloc 8, footer | [RÉSOLU — julien.hache@astucesdepomme.com — voir `03-legacy/01-inventaire-legacy.md` section "Données métier"] |
| I-11 | Zone / communes d'intervention | Homepage bloc 7 | [RÉSOLU — "Région Lilloise, 60km autour d'Houplines" — homepage legacy ID 18] |
| I-12 | Textes descriptifs des cartes de services | Homepage blocs 3 et 5 | [RÉSOLU — propositions projet validées, modifiables par Julien HACHE — voir `05-specs/pages/homepage.md`] |
| I-13 | Police validée | CSS global Divi | [RÉSOLU — carte blanche client, préconisation projet : `Inter`] |
| I-14 | Mention légale crédit d'impôt (texte exact) | Homepage bloc 4 | [RÉSOLU — "Dans les limites prévues à l'article 199 sexdecies du code général des impôts" — CGV legacy] |
| I-15 | Photo portrait de Julien HACHE | Spec `/a-propos/` | [RÉSOLU — `adp-app/assets/design/julien-hache-portrait.png` récupérée depuis le legacy prod (D-020, 2026-04-25) — 810×552 px, recadrage à prévoir selon intégration Divi] |
| I-16 | Texte biographique (parcours, expertise, valeurs) | Spec `/a-propos/` | [INCONNUE — placeholder acceptable (décision Eric STOCLET 2026-04-25) — Julien HACHE remplace après livraison préprod — issue #27] |
| I-17 | Horaires d'intervention (jours, plages horaires) | Modale Contact | [INCONNUE — placeholder acceptable] |
| I-18 | Sélection de 6 à 8 avis Google Business Profile | Modale Avis | [INCONNUE — placeholder acceptable (décision Eric STOCLET 2026-04-25) — Julien HACHE remplace après livraison préprod — issue #28] |
| I-19 | URL publique de la fiche Google Business Profile | Modale Avis | [INCONNUE — placeholder acceptable (décision Eric STOCLET 2026-04-25) — Julien HACHE remplace après livraison préprod — issue #28] |

---

## Structure de ce répertoire

```
adp-docs/
├── 00-initialisation-projet.md    ← Vous êtes ici (lecture seule pour agents)
├── INDEX.md                        ← Carte de navigation rapide
│
├── 01-cadrage/                     ← Périmètre, architecture, backoffice, migration
├── 02-gouvernance-ia/              ← Règles IA, conventions, périmètre agents
├── 03-legacy/                      ← Analyse de l'existant
├── 04-architecture/                ← Architecture cible du site
├── 05-specs/                       ← Specs fonctionnelles et pages
│   ├── pages/                      ← Une spec par page du site
│   └── fonctionnelles/             ← Un brief par fonctionnalité transverse
├── 06-decisions/                   ← ADRs (Architecture Decision Records)
├── 07-pilotage/                    ← Lotissement, task packs, journal
│   └── task-packs/                 ← Un fichier par tâche agent
└── 08-handoffs/                    ← Passations entre agents
```

---

## Règles d'usage impératives

1. **Ce fichier est en lecture seule pour les agents.** Toute modification requiert validation humaine.
2. **Les tickets vivent dans GitHub Issues** : https://github.com/estoclet/adp-docs/issues — pas dans ces fichiers.
3. **Tableau de bord projet** : https://estoclet.github.io/adp-docs/
4. **Un fait non sourcé dans ce dossier n'est pas un fait.** Marquer `[HYPOTHÈSE]` ou ne pas écrire.
5. **Lire `02-gouvernance-ia/01-regles-ia.md`** avant toute production de contenu.
6. **Tout changement de périmètre** doit passer par un ADR dans `06-decisions/`.
7. **Un agent qui ne sait pas** doit le dire explicitement — jamais inventer.

---

## Prochaines étapes recommandées

1. Lire `INDEX.md` pour la carte complète du dispositif.
2. Lire `02-gouvernance-ia/01-regles-ia.md` (règles opérationnelles).
3. Lire `02-gouvernance-ia/04-anti-patterns.md` (anti-patterns récurrents à éviter).
4. ~~Lancer `07-pilotage/task-packs/TP-001-analyse-legacy.md`~~ — terminé (Lot 1 clos, voir `03-legacy/`).
5. ~~Lot 2 — Architecture et specs~~ : terminé. Arborescence, composants Divi, specs 5 pages secondaires, ADR-002 produits. Validation client des specs secondaires en attente (issue #26).
6. **[PRIORITÉ — avant TP-005]** Créer **ADR-003** (architecture one page — D-018) et réviser `05-specs/pages/homepage.md` pour absorber les sections Prestations, Formations, À propos avec modales "Voir plus". Voir `04-architecture/01-arborescence-site.md` note D-018 et `07-pilotage/02-journal-decisions.md`.
7. **En cours — Lot 3** : Lancer `07-pilotage/task-packs/TP-005-homepage-divi.md` (intégration homepage Divi) **après ADR-003**. Lire `08-handoffs/HO-001-pre-TP-005-homepage.md`. DDEV doit être démarré (`ddev start`).
8. Arbitrer les inconnues ouvertes : **I-04** (budget/délais), **I-08** (persona). I-15 résolue (photo). I-16 placeholder (bio). I-17 placeholder. I-18/19 placeholder (avis GBP).
