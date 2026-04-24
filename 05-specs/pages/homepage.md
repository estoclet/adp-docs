# Page d'accueil — Spec

**Statut** : Validé client — Julien HACHE (réunion 2026-04-23)
**Dernière mise à jour** : 2026-04-24
**Produit par** : Eric STOCLET, d'après brief client
**URL cible** : `/`
**Template Divi** : Template Accueil (sur mesure, hors Theme Builder)
**Lié à** : `ADR-002`, `04-architecture/01-arborescence-site.md`, `04-architecture/03-composants-divi.md`, `01-cadrage/05-assets-design.md`  
**Référence visuelle** : `adp-app/assets/design/maquette_homepage.png` [FAIT — livrée 2026-04-24]

> **Note agent** : Ce document est basé sur le brief d'implémentation validé en réunion client (2026-04-23). Les éléments marqués [FAIT] sont fermes. Les éléments marqués [INCONNUE] nécessitent une information à recueillir avant développement. Ne pas inventer de valeurs pour les inconnues.

---

## Objectif de la page

Accueillir un visiteur qui a besoin d'aide sur Apple ou d'accompagnement pour des démarches en ligne, lui donner confiance immédiatement, lui faire percevoir le bénéfice "50% crédit d'impôt" et le convertir vers un rendez-vous ou un appel.

**Esprit global** : premium, simple, tech, humain, local. [FAIT]

---

## Structure générale

| # | Bloc | Type Divi |
|---|------|-----------|
| 1 | Header / navigation | Theme Builder — header global |
| 2 | Hero principal | Section 2 colonnes |
| 3 | Services rapides (4 cartes) | Section 4 colonnes |
| 4 | Bandeau "Services à la personne / 50% crédit d'impôt" | Section fond coloré |
| 5 | Prestations principales (6 cartes) | Section 2 × 3 colonnes |
| 6 | Thématiques de formation (pills) | Section multi-colonnes |
| 7 | Bandeau informations pratiques (4 blocs) | Section 4 colonnes fond clair |
| 8 | CTA de contact | Section sombre 2 colonnes |
| 9 | Footer | Theme Builder — footer global |

**Largeur conteneur** : 1200 à 1280 px max. [FAIT]
**Coins arrondis** : 16 à 24 px (régulier). [FAIT]
**Ombres** : légères, uniquement sur cartes et CTA. [FAIT]

---

## Bloc 1 — Header / Navigation

**Type Divi** : Theme Builder — header global sticky discret. [FAIT]
**Fond** : sombre (bleu nuit / noir). [FAIT]

### Composition

| Zone | Contenu | Notes |
|------|---------|-------|
| Gauche | Logo rond / monogramme blanc + "Astuces De Pomme" + sous-titre "Services à la personne" | [FAIT] |
| Centre / droite | Menu principal | Voir items ci-dessous |
| Extrême droite | Bouton CTA "Prendre rendez-vous" (bleu) | [FAIT] |

**Menu principal** : Accueil · Prestations · Formations · À propos · Avis · Contact [FAIT — blog retiré sur décision client 2026-04-24]

**Inconnues** :
- [RÉSOLU — I-09] Logo disponible : `adp-app/assets/design/logo-dark.png` (fond clair) + `logo-white.png` (fond sombre)
- [INCONNUE] Comportement du menu sur mobile (hamburger ?)

---

## Bloc 2 — Hero principal

**Type Divi** : Section standard, ligne 2 colonnes 45/55. [FAIT]
**Fond** : blanc ou très légèrement teinté. [FAIT]

### Colonne gauche (45%)

| Élément | Contenu | Statut |
|---------|---------|--------|
| H1 (3 lignes) | "Assistance & Formation Écosystème Apple" | [FAIT] |
| Accent couleur | Le "&" ou un accent en bleu/cyan | [FAIT] |
| Paragraphe intro | Assistance, formation, accompagnement Mac / iPhone / iPad / iCloud / réseau domestique / démarches administratives | [FAIT — thématiques confirmées] |
| CTA principal | Bouton bleu "Prendre rendez-vous" | [FAIT] |
| CTA secondaire | Bouton contour clair "06 51 31 15 37" | [FAIT] |
| Ligne réassurance | Étoiles + "Basé sur les avis de mes clients" | [FAIT] |

**Décision V1 — avis** :
- la homepage peut afficher un indicateur léger de preuve sociale issu des avis GBP
- privilégier une intégration éditorialisée ou statique légère, pas un widget externe lourd en V1
- la page `/avis/` reste la page de référence pour présenter une sélection d'avis avec lien vers la source externe

### Colonne droite (55%)

| Élément | Contenu | Statut |
|---------|---------|--------|
| Visuel hero | Bureau clair, laptop + tablette + smartphone, écrans fond noir/bleu/cyan lumineux, univers premium Apple-like | [FAIT — description] |
| Visuel | Image rassurante, propre, lumineuse | [INCONNUE — à fournir ou générer] |

### Mobile

- Colonne gauche (texte) d'abord, colonne droite (image) ensuite. [FAIT]
- Boutons pleine largeur ou quasi pleine largeur. [FAIT]

---

## Bloc 3 — Services rapides (4 cartes)

**Type Divi** : Section, ligne 4 colonnes. [FAIT]
**Fond** : blanc. [FAIT]
**Style** : fond blanc, ombre légère, coins arrondis, icône dans cercle clair, hover subtil. [FAIT]

### Cartes

| # | Titre | Icône style | Lien |
|---|-------|------------|------|
| 1 | Assistance Apple | Blurb — icône bleu clair | /prestations/#assistance |
| 2 | Formation | Blurb — icône bleu clair | /formations/ |
| 3 | Réseau & Wi-Fi | Blurb — icône bleu clair | /prestations/#reseau |
| 4 | Démarches administratives | Blurb — icône bleu clair | /prestations/#demarches |

**Contenu par carte** : icône ronde + titre + descriptif 2-4 lignes + lien "En savoir plus". [FAIT]

**Modules Divi** : Blurb (ou Image + Texte + Bouton texte). [FAIT]

### Textes proposés

| Carte | Texte proposé |
|------|---------------|
| Assistance Apple | Diagnostic, aide à l'usage et résolution de problèmes sur Mac, iPhone, iPad et iCloud. |
| Formation | Des explications claires et progressives pour mieux utiliser vos appareils Apple au quotidien. |
| Réseau & Wi-Fi | Configuration, optimisation et sécurisation de votre connexion et de vos équipements connectés à la maison. |
| Démarches administratives | Aide pas à pas pour vos démarches en ligne : impôts, santé, retraite, documents et services utiles. |

> [FAIT — validation chef de projet / carte blanche client] Les textes des cartes peuvent être proposés par le projet puis ajustés par Julien HACHE si nécessaire.

---

## Bloc 4 — Bandeau "Services à la personne / 50% crédit d'impôt"

**Type Divi** : Section fond bleu très clair, ligne 3 colonnes. [FAIT]
**Rôle** : Bloc de réassurance majeur — doit casser le rythme visuel. [FAIT]

### Composition

| Colonne | Contenu | Statut |
|---------|---------|--------|
| Gauche | Badge visuel "Services à la personne" | [FAIT] |
| Centre | Titre "Services à la personne" + **50% de crédit d'impôt** (gros) + "sur toutes nos prestations" + mention légale | [FAIT] |
| Droite | 3 puces réassurance : "Service déclaré" / "Intervention à domicile" / "Paiement par chèque ou virement" | [FAIT] |

**Mention légale** : [RÉSOLU — I-14] "Dans les limites prévues à l'article 199 sexdecies du code général des impôts" — source : CGV legacy.

### Mobile
Empilement propre des 3 colonnes. [FAIT]

---

## Bloc 5 — Prestations principales (6 cartes)

**Type Divi** : Titre centré + 2 lignes de 3 colonnes. [FAIT]
**Titre de section** : "Prestations principales" (centré). [FAIT]
**Sauvegarder en Divi Library** pour réutilisation. [FAIT]

### Cartes

| # | Titre | Lien |
|---|-------|------|
| 1 | Dépannage | /prestations/#depannage |
| 2 | Formation | /formations/ |
| 3 | Sauvegardes & installation | /prestations/#sauvegardes |
| 4 | Réseau domestique | /prestations/#reseau |
| 5 | Conseil | /prestations/#conseil |
| 6 | Démarches administratives | /prestations/#demarches |

**Contenu par carte** : icône + titre + description courte + lien "En savoir plus". [FAIT]

### Textes proposés

| Carte | Texte proposé |
|------|---------------|
| Dépannage | Résolution de pannes, blocages, lenteurs et problèmes d'usage sur vos équipements Apple. |
| Formation | Accompagnement personnalisé pour gagner en autonomie sur Mac, iPhone, iPad, iCloud et les usages numériques. |
| Sauvegardes & installation | Mise en place de sauvegardes fiables, transferts, installation et remise en route de vos appareils. |
| Réseau domestique | Amélioration du Wi-Fi, configuration du réseau local et connexion de vos périphériques à domicile. |
| Conseil | Recommandations simples et adaptées pour achat, configuration, évolution ou remplacement de matériel. |
| Démarches administratives | Aide concrète pour vos formalités en ligne, avec explications claires et accompagnement à votre rythme. |

> [FAIT — validation chef de projet / carte blanche client] Les textes de prestations peuvent être proposés par le projet puis retouchés par Julien HACHE si nécessaire.

---

## Bloc 6 — Thématiques de formation (pills)

**Type Divi** : Titre centré + ligne multi-colonnes ou modules stylés. [FAIT]
**Titre de section** : "Thématiques de formation" (centré). [FAIT]

### Pills à afficher

| # | Libellé |
|---|---------|
| 1 | Communication |
| 2 | iCloud |
| 3 | Multimédia |
| 4 | Sécurité |
| 5 | Système & Réseau |

**Style pills** : forme capsule, contour léger, icône simple à gauche, fond blanc ou légèrement bleuté. [FAIT]

**Implémentation Divi** : Blurb stylés + CSS personnalisé ou modules Code si nécessaire. [FAIT]

---

## Bloc 7 — Bandeau informations pratiques (4 blocs)

**Type Divi** : Section fond très clair, ligne 4 colonnes. [FAIT]
**Style** : pictogramme rond bleu, textes courts, séparateurs verticaux possibles sur desktop. [FAIT]

### Blocs

| # | Titre | Contenu | Statut |
|---|-------|---------|--------|
| 1 | 40€ / heure | "après déduction fiscale" + "soit 80€ avant avantage fiscal" | [FAIT] |
| 2 | Intervention à domicile | "sur rendez-vous" + "zone locale" | [FAIT] |
| 3 | Secteur d'intervention | "Région Lilloise, 60km autour d'Houplines" | [RÉSOLU — I-11 — source : homepage legacy ID 18] |
| 4 | Système & Réseau | "configuration, optimisation, sécurisation des équipements connectés" | [FAIT] |

### Responsive
- Tablette : 2 × 2
- Mobile : pile verticale

---

## Bloc 8 — Grand CTA de contact

**Type Divi** : Section sombre (bleu nuit / noir), coins arrondis, 2 colonnes. [FAIT]

### Composition

| Zone | Contenu | Statut |
|------|---------|--------|
| Gauche | Logo + titre "Besoin d'aide ? Parlons-en !" + sous-texte "Un conseil, une question ou un rendez-vous ? Je suis à votre écoute." | [FAIT] |
| Droite | Bouton téléphone bleu "06 51 31 15 37" (prioritaire) + bouton email contour sombre | [FAIT] |

**Email** : [RÉSOLU — I-10] julien.hache@astucesdepomme.com — source : llms.txt legacy.

---

## Bloc 9 — Footer

**Type Divi** : Theme Builder — footer global, 4 colonnes + barre copyright. [FAIT]

| Colonne | Contenu |
|---------|---------|
| 1 | Astuces De Pomme + Services à la personne + court texte présentation + icônes réseaux / contact |
| 2 | Navigation : Accueil · Prestations · Formations · À propos · Avis · Contact |
| 3 | Informations : Services à la personne · Tarifs & prestations · FAQ · Mentions légales · Politique de confidentialité |
| 4 | Contact : téléphone · email · localisation |
| Bas | Ligne de copyright |

**Réseaux sociaux** :
- Facebook : `https://www.facebook.com/astucesdepomme/`
- LinkedIn : `https://www.linkedin.com/company/astuces-de-pomme/about/`

**Email** : [RÉSOLU — I-10] `julien.hache@astucesdepomme.com`

---

## Charte visuelle (résumé)

Voir `ADR-002-identite-visuelle.md` pour la charte complète.

| Rôle | Couleur | Usage | Statut |
|------|---------|-------|--------|
| Bleu marine (primaire) | `#1e3264` | Header, pictos, bouton principal, bandeau CTA | [FAIT — extrait logo-dark.png 2026-04-24] |
| Bleu vif (accent) | `#0070c8` | Liens, icônes actives, hover boutons | [FAIT — extrait maquette 2026-04-24] |
| Noir / bleu nuit | `#1e3264` foncé ou var. | Header fond, bandeau CTA final | [HYPOTHÈSE — à confirmer en intégration] |
| Blanc | `#ffffff` | Fonds principaux, cartes | [FAIT] |
| Bleu très clair / gris bleuté | À préciser | Fonds secondaires, bandeaux réassurance | [HYPOTHÈSE — visible dans maquette] |
| Gris foncé | À préciser | Texte courant | [HYPOTHÈSE] |
| Gris clair | À préciser | Bordures discrètes | [HYPOTHÈSE] |

**Police** : sans-serif moderne, sobre, très lisible. Carte blanche projet/client pour le choix final.  
**Préconisation projet** : `Inter` en priorité, `DM Sans` en alternative. [FAIT — choix libre validé]

**Inconnues couleurs** : [INCONNUE] Valeurs hex exactes — à extraire de la carte de visite du client ou à définir avec lui.

---

## CSS personnalisé à prévoir

L'agent ou le développeur peut ajouter du CSS pour : [FAIT — consigne brief]

- Uniformiser les coins arrondis
- Améliorer les hover states
- Harmoniser les hauteurs de cartes
- Gérer les pills de thématiques
- Styliser finement les boutons secondaires
- Améliorer le responsive

---

## Inconnues bloquantes récapitulatives

| ID | Inconnue | Bloque | Statut |
|----|----------|--------|--------|
| I-logo | Logo / monogramme (format PNG fond transparent) | Header, hero, CTA final | [RÉSOLU — I-09 — logo-dark.png + logo-white.png dans `adp-app/assets/design/`] |
| I-email | Adresse email de contact | Bloc 8, footer | [RÉSOLU — I-10 — julien.hache@astucesdepomme.com] |
| I-zone | Zone / communes d'intervention | Bloc 7 | [RÉSOLU — I-11 — "Région Lilloise, 60km autour d'Houplines"] |
| I-hex | Valeurs hex exactes de la palette | Tous les blocs | [RÉSOLU PARTIEL — I-07 — `#1e3264` (primaire) + `#0070c8` (accent) — voir `01-cadrage/05-assets-design.md`] |
| I-police | Police validée | Tous les blocs | [RÉSOLU — I-13 — carte blanche client ; préconisation projet : `Inter`] |
| I-textes | Textes descriptifs des cartes et prestations | Blocs 3, 5 | [RÉSOLU — I-12 — proposition projet autorisée, révisable par Julien HACHE] |
| I-mention-legale | Mention légale crédit d'impôt | Bloc 4 | [RÉSOLU — I-14 — "Dans les limites prévues à l'article 199 sexdecies du code général des impôts"] |
| I-visuels | Image hero + badge "Services à la personne" | Blocs 2, 4 | [RÉSOLU PARTIEL — hero-bg.png disponible dans `adp-app/assets/design/` ; badge SAP à créer] |
| I-reseaux | Réseaux sociaux présents et URLs | Footer | [RÉSOLU — Facebook + LinkedIn fournis le 2026-04-24] |

---

## Responsivité

| Contexte | Comportement |
|----------|-------------|
| Desktop | Aéré, 4 colonnes, CTA visibles, grilles pleines |
| Tablette | Hero compact, cartes 2 colonnes, bandeaux plus verticaux |
| Mobile | Empilement propre, texte hero d'abord, image ensuite, boutons pleine largeur |

---

## Modules Divi à utiliser

`Text` · `Button` · `Image` · `Blurb` · `Call To Action` · `Divider` · `Icon`
CSS uniquement pour pills et finitions responsive. [FAIT]
Pas de module `Code` sauf si indispensable. [FAIT]

---

## Signalement

- **Statut** : Brief client validé (réunion 2026-04-23) — spec rédigée en conséquence
- **Hypothèses posées** : Liens internes (slugs des pages Prestations/Formations/Avis non encore créées), préconisation de police (`Inter`) dans le cadre de la carte blanche client
- **Inconnues résolues** : logo (I-09), email (I-10), zone géo (I-11), palette primaire/accent (I-07 partiel), hero image (I-visuels partiel), mention légale (I-14)
- **Inconnues restantes** : badge SAP, couleurs complémentaires (hover, fond section)
- **Points à arbitrer** : uniquement les couleurs complémentaires et la forme finale du badge SAP
- **Prochaine étape** : intégrer la homepage sur base des textes proposés et des réseaux fournis, puis laisser Julien HACHE ajuster si besoin
