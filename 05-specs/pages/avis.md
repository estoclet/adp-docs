# Modale Avis — Spec (Contenu)

**Statut** : [FAIT] Révisé ADR-003 (D-018 one page) — prêt pour intégration  
**Dernière mise à jour** : 2026-04-27 — Promotion au statut FAIT ; ID #modal-avis assigné  
**Produit par** : Agent IA  
**Déclencheur** : Lien "Avis" dans la navigation principale  
**ID Modale cible** : `#modal-avis`  
**Template Divi** : Popup Divi 5 (Méthode A — Interactions + Visibilité)  
**Lié à** : `ADR-003`, `05-specs/pages/homepage.md`, `07-pilotage/02-journal-decisions.md`

> [FAIT] Décision 2026-04-24 : page à contenu léger → affichage en modale. Pas de page WordPress dédiée `/avis/` en V1.

---

## Objectif

Présenter une sélection d'avis clients Google Business Profile pour renforcer la réassurance, avec accès direct à la fiche GBP pour lire tous les avis.

---

## Contenu de la modale

| Élément | Description | Statut |
|---------|-------------|--------|
| Titre | "Avis clients" | [RECOMMANDÉ] |
| Note globale | Étoiles (x/5) + nombre d'avis | [INCONNUE — placeholder acceptable (D-016) — Julien HACHE remplace après livraison préprod] |
| Sélection d'avis | 6 à 8 avis éditorialisés (prénom + note + texte court) | [INCONNUE — placeholder acceptable (D-016) — Julien HACHE remplace après livraison préprod] |
| Lien externe | "Voir tous les avis →" → URL Google Business Profile | [INCONNUE — placeholder acceptable (D-016) — Julien HACHE remplace après livraison préprod] |
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

## Inconnues

| ID | Inconnue | Impact | Statut |
|----|----------|--------|--------|
| I-18 | Sélection de 6 à 8 avis GBP (prénom + texte + note) | Contenu de la modale | [INCONNUE — placeholder acceptable (D-016) — Julien HACHE remplace après livraison préprod] |
| I-19 | URL Google Business Profile (ou Maps) | Lien "Voir tous les avis" | [INCONNUE — placeholder acceptable (D-016) — Julien HACHE remplace après livraison préprod] |

---

## Note technique — Implémentation modale

[FAIT — D-019, 2026-04-25] La solution technique pour les modales est **Divi 5 natif — Méthode A (Interactions + Visibilité)**. Voir `04-architecture/03-composants-divi.md` pour le détail des 3 méthodes et la justification.

| Méthode retenue | Description | Éditabilité client | Source |
|-----------------|-------------|-------------------|--------|
| **Divi 5 — Interactions + Visibilité** | Contenu popup dans la page, masqué, déclenché par Interactions | Oui — Visual Builder | Elegant Themes docs, 2026-04-25 |

**Alternative** : si 5 popups surchargent le builder de la homepage, basculer sur Canvases + Interactions (Méthode B) — éditabilité préservée — décision en TP-006.

> Cette décision s'applique uniformément à toutes les modales du site (Avis, Contact, Prestations, Formations, À propos). [FAIT — D-018 + D-019]

---

## Signalement agent

- **Tâche accomplie** : spec modale `/avis/` — structure, contenu, inconnues identifiées
- **Hypothèses posées** : 6 à 8 avis sélectionnés (format éditorialisé), grille 2 colonnes desktop
- **Inconnues rencontrées** : I-18 (avis GBP), I-19 (URL GBP) — placeholder acceptable par D-016 (Eric STOCLET 2026-04-25) ; Julien HACHE remplace en préprod
- **Points à arbitrer** : choix final Méthode A vs B selon charge builder lors de TP-006
- **Prochaine étape recommandée** : implémenter en TP-006 (modales) avec Divi 5 Méthode A ; placeholders I-18/19 en place
