# Plan de travail — Lotissement

**Statut** : Proposition initiale — [À VALIDER] après arbitrage I-04 (budget / délais)  
**Dernière mise à jour** : 2026-04-24  
**Chef de projet** : Eric STOCLET  
**Client** : Julien HACHE  
**Lié à** : `00-initialisation-projet.md`, `07-pilotage/task-packs/`

> **Note** : Ce document propose un découpage en lots. Le backlog détaillé (user stories, tâches) vit dans l'outil de gestion de projet, pas ici. Ce document définit les **frontières des lots et leurs livrables**.

---

## Lots du projet

### Lot 0 — Cadrage et gouvernance documentaire
**Objectif** : Poser les bases documentaires avant tout développement.  
**Statut** : En cours  
**Livrable** : `adp-docs/` complet et validé

| Tâche | Statut |
|-------|--------|
| Créer l'arborescence `adp-docs/` | ✅ Fait |
| Rédiger `00-initialisation-projet.md` | ✅ Fait |
| Rédiger les règles IA | ✅ Fait |
| Arbitrer les inconnues I-01, I-03, I-04, I-07, I-08 | ⏳ En attente client |

**Bloquants** : Arbitrages client sur les inconnues.

---

### Lot 1 — Analyse du legacy
**Objectif** : Comprendre l'existant avant de concevoir le nouveau.  
**Statut** : À démarrer (dépend de Lot 0)  
**Livrable** : `03-legacy/` complété et validé

| Tâche | Task pack | Statut |
|-------|-----------|--------|
| Inventaire structure et plugins | TP-001 | À lancer |
| Analyse éditoriale du contenu | TP-002 | Après TP-001 |
| Audit SEO et performances actuelles | TP-003 | Après TP-001 |
| Mapping URL legacy → nouveau | TP-004 | Après TP-002 + arborescence validée |

**Bloquants** : Accès au site legacy (adp-legacy/ disponible [FAIT]). Accès BDD pour volume exact (I-06).

---

### Lot 2 — Architecture et design
**Objectif** : Valider l'arborescence, les types de contenus, la charte Divi.  
**Statut** : À démarrer (dépend de Lot 1 + arbitrages I-07, I-08)  
**Livrable** : `04-architecture/` validé + charte Divi + maquettes pages clés

| Tâche | Statut |
|-------|--------|
| Valider l'arborescence cible | [À ARBITRER — Julien HACHE] |
| Définir la charte Divi (couleurs, typo) | [DÉPENDANCE] → I-07 |
| Valider types de contenus et taxonomies | [À ARBITRER] |
| Valider specs pages principales | [À FAIRE] |

**Bloquants** : Arbitrage I-07 (identité graphique), I-08 (persona), analyse legacy.

---

### Lot 3 — Développement et intégration
**Objectif** : Installer, configurer et construire le nouveau site dans `adp-app/`.  
**Statut** : À démarrer (dépend de Lot 2)  
**Livrable** : Site fonctionnel en staging

| Tâche | Statut |
|-------|--------|
| Installation WP + configuration de base | À planifier |
| Installation et activation Divi | À planifier |
| Développement des composants globaux (header, footer, CTA) | À planifier |
| Intégration des templates de pages | À planifier |
| Configuration plugins (SEO, cache, sécurité, formulaires) | À planifier |

**Bloquants** : Hébergement staging (I-01), charte Divi validée, specs pages validées.

---

### Lot 4 — Migration du contenu
**Objectif** : Migrer le contenu qualifié depuis l'ancien site vers le nouveau.  
**Statut** : À démarrer (dépend de Lots 1 + 3)  
**Livrable** : Contenu migré, nettoyé, redirections en place

| Tâche | Statut |
|-------|--------|
| Export contenu legacy | [DÉPENDANCE] → I-06 + méthode d'export |
| Import et nettoyage sur le nouveau site | À planifier |
| Configuration des redirections 301 | [DÉPENDANCE] → mapping TP-004 |
| Optimisation des images migrées | À planifier |

**Bloquants** : Mapping validé, accès BDD ou export WP XML.

---

### Lot 5 — Recette et mise en production
**Objectif** : Valider le site avant la bascule publique.  
**Statut** : À démarrer (dépend de Lots 3 + 4)  
**Livrable** : Site en production, ancien site désactivé

| Tâche | Statut |
|-------|--------|
| Tests fonctionnels complets | À planifier |
| Tests de performance (PageSpeed) | À planifier |
| Vérification des redirections | À planifier |
| Soumission sitemap Google Search Console | À planifier |
| Formation client WP/Divi [HYPOTHÈSE] | [À ARBITRER] |
| Bascule DNS et mise en production | À planifier |

---

## Dépendances inter-lots

```
Lot 0 → Lot 1 → Lot 2 → Lot 3 → Lot 4 → Lot 5
              ↘              ↗
          Arbitrages client
```

---

## Ressources connues

| Ressource | Rôle | Statut |
|-----------|------|--------|
| Eric STOCLET | Chef de projet | [FAIT] |
| Julien HACHE | Client, propriétaire du contenu | [FAIT] |
| Agents IA (Claude, etc.) | Production documentaire, analyse | [FAIT] |
| Développeur WP/Divi | Intégration technique Lot 3 | [À IDENTIFIER] |

---

## Ce que ce document ne contient pas

- Les user stories ou tâches détaillées (dans l'outil de gestion de projet)
- Les task packs agents (voir `07-pilotage/task-packs/`)
- Le calendrier détaillé (dépend de I-04)
