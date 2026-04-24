# Page Prestations — Spec

**Statut** : Brouillon — à valider par Eric STOCLET  
**Dernière mise à jour** : 2026-04-24  
**Produit par** : Agent IA — issue #25  
**URL cible** : `/prestations/`  
**Template Divi** : Template Prestations (sur mesure, hors Theme Builder)  
**Lié à** : `ADR-002`, `04-architecture/01-arborescence-site.md`, `05-specs/pages/homepage.md`

---

## Objectif de la page

Présenter l'ensemble des 6 prestations de manière détaillée, permettre au visiteur de qualifier son besoin, et le convertir vers un contact ou rendez-vous.

**Esprit** : page hub claire et rassurante — chaque prestation est autonome (ancre directe depuis le menu, les cards homepage, Google). [FAIT]

---

## Structure de la page

| # | Bloc | Type Divi |
|---|------|-----------|
| 1 | Header / navigation | Theme Builder — header global |
| 2 | Hero prestations | Section fond clair, 1 colonne centrée |
| 3 | Navigation rapide (pills ancres) | Section fond blanc, inline |
| 4 | Section Assistance Apple | Section 2 colonnes |
| 5 | Section Formation | Section 2 colonnes (inversée) |
| 6 | Section Réseau & Wi-Fi | Section 2 colonnes |
| 7 | Section Démarches administratives | Section 2 colonnes (inversée) |
| 8 | Section Sauvegardes & installation | Section 2 colonnes |
| 9 | Section Conseil | Section 2 colonnes (inversée) |
| 10 | Bandeau SAP / crédit d'impôt | Section fond bleu clair (réutilisation homepage) |
| 11 | Grand CTA de contact | Section fond bleu nuit (réutilisation homepage) |
| 12 | Footer | Theme Builder — footer global |

**Largeur conteneur** : identique à la homepage (1200–1280 px max). [FAIT]

---

## Bloc 2 — Hero prestations

**Type Divi** : Section fond très clair, centré, 1 colonne. [FAIT]

| Élément | Contenu proposé | Statut |
|---------|-----------------|--------|
| H1 | "Mes prestations" | [RECOMMANDÉ] |
| Sous-titre | "Assistance, formation et accompagnement Apple à domicile dans la région lilloise." | [RECOMMANDÉ] |
| CTA | Bouton bleu "Prendre rendez-vous" → `/contact/` | [FAIT] |

---

## Bloc 3 — Navigation rapide (ancres)

**Type Divi** : Ligne de pills/boutons texte cliquables, centrés, fond blanc.

| Pill | Ancre |
|------|-------|
| Assistance Apple | `#assistance` |
| Formation | `#formation` |
| Réseau & Wi-Fi | `#reseau` |
| Démarches administratives | `#demarches` |
| Sauvegardes & installation | `#sauvegardes` |
| Conseil | `#conseil` |

**Style** : identique aux pills de la homepage (Bloc 6). [FAIT]

---

## Blocs 4 à 9 — Sections prestations

Chaque section suit le même schéma :

| Élément | Description |
|---------|-------------|
| Ancre HTML | `id="[slug]"` sur la section |
| H2 | Titre de la prestation |
| Description | 3 à 6 lignes — détail, exemples concrets |
| Liste à puces | 4 à 6 cas d'usage ou exemples |
| CTA | "Prendre rendez-vous" → `/contact/` |
| Visuel | Icône ronde bleue (identique homepage) ou photo d'illustration [INCONNUE — I-visuels] |

**Alternance** : sections paires → 2 colonnes image/icône à gauche, texte à droite ; sections impaires → inversé. [RECOMMANDÉ]

---

### Section 4 — Assistance Apple (`#assistance`)

| Élément | Contenu proposé | Statut |
|---------|-----------------|--------|
| H2 | "Assistance Apple" | [RECOMMANDÉ] |
| Description | "Votre iPhone ne démarre plus, votre Mac est lent ou votre réseau Wi-Fi ne répond plus ? J'interviens à domicile pour diagnostiquer et résoudre votre problème rapidement, sans jargon." | [RECOMMANDÉ] |
| Exemples | Mac qui ne démarre plus ou trop lent · iPhone bloqué ou écran figé · iPad inaccessible · iCloud non synchronisé · Problème de connexion réseau ou Wi-Fi · Perte de données ou d'accès à un compte Apple | [RECOMMANDÉ] |

---

### Section 5 — Formation (`#formation`)

| Élément | Contenu proposé | Statut |
|---------|-----------------|--------|
| H2 | "Formation Apple" | [RECOMMANDÉ] |
| Description | "Apprenez à maîtriser votre iPhone, Mac ou iPad à votre rythme. Les séances sont personnalisées, à domicile, adaptées à votre niveau et à vos objectifs du moment." | [RECOMMANDÉ] |
| Exemples | Prise en main d'un nouvel appareil Apple · iCloud, FaceTime, Messages · Sécurité et vie privée · Photos, vidéos et partage · Usages avancés Mac (Spotlight, Finder, raccourcis) | [RECOMMANDÉ] |
| Lien complémentaire | "Voir le programme complet →" → `/formations/` | [FAIT] |

---

### Section 6 — Réseau & Wi-Fi (`#reseau`)

| Élément | Contenu proposé | Statut |
|---------|-----------------|--------|
| H2 | "Réseau & Wi-Fi" | [RECOMMANDÉ] |
| Description | "Wi-Fi instable, équipements déconnectés, box mal configurée ? J'analyse et optimise votre réseau domestique pour un fonctionnement fiable et sécurisé." | [RECOMMANDÉ] |
| Exemples | Configuration de box internet (Orange, SFR, Free, Bouygues) · Extension Wi-Fi (répéteurs, mesh) · Connexion TV, imprimante, NAS · Sécurisation réseau et Wi-Fi · Résolution de coupures ou lenteurs | [RECOMMANDÉ] |

---

### Section 7 — Démarches administratives (`#demarches`)

| Élément | Contenu proposé | Statut |
|---------|-----------------|--------|
| H2 | "Démarches administratives en ligne" | [RECOMMANDÉ] |
| Description | "Ameli, impots.gouv, FranceConnect, DémarchesSimplifiées, retraite… Je vous accompagne pas à pas pour accéder à vos droits et effectuer vos démarches en toute sérénité." | [RECOMMANDÉ] |
| Exemples | Espace Ameli et remboursements · Déclaration d'impôts en ligne · FranceConnect et identité numérique · Portail Ma Retraite · Demandes en ligne CAF, Pôle Emploi · Récupération de comptes ou mots de passe | [RECOMMANDÉ] |

---

### Section 8 — Sauvegardes & installation (`#sauvegardes`)

| Élément | Contenu proposé | Statut |
|---------|-----------------|--------|
| H2 | "Sauvegardes & installation" | [RECOMMANDÉ] |
| Description | "Protégez vos photos, contacts et documents avec iCloud ou Time Machine. J'installe, configure et vérifie vos sauvegardes pour ne rien perdre en cas de panne ou de changement d'appareil." | [RECOMMANDÉ] |
| Exemples | Configuration iCloud et gestion de l'espace · Time Machine (sauvegarde Mac) · Transfert de données vers un nouvel appareil · Installation et mise à jour macOS / iOS · Configuration d'un iPhone ou Mac neuf | [RECOMMANDÉ] |

---

### Section 9 — Conseil (`#conseil`)

| Élément | Contenu proposé | Statut |
|---------|-----------------|--------|
| H2 | "Conseil avant achat" | [RECOMMANDÉ] |
| Description | "Vous hésitez avant un achat ou ne savez pas quel équipement choisir ? Je vous guide avec un avis impartial, adapté à votre usage réel et à votre budget." | [RECOMMANDÉ] |
| Exemples | Choisir entre iPhone et iPad · Quel Mac pour quel usage ? · Accessoires utiles vs marketing · Quand réparer, quand remplacer ? · Comparaison opérateurs et forfaits | [RECOMMANDÉ] |

---

## Bloc 10 — Bandeau SAP

[FAIT] Identique au Bloc 4 de la homepage — réutiliser le module Divi Library.

---

## Bloc 11 — Grand CTA

[FAIT] Identique au Bloc 8 de la homepage — réutiliser le module Divi Library.

---

## SEO

| Élément | Valeur proposée | Statut |
|---------|----------------|--------|
| Balise title | "Prestations · Assistance Apple, Formation, Réseau à domicile — Astuces De Pomme" | [RECOMMANDÉ] |
| Meta description | "Assistance, formation, réseau Wi-Fi, démarches administratives, sauvegardes… Julien Hache intervient à votre domicile dans la région lilloise. 50 % de crédit d'impôt." | [RECOMMANDÉ] |
| H1 | "Mes prestations" | [RECOMMANDÉ] |
| Mot-clé principal | assistance apple domicile lille | [HYPOTHÈSE] |

---

## Comportement mobile

- Pills ancres en scroll horizontal ou 2 × 3. [RECOMMANDÉ]
- Sections 2 colonnes → empilement : visuel dessus, texte dessous. [FAIT]
- CTA pleine largeur. [FAIT]

---

## Dépendances

| Dépendance | Type | Bloque |
|-----------|------|--------|
| Header + Footer globaux | Composant Theme Builder | Toute la page |
| Module "Bandeau SAP" en Divi Library | Composant réutilisable | Bloc 10 |
| Module "Grand CTA" en Divi Library | Composant réutilisable | Bloc 11 |
| Visuels / icônes par prestation | Assets | Blocs 4 à 9 (icônes homepage OK ; photos illus INCONNUE) |

---

## Signalement agent

- **Tâche accomplie** : spec complète de `/prestations/` — 6 sections avec textes proposés, SEO, mobile, dépendances
- **Hypothèses posées** : alternance colonnes impaires/paires, contenu descriptif de chaque prestation (à valider/retoucher par Julien HACHE), titre H1 "Mes prestations"
- **Inconnues rencontrées** : visuels d'illustration par section (photos contextuelles) — les icônes de la homepage suffisent pour V1
- **Points à arbitrer** : présence ou non de photos d'illustration par section (les icônes de la homepage peuvent suffire en V1)
- **Prochaine étape recommandée** : validation de la structure et des textes par Eric STOCLET + Julien HACHE avant intégration Divi
