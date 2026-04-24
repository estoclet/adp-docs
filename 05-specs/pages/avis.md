# Page Avis — Spec (Modale)

**Statut** : Brouillon — à valider par Eric STOCLET  
**Dernière mise à jour** : 2026-04-24  
**Produit par** : Agent IA — issue #25  
**URL cible** : N/A — **contenu affiché en modale** (décision chef de projet 2026-04-24)  
**Déclencheur** : lien "Avis" dans la navigation principale  
**Template Divi** : Popup / overlay Divi  
**Lié à** : `ADR-002`, `04-architecture/01-arborescence-site.md`, `05-specs/pages/homepage.md`

> [FAIT] Décision 2026-04-24 : page à contenu léger → affichage en modale. Pas de page WordPress dédiée `/avis/` en V1.

---

## Objectif

Présenter une sélection d'avis clients Google Business Profile pour renforcer la réassurance, avec accès direct à la fiche GBP pour lire tous les avis.

---

## Contenu de la modale

| Élément | Description | Statut |
|---------|-------------|--------|
| Titre | "Avis clients" | [RECOMMANDÉ] |
| Note globale | Étoiles (x/5) + nombre d'avis | [INCONNUE — I-18] |
| Sélection d'avis | 6 à 8 avis éditorialisés (prénom + note + texte court) | [INCONNUE — I-18] |
| Lien externe | "Voir tous les avis →" → URL Google Business Profile | [INCONNUE — I-19] |
| CTA bas de modale | Bouton "Prendre rendez-vous" → modale Contact | [FAIT] |

---

## Mise en forme

**Structure** :
- En-tête : titre + note globale (étoiles)
- Grille : 2 colonnes d'avis (desktop) → 1 colonne (mobile)
- Format carte : 5 étoiles + prénom + texte (100 mots max)
- Pied de modale : lien GBP + CTA

**Implémentation Divi** : overlay/popup Divi ou section masquée en CSS/JS selon la solution retenue pour toutes les modales du site. [À ARBITRER — voir note ci-dessous]

---

## Inconnues bloquantes

| ID | Inconnue | Impact |
|----|----------|--------|
| I-18 | Sélection de 6 à 8 avis GBP (prénom + texte + note) | Contenu de la modale — **bloquant** |
| I-19 | URL Google Business Profile (ou Maps) | Lien "Voir tous les avis" — **bloquant** |

---

## Note technique — Implémentation modale

[À ARBITRER] La solution technique pour les modales (Avis + Contact + pages légales) doit être homogène sur le site. Options en V1 avec Divi :

| Option | Description | Avantages | Inconvénients |
|--------|-------------|-----------|---------------|
| A | Divi Popup natif (module Divi intégré) | Pas de plugin, intégré | Fonctionnalités limitées |
| B | Plugin popup dédié (ex. WP Popups, Popup Maker) | Flexible, accessible | Plugin supplémentaire |
| C | Section masquée + CSS/JS custom | Contrôle total | Maintenance code |

> Cette décision est structurante — elle s'applique à toutes les modales (Contact, Avis, pages légales). Un seul choix doit être fait et appliqué uniformément. [À ARBITRER — Eric STOCLET]

---

## Signalement agent

- **Tâche accomplie** : spec modale `/avis/` — structure, contenu, inconnues identifiées
- **Hypothèses posées** : 6 à 8 avis sélectionnés (format éditorialisé), grille 2 colonnes desktop
- **Inconnues rencontrées** : I-18 (avis GBP), I-19 (URL GBP) — à recueillir auprès de Julien HACHE
- **Points à arbitrer** : solution technique modale unifiée pour le site (voir table ci-dessus)
- **Prochaine étape recommandée** : arbitrer la solution modale (impact toutes les modales du site), puis recueillir I-18 et I-19
