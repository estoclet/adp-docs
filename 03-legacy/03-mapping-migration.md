# Mapping de migration — URLs legacy → nouveau site

**Statut** : Squelette — à compléter après analyse legacy et validation arborescence  
**Dernière mise à jour** : 2026-04-24  
**Produit par** : Chef de projet — structure initiale  
**Lié à** : `02-analyse-contenu.md`, `04-architecture/01-arborescence-site.md`, `01-cadrage/04-strategie-migration.md`

> **Note agent** : Ne pas remplir ce document avant que les deux conditions suivantes soient réunies : (1) l'analyse legacy est terminée (`01-inventaire-legacy.md` et `02-analyse-contenu.md` complétés), (2) l'arborescence cible est validée (`04-architecture/01-arborescence-site.md`). Un mapping partiel ou basé sur des hypothèses est inutilisable et dangereux.

> [DÉPENDANCE] Dépend de I-03 (changement de domaine ou redirection).

---

## Règles de mapping

1. **Une URL legacy = une ligne** dans ce tableau.
2. **Pas de renvoi vers la page d'accueil** par défaut — trouver la page cible la plus pertinente.
3. **Toute URL sans équivalent cible** est à signaler `[À ARBITRER]` avant de choisir la redirection.
4. **Le mapping validé est une source de vérité** — ne pas le dupliquer ailleurs.

---

## Table de mapping

> À compléter après analyse legacy et validation de l'arborescence cible.

| URL source (legacy) | Titre legacy | Décision contenu | URL cible (nouveau site) | Type redirection | Statut |
|--------------------|-------------|-----------------|--------------------------|-----------------|--------|
| /exemple-article | Titre de l'article | Garder | /astuces/iphone/exemple | 301 | [À FAIRE] |
| /exemple-2 | Titre 2 | Supprimer | /astuces/iphone/ (catégorie) | 301 | [À FAIRE] |
| … | … | … | … | … | … |

---

## Catégories de redirection

| Type | Code HTTP | Quand utiliser |
|------|-----------|----------------|
| Redirect permanente | 301 | Contenu migré ou supprimé définitivement |
| Page de catégorie | 301 → catégorie | Contenu supprimé sans équivalent précis |
| Page d'accueil | 301 → / | Uniquement si aucune catégorie pertinente |
| *(Ne pas utiliser)* | 302 | Éviter — Google traite en temporaire |

---

## URLs à fort enjeu SEO (priorité 1)

> Lister ici les URLs avec le plus de trafic ou de backlinks — à traiter en priorité absolue.

| URL source | Trafic estimé | Backlinks | URL cible validée | Statut |
|-----------|--------------|-----------|------------------|--------|
| | | | | |

---

## URLs non résolues (en attente d'arbitrage)

> URLs pour lesquelles aucune URL cible évidente n'a été identifiée.

| URL source | Titre | Problème | [À ARBITRER] par |
|-----------|-------|----------|-----------------|
| | | | Chef de projet |

---

## Signalement agent

_(À compléter par l'agent qui réalise le mapping)_

- **Tâche accomplie** :
- **Hypothèses posées** :
- **Inconnues rencontrées** :
- **Points à arbitrer** :
- **Prochaine étape recommandée** :
