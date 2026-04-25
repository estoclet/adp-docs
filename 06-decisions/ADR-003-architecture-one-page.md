# ADR-003 — Architecture one page : homepage comme hub unique + modales

**Statut** : Accepté  
**Date** : 2026-04-25  
**Décideurs** : Julien HACHE (client), Eric STOCLET (chef de projet)  
**Lié à** : `D-018`, `D-019`, `04-architecture/01-arborescence-site.md`, `05-specs/pages/homepage.md`, `ADR-002`

---

## Contexte

La structure initiale du site (Lot 2) prévoyait un site multi-pages : une page dédiée pour chaque item du menu (Prestations, Formations, À propos), plus des modales pour les contenus légers (Avis, Contact — D-014). [FAIT — D-004, D-005]

Le 2026-04-25, Julien HACHE a confirmé une orientation **site one page** : la page d'accueil sera le hub unique de tout le contenu principal. Des liens "Voir plus" ouvriront des modales pour le contenu détaillé. [FAIT — D-018]

Condition associée (Eric STOCLET) : les modales doivent être **éditables par Julien HACHE en autonomie** dans le backoffice Divi, sans intervention technique. L'option Divi 5 popup natif est préférentielle si l'éditabilité est confirmée. [FAIT — D-019]

Contraintes connues :
- WordPress + Divi 5.3.3 installés [FAIT]
- Divi 5 dispose de 3 méthodes natives pour les popups (source : Elegant Themes docs) [FAIT — 2026-04-25]
- **Méthode retenue (D-019)** : Interactions + Visibilité — contenu dans la page, éditable directement par le client dans le Visual Builder [FAIT — source Elegant Themes 2026-04-25]
- Alternative si trop de popups dans la page : Canvases + Interactions (Méthode B) — éditabilité préservée
- 11 pages WordPress publiées — certaines peuvent devenir des ancres ou redirections plutôt que des pages réelles [FAIT — à arbitrer]

---

## Décision

Le site Astuces De Pomme V1 adopte une **architecture one page** : la homepage (`/`) est le seul point d'entrée public pour tout le contenu de navigation (Accueil, Prestations, Formations, À propos). Les items de menu déclenchent un scroll vers la section correspondante sur la homepage. Le contenu détaillé de chaque section est accessible via un lien "Voir plus" qui ouvre une **modale** Divi. Les modales Avis et Contact restent inchangées (D-014). Les pages légales restent en pages WordPress dédiées (utile pour l'indexation SEO et les obligations légales).

---

## Raisons

1. **Demande client explicite** (2026-04-25) — Julien HACHE a exprimé cette préférence directement.
2. **Simplicité d'utilisation** — une seule page à entretenir pour le client ; tout le contenu visible d'un seul scroll.
3. **Cohérence avec D-014** — Avis et Contact étaient déjà en modales ; on uniformise le pattern à l'ensemble du site.
4. **Réduction du poids WordPress** — moins de pages à maintenir, moins de routes à gérer.
5. **Éditabilité client** — si Divi 5 popup permet l'édition autonome, Julien HACHE n'a besoin d'aucun accès développeur pour maintenir le contenu.

---

## Alternatives écartées

| Alternative | Raison d'abandon |
|------------|-----------------|
| Multi-pages (initial Lot 2) | Contredit la volonté client exprimée le 2026-04-25 |
| One page sans modales (tout sur la homepage) | Page trop longue, lisibilité dégradée ; contenu détaillé trop volumineux pour être intégré directement |
| Modales via plugin tiers | Ajoute un plugin au socle V1 déjà arbitré (D-011) ; Divi natif préféré si fonctionnel |

---

## Conséquences

### Positives
- Homepage devient la spec pivot de tout le projet — un seul document de référence.
- Navigation anchor-based : plus fluide pour l'utilisateur, pas de chargement de page.
- Modales Divi éditables : autonomie totale du client post-livraison.
- Cohérence totale du pattern modale sur le site.

### Négatives / risques
- **Spec homepage à réviser** : `05-specs/pages/homepage.md` doit être réécrite pour intégrer les sections Prestations, Formations, À propos. Travail non négligeable — à faire avant TP-005.
- **SEO** : les URLs `/prestations/`, `/formations/`, `/a-propos/` ne seront plus des pages réelles. Si elles sont référencées (Google, annuaires), mettre en place des redirections 301 vers `/#prestations`, etc. — impact faible car le site est en refonte.
- **Pages WordPress orphelines** : les 11 pages publiées incluent `prestations`, `formations`, `a-propos` — décider si on les conserve comme ancres, redirections, ou on les supprime.
- **Divi 5 popup editability** : [FAIT — source Elegant Themes 2026-04-25] La Méthode A (Interactions + Visibilité) permet l'édition autonome des popups par Julien HACHE directement dans le Visual Builder. Risque résiduel : si les 5 popups surchargent la page dans le builder, basculer sur la Méthode B (Canvases).
- **Complexité homepage** : une seule page très dense — les tests responsive et performance seront plus importants.

### Risque atténué
- L'éditabilité Divi sera vérifiée en TP-006 (implémentation modales) avant la livraison préprod.
- Les pages WordPress orphelines peuvent être conservées transitoirement et supprimées ou redirigées après validation.

---

## Impact sur les documents existants

| Document | Action requise |
|----------|---------------|
| `05-specs/pages/homepage.md` | **Réécriture** — absorber les sections Prestations, Formations, À propos avec blocs summary + liens "Voir plus" → modale |
| `05-specs/pages/prestations.md` | Devient la spec du **contenu de la modale Prestations** |
| `05-specs/pages/formations.md` | Devient la spec du **contenu de la modale Formations** |
| `05-specs/pages/a-propos.md` | Devient la spec du **contenu de la modale À propos** |
| `04-architecture/01-arborescence-site.md` | Mis à jour — navigation anchor-based documentée |
| `07-pilotage/task-packs/TP-005-homepage-divi.md` | Mise à jour des prérequis — homepage spec révisée avant de démarrer |

---

## Révision

Cette décision sera révisée si :
- Julien HACHE revient sur l'orientation one page après visualisation d'une maquette.
- Divi 5 ne supporte pas l'édition autonome des popups par le client — nécessiterait un arbitrage technique alternatif.
- Le référencement SEO exige des pages dédiées (ex. campagne Google Ads sur `/prestations/`).

---

## Historique

| Date | Auteur | Changement |
|------|--------|-----------|
| 2026-04-25 | Agent IA (boucle gouvernance) | Création — sur décision Julien HACHE 2026-04-25 (D-018) |
| 2026-04-25 | Agent IA (boucle gouvernance) | Mise à jour — popup Divi 5 Méthode A documentée (D-019, source Elegant Themes) |
