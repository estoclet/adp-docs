# Plan de travail — Lotissement

**Statut** : Proposition initiale — [À VALIDER] après arbitrage I-04 (budget / délais)  
**Dernière mise à jour** : 2026-04-25 — D-018 one page : TP-005 en attente (spec homepage à réviser) ; ajout TP-006 modales  
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
| Arbitrer les inconnues I-01, I-03, I-07 | ✅ Fait — résolus (voir `00-initialisation-projet.md`) |
| Arbitrer les inconnues I-04, I-08 | ⏳ En attente client |

**Bloquants** : Arbitrages client sur I-04 (budget/délais) et I-08 (persona).

---

### Lot 1 — Analyse du legacy
**Objectif** : Comprendre l'existant avant de concevoir le nouveau.  
**Statut** : Terminé — à valider  
**Livrable** : `03-legacy/` complété et validé

| Tâche | Task pack | Statut |
|-------|-----------|--------|
| Inventaire structure et plugins | TP-001 | ✅ Terminé — à valider |
| Analyse éditoriale du contenu | TP-002 | ✅ Terminé — à valider |
| Audit SEO et performances actuelles | TP-003 | Non planifié (V1 : hors périmètre) |
| Mapping URL legacy → nouveau | TP-004 | ✅ Terminé — à valider (1 proposition) |

**Bloquants** : Aucun — validation client requise sur les 3 livrables `03-legacy/`.

---

### Lot 2 — Architecture et design
**Objectif** : Valider l'arborescence, les types de contenus, la charte Divi.  
**Statut** : En cours — à valider client  
**Livrable** : `04-architecture/` validé + charte Divi + specs pages clés

| Tâche | Statut |
|-------|--------|
| Valider l'arborescence cible | ✅ Rédigée — à valider Julien HACHE |
| Définir la charte Divi (couleurs, typo) | ✅ [RÉSOLU] — `#1e3264` + `#0070c8`, Inter |
| Valider types de contenus et taxonomies | ✅ Rédigés — à valider |
| Rédiger specs pages principales | ✅ Fait — homepage validée client, 5 autres en brouillon |

**Bloquants** : Révision specs pour ADR-003 (one page — D-018). I-15 résolue (photo portrait). I-16/17/18/19 : placeholders acceptables (D-016). Validation client des specs secondaires (issue #26).

---

### Lot 3 — Développement et intégration
**Objectif** : Installer, configurer et construire le nouveau site dans `adp-app/`.  
**Statut** : En cours  
**Livrable** : Site fonctionnel en staging

| Tâche | Task pack | Statut |
|-------|-----------|--------|
| Installation WP + configuration de base | — | ✅ Fait — DDEV adp-app, WP 6.9.4 fr_FR |
| Installation et activation Divi | — | ✅ Fait — Divi 5.3.3, adp-divi-child v0.1.0 (commit 069d734) |
| Révision spec homepage (D-018 one page) | — | **[PRIORITÉ]** À faire avant TP-005 — voir ADR-003 |
| Intégration Divi homepage (one page + sections) | TP-005 | **En attente** — spec homepage à réviser d'abord (D-018) |
| Intégration des modales (Prestations, Formations, À propos, Avis, Contact) | TP-006 | [DÉPENDANCE] → TP-005 terminé — Divi 5 popup (D-019) |
| Configuration plugins (SEO, cache, sécurité, formulaires) | À planifier | À planifier |

**Bloquants** : Révision spec homepage (D-018 — ADR-003) avant TP-005. Licence Divi (activation sur adp-app — credentials Elegant Themes Julien HACHE). Éditabilité popup Divi à valider (D-019) avant livraison.

---

### Lot 4 — Migration du contenu
**Objectif** : Migrer le contenu qualifié depuis l'ancien site vers le nouveau.  
**Statut** : À démarrer (dépend de Lots 1 + 3)  
**Livrable** : Contenu migré, nettoyé, redirections en place

| Tâche | Statut |
|-------|--------|
| Export contenu legacy | [FAIT — I-06 résolu] Méthode retenue : WP XML natif (faible volume V1) |
| Import et nettoyage sur le nouveau site | À planifier |
| Configuration des redirections 301 | [FAIT — mapping TP-004 terminé] À implémenter en Lot 3 |
| Optimisation des images migrées | À planifier |

**Bloquants** : Aucun bloquant documentaire — démarrage conditionné à la fin du Lot 3.

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
