# Modale À propos — Spec (Contenu)

**Statut** : [FAIT] Révisé ADR-003 (D-018 one page) — prêt pour intégration  
**Dernière mise à jour** : 2026-04-27 — Transformation page → contenu de modale  
**Produit par** : Agent IA  
**Déclencheur** : Lien "Voir plus" du Bloc 7 (À propos) de la Homepage  
**ID Modale cible** : `#modal-a-propos`  
**Template Divi** : Popup Divi 5 (Méthode A — Interactions + Visibilité)  
**Lié à** : `ADR-003`, `05-specs/pages/homepage.md`, `04-architecture/03-composants-divi.md`

---

## Objectif du contenu

Présenter Julien Hache, son parcours, ses valeurs et rassurer sur le cadre légal (agrément Service à la personne).

---

## Structure du contenu (dans la modale)

La modale est un conteneur défilable (scrollable).

| # | Bloc | Type Divi | Notes |
|---|------|-----------|-------|
| 1 | Titre de la modale | H2 / Titre de section | "Qui est votre interlocuteur ?" |
| 2 | Présentation / Photo | Ligne 2 colonnes | Photo Julien HACHE + texte bio |
| 3 | Mes Valeurs | Ligne 3 colonnes | Clarté / Proximité / Honnêteté |
| 4 | Agrément SAP (Confiance) | Ligne 2 colonnes | Texte légal + Logo SAP |
| 5 | Bouton de fermeture / CTA | Bouton centré | "Prendre rendez-vous" |

---

## Détail des sections

### Présentation & Parcours
- **Photo** : `adp-app/assets/design/julien-hache-portrait.png` (810×552 px).
- **Texte Bio** : [PLACEHOLDER] "Julien Hache, technicien Apple indépendant. Passionné par l'écosystème Apple depuis plus de X années, j'ai créé Astuces De Pomme pour apporter une aide concrète et humaine aux utilisateurs." (Julien HACHE remplacera ce texte).

### Valeurs
- **Clarté** : J'explique sans jargon. Vous comprenez ce qui se passe sur vos appareils.
- **Proximité** : Un service local, à domicile, adapté à votre emploi du temps.
- **Honnêteté** : Un conseil impartial. Si une réparation n'est pas rentable, je vous le dis.

### Agrément SAP & Données Légales
- **Texte** : "Astuces De Pomme est un service à la personne déclaré (N° SAP 502282080). Cet agrément vous permet de bénéficier de 50 % de crédit d'impôt."
- **Mention obligatoire** : "Dans les limites prévues à l'article 199 sexdecies du CGI."
- **SIRET** : 50228208000022.

---

## CTA de sortie

En bas de modale, un bouton principal :
- **Libellé** : "Prendre rendez-vous"
- **Action** : Fermer la modale et scroller vers `#contact` sur la homepage.

---

## Design & Comportement

- **Fond** : Blanc.
- **Typographie** : Identique homepage (`Inter`).
- **Fermeture** : Croix en haut à droite + clic à l'extérieur + bouton de sortie.
- **Mobile** : Photo au-dessus du texte, colonnes empilées.

---

## Signalement agent

- **Modification** : Transformation complète de la spec page en spec contenu modale.
- **Asset** : Utilisation de la photo portrait récupérée (D-020).
- **ID cible** : `#modal-a-propos` défini pour l'intégration Divi.
- **Cohérence** : Alignement sur ADR-003.
