# Modale Formations — Spec (Contenu)

**Statut** : [FAIT] Révisé ADR-003 (D-018 one page) — prêt pour intégration  
**Dernière mise à jour** : 2026-04-27 — Transformation page → contenu de modale  
**Produit par** : Agent IA  
**Déclencheur** : Lien "Voir plus" du Bloc 5 (Formations) de la Homepage  
**ID Modale cible** : `#modal-formations`  
**Template Divi** : Popup Divi 5 (Méthode A — Interactions + Visibilité)  
**Lié à** : `ADR-003`, `05-specs/pages/homepage.md`, `04-architecture/03-composants-divi.md`

---

## Objectif du contenu

Détailler l'offre de formation Apple (iPhone, Mac, iPad, iCloud) pour les visiteurs souhaitant comprendre la méthode pédagogique et les thématiques couvertes.

---

## Structure du contenu (dans la modale)

La modale est un conteneur défilable (scrollable) organisé en sections claires.

| # | Bloc | Type Divi | Notes |
|---|------|-----------|-------|
| 1 | Titre de la modale | H2 / Titre de section | "Apprendre à votre rythme" |
| 2 | L'approche pédagogique | Ligne 3 colonnes | Domicile / Rythme / Sans jargon |
| 3 | Thématiques de formation | Grille de cartes (2x3) | Communication, iCloud, Multimédia, Sécurité, Système |
| 4 | Infos pratiques (Tarifs/Zone) | Ligne 2 ou 3 colonnes | Rappel des bénéfices SAP |
| 5 | Bouton de fermeture / CTA | Bouton centré | "Prendre rendez-vous" |

---

## Détail des sections

### L'approche pédagogique
- **À votre domicile** : Je me déplace chez vous pour une formation en situation réelle sur vos propres appareils.
- **À votre rythme** : Chaque séance est personnalisée selon vos besoins et votre niveau actuel.
- **Sans jargon** : Des explications simples et concrètes pour une compréhension immédiate.

### Thématiques de formation
1. **Communication** : Appels, FaceTime, Messages, Mail, gestion des contacts.
2. **iCloud & Sauvegardes** : Synchronisation de vos appareils, gestion de l'espace, sécurité des données.
3. **Multimédia** : Organiser ses photos, créer des albums partagés, podcasts et streaming.
4. **Sécurité & Vie privée** : Identifiant Apple, mots de passe, protection contre les arnaques.
5. **Système & Réseau** : Maîtriser le Finder sur Mac, les réglages système, configurer son Wi-Fi.

### Infos pratiques
- **Tarif unique** : 80€/h — soit **40€/h après crédit d'impôt** (Service à la personne).
- **Format** : Séances de 1h à 2h selon vos besoins.
- **Zone** : Région lilloise (60 km autour d'Houplines).

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
- **Mobile** : Contenu empilé verticalement, cartes en pleine largeur.

---

## Signalement agent

- **Modification** : Transformation complète de la spec page en spec contenu modale.
- **Simplification** : Retrait du Hero complexe et des sections SEO.
- **ID cible** : `#modal-formations` défini pour l'intégration Divi.
- **Cohérence** : Alignement sur ADR-003.
