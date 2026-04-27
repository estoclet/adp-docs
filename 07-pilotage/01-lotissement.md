# Plan de travail — Lotissement

**Statut** : Proposition initiale — [À VALIDER] après arbitrage I-04 (budget / délais)  
**Dernière mise à jour** : 2026-04-27 — TP-005 terminé (homepage Divi intégrée, Theme Builder actif, smoke 4/4) ; TP-006 à lancer  
**Chef de projet** : Eric STOCLET  
**Client** : Julien HACHE  
**Lié à** : `00-initialisation-projet.md`, `07-pilotage/task-packs/`

---

## Lots du projet

### Lot 0 — Cadrage et gouvernance documentaire
**Objectif** : Poser les bases documentaires avant tout développement.  
**Statut** : Terminé [À VALIDER]  
**Livrable** : `adp-docs/` complet et validé

| Tâche | Statut |
|-------|--------|
| Créer l'arborescence `adp-docs/` | ✅ Fait |
| Rédiger `00-initialisation-projet.md` | ✅ Fait |
| Rédiger les règles IA | ✅ Fait |
| Arbitrer les inconnues I-01, I-03, I-07 | ✅ Fait — résolus |
| Arbitrer les inconnues I-04, I-08 | ⏳ En attente client |

---

### Lot 1 — Analyse du legacy
**Objectif** : Comprendre l'existant avant de concevoir le nouveau.  
**Statut** : Terminé — à valider  
**Livrable** : `03-legacy/` complété et validé

| Tâche | Task pack | Statut |
|-------|-----------|--------|
| Inventaire structure et plugins | TP-001 | ✅ Terminé |
| Analyse éditoriale du contenu | TP-002 | ✅ Terminé |
| Audit SEO et performances actuelles | TP-003 | Hors périmètre V1 |
| Mapping URL legacy → nouveau | TP-004 | ✅ Terminé |

---

### Lot 2 — Architecture et design
**Objectif** : Valider l'arborescence, les types de contenus, la charte Divi.  
**Statut** : Terminé [À VALIDER]  
**Livrable** : `04-architecture/` validé + charte Divi + specs modales

| Tâche | Statut |
|-------|--------|
| Valider l'arborescence cible | ✅ Révisée ADR-003 (One-page) |
| Définir la charte Divi (couleurs, typo) | ✅ Fait — #1e3264, #0070c8, Inter |
| Valider types de contenus et taxonomies | ✅ Fait — pas de CPT en V1 |
| Rédiger specs pages et modales | ✅ Révisées ADR-003 — Prestations, Formations, À propos |

---

### Lot 3 — Développement et intégration
**Objectif** : Installer, configurer et construire le nouveau site dans `adp-app/`.  
**Statut** : En cours  
**Livrable** : Site fonctionnel en staging

| Tâche | Task pack | Statut |
|-------|-----------|--------|
| Installation WP + configuration de base | — | ✅ Fait |
| Installation et activation Divi | — | ✅ Fait |
| Révision spec homepage (D-018 one page) | — | ✅ Fait — ADR-003 intégré |
| Intégration Divi homepage (one page) | TP-005 | ✅ Terminé — à valider Eric STOCLET |
| Intégration des modales (TP-006) | TP-006 | ⏳ À lancer |
| Configuration plugins (SEO, Redirection) | — | ✅ Fait — redirections.json prêt |

---

### Lot 4 — Migration du contenu
**Objectif** : Migrer le contenu qualifié depuis l'ancien site vers le nouveau.  
**Statut** : En préparation  
**Livrable** : Contenu migré, nettoyé, redirections en place

| Tâche | Statut |
|-------|--------|
| Export contenu legacy | ✅ Fait |
| Configuration des redirections 301 | ✅ Fait — redirections-v1.json prêt |
| Plan de marquage GA4 | ✅ Fait — plan-marquage.md prêt |

---

### Lot 5 — Recette et mise en production
**Objectif** : Valider le site avant la bascule publique.  
**Statut** : À démarrer
