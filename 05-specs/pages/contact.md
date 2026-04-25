# Page Contact — Spec (Modale)

**Statut** : Brouillon — à valider par Eric STOCLET  
**Dernière mise à jour** : 2026-04-25 — D-019 : méthode popup Divi 5 Méthode A retenue  
**Produit par** : Agent IA — issue #25  
**URL cible** : N/A — **contenu affiché en modale** (décision chef de projet 2026-04-24)  
**Déclencheur** : bouton "Prendre rendez-vous" (header, hero, blocs CTA), lien "Contact" dans navigation  
**Template Divi** : Popup / overlay Divi  
**Lié à** : `ADR-002`, `04-architecture/01-arborescence-site.md`

> [FAIT] Décision 2026-04-24 : page à contenu léger → affichage en modale. Pas de page WordPress dédiée `/contact/` en V1.

---

## Objectif

Offrir un point de contact immédiat — téléphone en priorité, formulaire en seconde option — avec le minimum de friction possible.

---

## Contenu de la modale

**Structure** : 2 colonnes (desktop) → 1 colonne (mobile)

### Colonne gauche — Coordonnées directes

| Élément | Valeur | Statut |
|---------|--------|--------|
| Titre | "Parlons-en !" | [RECOMMANDÉ] |
| Sous-titre | "Un conseil, une question ou un rendez-vous ? Je vous réponds rapidement." | [RECOMMANDÉ] |
| Téléphone (prioritaire) | 06 51 31 15 37 | [FAIT] |
| Email | julien.hache@astucesdepomme.com | [FAIT — I-10 résolu] |
| Zone d'intervention | Région Lilloise, 60 km autour d'Houplines | [FAIT — I-11 résolu] |
| Horaires | [INCONNUE — I-17] | [INCONNUE] |

> [INCONNUE — I-17] Plages horaires d'intervention / disponibilité (ex : "Lundi–Vendredi, 9h–18h, sur rendez-vous"). À recueillir auprès de Julien HACHE.

### Colonne droite — Formulaire de contact

| Champ | Type | Obligatoire |
|-------|------|-------------|
| Prénom + Nom | Texte | Oui |
| Email | Email | Oui |
| Téléphone | Téléphone | Optionnel |
| Objet / Appareil | Liste : iPhone · Mac · iPad · Réseau · Démarches · Autre | Oui |
| Message | Textarea | Oui |
| Envoi | Bouton bleu "Envoyer ma demande" | — |

**Plugin formulaire** : WPForms Lite — [FAIT — retenu dans `01-cadrage/02-architecture-cible.md`, plugins V1]

---

## Comportement mobile

- Formulaire en pleine largeur sous les coordonnées. [FAIT]
- Téléphone cliquable (tel: href). [FAIT]
- Email cliquable (mailto: href). [FAIT]

---

## Réseaux sociaux (optionnel en pied de modale)

| Réseau | URL | Statut |
|--------|-----|--------|
| Facebook | https://www.facebook.com/astucesdepomme/ | [FAIT] |
| LinkedIn | https://www.linkedin.com/company/astuces-de-pomme/about/ | [FAIT] |

---

## Inconnues

| ID | Inconnue | Impact |
|----|----------|--------|
| I-17 | Horaires / disponibilité | Coordonnées — non bloquant, peut être omis en V1 |
| — | Plugin formulaire à confirmer | Développement Lot 3 |

---

## Note technique — Implémentation modale

[FAIT — D-019, 2026-04-25] Solution retenue : **Divi 5 — Interactions + Visibilité (Méthode A)** — native, sans plugin, éditabilité client dans le Visual Builder. Voir `04-architecture/03-composants-divi.md` et `05-specs/pages/avis.md` pour le détail des 3 méthodes.

**Implémentation** : dans TP-006.

---

## Signalement agent

- **Tâche accomplie** : spec modale Contact — coordonnées, formulaire, mobile, réseaux
- **Hypothèses posées** : horaires non bloquants en V1 (I-17)
- **Inconnues rencontrées** : I-17 (horaires — non bloquant V1)
- **Points à arbitrer** : recueillir I-17 (horaires) si souhaité avant préprod
- **Prochaine étape recommandée** : implémenter en TP-006 avec Divi 5 Méthode A
