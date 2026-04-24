# Mapping de migration — URLs legacy → nouveau site

**Statut** : En cours — mapping initial basé sur le legacy réel et l'arborescence cible validée  
**Dernière mise à jour** : 2026-04-24  
**Produit par** : Agent IA — première proposition de mapping  
**Lié à** : `02-analyse-contenu.md`, `04-architecture/01-arborescence-site.md`, `01-cadrage/04-strategie-migration.md`

> **Note agent** : Ne pas remplir ce document avant que les deux conditions suivantes soient réunies : (1) l'analyse legacy est terminée (`01-inventaire-legacy.md` et `02-analyse-contenu.md` complétés), (2) l'arborescence cible est validée (`04-architecture/01-arborescence-site.md`). Un mapping partiel ou basé sur des hypothèses est inutilisable et dangereux.

> [FAIT] I-03 est validé : le domaine public est conservé (`https://astucesdepomme.com`).  
> [RÈGLE] Ce mapping porte donc sur les URLs internes legacy → nouvelles URLs internes.

---

## Règles de mapping

1. **Une URL legacy = une ligne** dans ce tableau.
2. **Pas de renvoi vers la page d'accueil** par défaut — trouver la page cible la plus pertinente.
3. **Toute URL sans équivalent cible** est à signaler `[À ARBITRER]` avant de choisir la redirection.
4. **Le mapping validé est une source de vérité** — ne pas le dupliquer ailleurs.

---

## Table de mapping

| URL source (legacy) | Titre legacy | Décision contenu | URL cible (nouveau site) | Type redirection | Statut |
|--------------------|-------------|-----------------|--------------------------|-----------------|--------|
| / | Accueil | Réécrire | / | 301 implicite / remplacement direct | [PROPOSITION] |
| /mentions-legales | Mentions legales | Réécrire | /mentions-legales/ | 301 | [PROPOSITION] |
| /cgv | CGV | Réécrire | /cgv/ | 301 | [VALIDÉ] |
| /infos-fiscales | Information Fiscale | Réécrire | /infos-fiscales/ | 301 | [VALIDÉ] |
| /confidentialite | Confidentialité | Réécrire | /politique-confidentialite/ | 301 | [PROPOSITION] |

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

> Le legacy ne présente pas de corpus d'articles publié. Les URLs prioritaires sont donc les 5 pages existantes.

| URL source | Trafic estimé | Backlinks | URL cible validée | Statut |
|-----------|--------------|-----------|------------------|--------|
| / | [INCONNUE] | [INCONNUE] | / | [PROPOSITION] |
| /mentions-legales | [INCONNUE] | [INCONNUE] | /mentions-legales/ | [PROPOSITION] |
| /confidentialite | [INCONNUE] | [INCONNUE] | /politique-confidentialite/ | [PROPOSITION] |
| /cgv | [INCONNUE] | [INCONNUE] | /cgv/ | [VALIDÉ] |
| /infos-fiscales | [INCONNUE] | [INCONNUE] | /infos-fiscales/ | [VALIDÉ] |

---

## URLs non résolues (en attente d'arbitrage)

> URLs pour lesquelles aucune URL cible évidente n'a été identifiée.

| URL source | Titre | Problème | [À ARBITRER] par |
|-----------|-------|----------|-----------------|
| | | | |

---

## Observations de mapping

- [FAIT] Le legacy réel ne contient que 5 pages publiées et aucun article publié.
- [FAIT] Le mapping ne dépend plus d'un changement de domaine.
- [FAIT] Les pages légales obligatoires ont déjà des cibles naturelles dans l'arborescence cible pour `mentions-legales` et `politique-confidentialite`.
- [FAIT] `/cgv` reste une page dédiée sur le nouveau site.
- [FAIT] `/infos-fiscales` reste une page dédiée sur le nouveau site.
- [FAIT] `/tarifs-prestations/` reste distincte de `/infos-fiscales/` et devra contenir une mention + un renvoi vers cette page fiscale.

---

## Signalement agent

- **Tâche accomplie** : premier mapping des 5 URLs réellement publiées sur le legacy, en cohérence avec le domaine conservé et l'arborescence cible actuelle.
- **Hypothèses posées** : aucune hypothèse de trafic ou de backlinks ; seules des propositions de destination ont été formulées quand la cible est déjà identifiable.
- **Inconnues rencontrées** : absence de données SEO fines (trafic, backlinks, requêtes réelles).
- **Points à arbitrer** : aucun arbitrage structurel majeur restant sur les 5 pages publiées ; reste à confirmer l'ajout explicite de `/cgv/` et `/infos-fiscales/` dans l'arborescence cible documentaire si souhaité.
- **Prochaine étape recommandée** : considérer le mapping V1 comme pratiquement validé, puis répercuter si besoin ces deux pages explicites dans l'arborescence cible.
