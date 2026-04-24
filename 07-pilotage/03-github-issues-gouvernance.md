# Gouvernance GitHub Issues

**Statut** : Actif
**Dernière mise à jour** : 2026-04-24
**Lié à** : `07-pilotage/01-lotissement.md`, `index.html` (dashboard)

> Le backlog de ce projet vit dans GitHub Issues sur le dépôt `estoclet/adp-docs`.  
> Les fichiers markdown d'`adp-docs` servent au cadrage, aux specs et à la gouvernance — pas au suivi de tâches.

---

## Tableau de bord en ligne

URL GitHub Pages : **https://estoclet.github.io/adp-docs/**

> Activation requise : Settings → Pages → Branch: `main` → Folder: `/ (root)` → Save.

---

## Taxonomie des labels

La lisibilité du dashboard dépend du respect strict de ces conventions de nommage.

### Labels de statut (colonne Kanban)

| Label | Couleur | Usage |
|-------|---------|-------|
| `statut: à faire` | Gris `#94A3B8` | Ticket créé, non démarré |
| `statut: en cours` | Bleu `#2563EB` | Travail en cours |
| `statut: bloqué` | Rouge `#DC2626` | Bloqué par une dépendance ou une inconnue |
| `statut: à valider` | Ambre `#D97706` | Produit, en attente de validation humaine |

> Ne pas ajouter d'autre label `statut:*`. Un ticket sans label de statut est automatiquement affiché en "À faire".

### Labels de lot (progression par lot)

| Label | Couleur | Lot |
|-------|---------|-----|
| `lot: 0 - cadrage` | Violet `#7C3AED` | Lot 0 |
| `lot: 1 - legacy` | Orange `#EA580C` | Lot 1 |
| `lot: 2 - architecture` | Cyan `#0891B2` | Lot 2 |
| `lot: 3 - développement` | Vert `#16A34A` | Lot 3 |
| `lot: 4 - migration` | Rose `#DB2777` | Lot 4 |
| `lot: 5 - recette` | Emeraude `#059669` | Lot 5 |

> Le préfixe `lot:` suivi d'un espace et d'un chiffre est requis pour que le dashboard calcule la progression.

### Labels de type

| Label | Couleur | Usage |
|-------|---------|-------|
| `type: spec` | Bleu clair `#60A5FA` | Rédaction ou validation d'une spec |
| `type: décision` | Jaune `#FBBF24` | Arbitrage requis |
| `type: analyse` | Indigo `#6366F1` | Analyse legacy, audit, inventaire |
| `type: dev` | Vert `#22C55E` | Développement WordPress / Divi |
| `type: contenu` | Rose `#F472B6` | Contenu à fournir (textes, visuels) |
| `type: bug` | Rouge `#EF4444` | Anomalie constatée |
| `type: recette-client` | Violet clair `#A78BFA` | Souhait ou remarque remontés par le client lors de sa recette |

### Labels de priorité

| Label | Couleur | Usage |
|-------|---------|-------|
| `priorité: haute` | Rouge foncé `#B91C1C` | Bloque d'autres tickets |
| `priorité: moyenne` | Gris `#6B7280` | Standard |
| `priorité: basse` | Gris clair `#D1D5DB` | À faire quand possible |

---

## Milestones GitHub (secondaires)

Les milestones GitHub correspondent aux lots du projet. Ils permettent de filtrer par lot depuis l'interface GitHub.

| Milestone | Titre | Lot |
|-----------|-------|-----|
| 1 | Lot 0 — Cadrage et gouvernance | Lot 0 |
| 2 | Lot 1 — Analyse du legacy | Lot 1 |
| 3 | Lot 2 — Architecture et design | Lot 2 |
| 4 | Lot 3 — Développement et intégration | Lot 3 |
| 5 | Lot 4 — Migration du contenu | Lot 4 |
| 6 | Lot 5 — Recette et mise en production | Lot 5 |

> **Note** : Le dashboard utilise les labels `lot:` pour la progression — les milestones GitHub sont un filtre complémentaire sur l'interface GitHub.

---

## Assignees

| GitHub login | Rôle |
|-------------|------|
| `estoclet` | Eric STOCLET — chef de projet |
| Agent IA | Non assignable sur GitHub — noter dans la description |

---

## Workflow d'un ticket

```
Création → [statut: à faire]
    ↓ travail démarré
[statut: en cours]
    ↓ blocage identifié
[statut: bloqué]  ← résoudre l'inconnue, puis
    ↓ production terminée
[statut: à valider]
    ↓ validation Eric STOCLET
Fermer le ticket (closed = Terminé sur le dashboard)
```

---

## Règles de création d'un ticket

1. **Un ticket = une tâche bornée et vérifiable.** Pas de tickets "Refonte du site" en entier.
2. **Titre** : commencer par l'action — "Rédiger la spec de /prestations/", "Analyser les plugins legacy"
3. **Label de lot** : obligatoire pour apparaître dans la progression.
4. **Label de statut** : omis = "À faire" (acceptable pour les nouveaux tickets).
5. **Label de type** : recommandé pour le filtrage.
6. **Description** : renseigner le lien vers les fichiers de référence (`adp-docs/...`).
7. **Référence au task pack** : si un task pack IA existe, le mentionner dans la description.

---

## Règle d'ouverture obligatoire par les agents

Avant d'entamer une action significative, un agent IA doit appliquer cette séquence :

1. Chercher s'il existe déjà une issue correspondant à l'action.
2. Si elle existe, travailler sous cette issue et la citer dans son output.
3. Si elle n'existe pas et que l'action est pertinente pour le suivi, créer l'issue immédiatement.
4. Ensuite seulement, commencer l'exécution de l'action.

### Une issue est considérée comme obligatoire si l'action :

- produit un livrable identifiable
- peut être bloquée ou validée
- prend plus qu'une vérification ponctuelle
- modifie le code, l'infrastructure locale, la documentation ou le contenu
- prépare ou exécute un task pack
- débloque ou structure un lot

### Une issue n'est pas requise si l'action :

- consiste seulement à lire, vérifier ou diagnostiquer très brièvement
- ne produit aucun livrable durable
- ne mérite pas d'apparaître dans le dashboard projet

> Règle d'arbitrage : **si l'action pourrait légitimement être suivie, revue ou priorisée, elle doit avoir une issue**.

---

## Configuration du dépôt privé

Si `estoclet/adp-docs` est privé :
1. Créer un Personal Access Token (PAT) sur https://github.com/settings/tokens
2. Permissions requises : `repo` (lecture)
3. Cliquer sur 🔑 dans le dashboard et coller le token
4. Il sera stocké dans `localStorage` (jamais transmis à un serveur externe)

> **Note** : GitHub Pages nécessite un dépôt public OU GitHub Pro/Team pour les dépôts privés.

---

## Ce que ce document ne contient pas

- Le backlog détaillé (vit dans les issues GitHub)
- Les specs des tâches (voir `05-specs/` et `07-pilotage/task-packs/`)
