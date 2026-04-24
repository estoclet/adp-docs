# Astuces De Pomme — Initialisation projet

**Statut** : Cadrage initial  
**Date** : 2026-04-24  
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
| 5 | Navigation : Accueil · Prestations · Formations · À propos · Avis · Blog · Contact | Réunion client 2026-04-23 |
| 6 | Périmètre : Assistance + Formation + Réseau + Démarches + Services à la personne | Réunion client 2026-04-23 |
| 7 | Tarif : 80€/h (40€ après crédit d'impôt) — téléphone : 06 51 31 15 37 | Réunion client 2026-04-23 |
| 8 | Environnement local : WordPress sous DDEV dans `adp-app/` — URL locale `http://adp.ddev.site` | Confirmé 2026-04-24 — issue #5 fermée |
| 9 | Préprod : VPS OVH — accès `ssh vps-adp` — chemin `/homez.31/astucesdib/www/dev/web` | Confirmé 2026-04-24 — issue #5 fermée |

---

## Inconnues bloquantes

Ces inconnues doivent être arbitrées par un humain avant que le travail concerné puisse avancer.

| # | Inconnue | Impact | Statut |
|---|----------|--------|--------|
| I-01 | ~~Hébergement cible~~ | Architecture, performance | [RÉSOLU — voir décisions 8 et 9] |
| I-02 | Volume réel du contenu legacy | Plan de migration | [ANALYSE REQUISE — TP-001] |
| I-03 | Nom de domaine : redirection ou changement ? | SEO, migration | [À ARBITRER] |
| I-04 | Budget et délais | Lotissement | [À ARBITRER] |
| I-05 | Plugins WP actifs sur le legacy | Compatibilité | [ANALYSE REQUISE — TP-001] |
| I-06 | Accès BDD legacy pour export | Migration de contenu | [À CONFIRMER] |
| I-07 | Palette hex exacte (extraire de la carte de visite) | Charte Divi — **bloque le Lot 3** | [À RECUEILLIR — Julien HACHE] |
| I-08 | Persona cible détaillé | Architecture info, rédaction | [À ARBITRER] |
| I-09 | Logo / monogramme PNG fond transparent | Header, footer, CTA | [À RECUEILLIR — Julien HACHE] |
| I-10 | Adresse email de contact | Homepage bloc 8, footer | [À RECUEILLIR — Julien HACHE] |
| I-11 | Zone / communes d'intervention | Homepage bloc 7 | [À RECUEILLIR — Julien HACHE] |
| I-12 | Textes descriptifs des cartes de services | Homepage blocs 3 et 5 | [À RECUEILLIR — Julien HACHE] |
| I-13 | Police validée | CSS global Divi | [À RECUEILLIR — Julien HACHE] |
| I-14 | Mention légale crédit d'impôt (texte exact) | Homepage bloc 4 | [À RECUEILLIR — Julien HACHE / comptable] |

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
4. Lancer `07-pilotage/task-packs/TP-001-analyse-legacy.md` pour inventorier l'existant.
5. Arbitrer les inconnues I-03, I-04, I-07, I-08 avant de poursuivre (I-01 résolue).
