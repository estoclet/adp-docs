# Page d'accueil — Spec

**Statut** : Validé — Eric STOCLET 2026-04-27
**Dernière mise à jour** : 2026-04-27 — Validation Eric STOCLET ; TP-005 lancé
**Produit par** : Eric STOCLET, d'après brief client
**URL cible** : `/`
**Template Divi** : Template Accueil (sur mesure, hors Theme Builder)
**Lié à** : `ADR-002`, `04-architecture/01-arborescence-site.md`, `04-architecture/03-composants-divi.md`, `01-cadrage/05-assets-design.md`  
**Référence visuelle** : `adp-app/assets/design/maquette_homepage.png` [FAIT — livrée 2026-04-24]

> **Note agent** : Ce document est basé sur le brief d'implémentation validé en réunion client (2026-04-23). Les éléments marqués [FAIT] sont fermes. Les éléments marqués [INCONNUE] nécessitent une information à recueillir avant développement. Ne pas inventer de valeurs pour les inconnues.
>
> **[ALERTE D-018 — 2026-04-25]** La décision client "site one page" (ADR-003) impose de réviser cette spec. La homepage doit absorber des **sections résumées** pour Prestations, Formations et À propos, chacune avec un lien "Voir plus" → popup Divi. La structure des 9 blocs initiaux est conservée comme base, mais des sections supplémentaires s'y ajoutent. **Cette spec ne doit pas être utilisée telle quelle pour TP-005** — relire ADR-003 d'abord (R-29).

---

## Objectif de la page

Accueillir un visiteur qui a besoin d'aide sur Apple ou d'accompagnement pour des démarches en ligne, lui donner confiance immédiatement, lui faire percevoir le bénéfice "50% crédit d'impôt" et le convertir vers un rendez-vous ou un appel.

**Esprit global** : premium, simple, tech, humain, local. [FAIT]

---

## Structure générale

> **[D-018 — 2026-04-25]** Architecture one page : les items de navigation (Prestations, Formations, À propos) scrollent vers leurs sections respectives via des ancres CSS ID. Chaque section a un lien "Voir plus" → popup Divi pour le contenu détaillé. L'implémentation technique des popups est définie en TP-006 (D-019).

| # | Bloc | Type Divi | Ancre nav |
|---|------|-----------|-----------|
| 1 | Header / navigation | Theme Builder — header global | — |
| 2 | Hero principal | Section 2 colonnes | — |
| 3 | Services rapides (4 cartes) | Section 4 colonnes | `#prestations` |
| 4 | Bandeau "Services à la personne / 50% crédit d'impôt" | Section fond coloré | — |
| 5 | Prestations principales (6 cartes + CTA popup) | Section 2 × 3 colonnes | (suite section Prestations) |
| 6 | Thématiques de formation (pills + CTA popup) | Section multi-colonnes | `#formations` |
| **7** | **À propos — intro Julien HACHE (photo + texte + CTA popup)** | **Section 2 colonnes** | **`#a-propos`** |
| 8 | Bandeau informations pratiques (4 blocs) | Section 4 colonnes fond clair | — |
| 9 | CTA de contact | Section sombre 2 colonnes | — |
| 10 | Footer | Theme Builder — footer global | — |

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

> **[D-018]** Navigation anchor-based : les items "Prestations", "Formations" et "À propos" scrollent vers les sections de la homepage (CSS ID : `#prestations`, `#formations`, `#a-propos`). "Avis" et "Contact" ouvrent leur popup. "Accueil" remonte en haut de page.

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
| Visuel | Image rassurante, propre, lumineuse | [FAIT — `hero-bg.png` dans `adp-app/assets/design/` — versionnée 2026-04-24] |

### Mobile

- Colonne gauche (texte) d'abord, colonne droite (image) ensuite. [FAIT]
- Boutons pleine largeur ou quasi pleine largeur. [FAIT]

---

## Bloc 3 — Services rapides (4 cartes)

**Type Divi** : Section, ligne 4 colonnes. [FAIT]
**Fond** : blanc. [FAIT]
**Style** : fond blanc, ombre légère, coins arrondis, icône dans cercle clair, hover subtil. [FAIT]
**Ancre CSS** : `id="prestations"` sur cette section (navigation anchor — D-018). [RECOMMANDÉ]

### Cartes

| # | Titre | Icône style | Lien |
|---|-------|------------|------|
| 1 | Assistance Apple | Blurb — icône bleu clair | `[popup-prestations]` — voir note D-018 |
| 2 | Formation | Blurb — icône bleu clair | `[popup-formations]` — voir note D-018 |
| 3 | Réseau & Wi-Fi | Blurb — icône bleu clair | `[popup-prestations]` — voir note D-018 |
| 4 | Démarches administratives | Blurb — icône bleu clair | `[popup-prestations]` — voir note D-018 |

> **[D-018 — popup links]** Les liens "En savoir plus" des cartes déclenchent le popup correspondant (Prestations ou Formations). L'implémentation technique (ID popup Divi, déclencheur) est définie en TP-006. Notation `[popup-XXX]` = déclencheur popup à remplacer par le mécanisme Divi retenu.

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
| 1 | Dépannage | `[popup-prestations]` |
| 2 | Formation | `[popup-formations]` |
| 3 | Sauvegardes & installation | `[popup-prestations]` |
| 4 | Réseau domestique | `[popup-prestations]` |
| 5 | Conseil | `[popup-prestations]` |
| 6 | Démarches administratives | `[popup-prestations]` |

**Contenu par carte** : icône + titre + description courte + lien "En savoir plus". [FAIT]

**CTA de section (D-018)** : bouton secondaire "Voir toutes les prestations →" en bas de section, déclenche `[popup-prestations]`. [RECOMMANDÉ]

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
**Ancre CSS** : `id="formations"` sur cette section (navigation anchor — D-018). [RECOMMANDÉ]

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

**CTA de section (D-018)** : bouton secondaire "Voir le détail des formations →" en bas de section, déclenche `[popup-formations]`. [RECOMMANDÉ]

---

## Bloc 7 — À propos — intro Julien HACHE *(nouveau — D-018)*

**Type Divi** : Section fond blanc ou très légèrement teinté, ligne 2 colonnes 40/60. [RECOMMANDÉ]
**Titre de section** : "À propos de Julien Hache" (centré ou aligné gauche). [RECOMMANDÉ]
**Ancre CSS** : `id="a-propos"` sur cette section (navigation anchor — D-018). [RECOMMANDÉ]

### Composition

| Zone | Contenu | Statut |
|------|---------|--------|
| Colonne gauche (40%) | Photo de Julien HACHE — `adp-app/assets/design/julien-hache-portrait.png` | [FAIT — D-020, 2026-04-25 — 810×552 px, recadrage recommandé] |
| H2 (colonne droite) | "Technicien Apple indépendant à votre domicile" | [RECOMMANDÉ] |
| Texte intro (colonne droite) | 2-3 phrases de présentation — parcours, agrément SAP, zone d'intervention | [RECOMMANDÉ — placeholder I-16 acceptable (D-016)] |
| CTA "En savoir plus" | Bouton secondaire → déclenche `[popup-a-propos]` | [RECOMMANDÉ] |

### Texte intro proposé (placeholder I-16)

> "Julien Hache accompagne particuliers et professionnels de la région lilloise pour simplifier leur quotidien numérique. Certifié services à la personne (agrément SAP N° 502282080), il intervient à domicile pour l'assistance Apple, la formation et les démarches administratives. 50% de crédit d'impôt sur toutes les prestations."

*[RECOMMANDÉ — placeholder D-016 en attente du texte fourni par Julien HACHE]*

### Mobile

Image en pleine largeur → texte → bouton. [RECOMMANDÉ]

---

## Bloc 8 — Bandeau informations pratiques (4 blocs)

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

## Bloc 9 — Grand CTA de contact

**Type Divi** : Section sombre (bleu nuit / noir), coins arrondis, 2 colonnes. [FAIT]

### Composition

| Zone | Contenu | Statut |
|------|---------|--------|
| Gauche | Logo + titre "Besoin d'aide ? Parlons-en !" + sous-texte "Un conseil, une question ou un rendez-vous ? Je suis à votre écoute." | [FAIT] |
| Droite | Bouton téléphone bleu "06 51 31 15 37" (prioritaire) + bouton email contour sombre | [FAIT] |

**Email** : [RÉSOLU — I-10] julien.hache@astucesdepomme.com — source : llms.txt legacy.

---

## Bloc 10 — Footer

**Type Divi** : Theme Builder — footer global, 4 colonnes + barre copyright. [FAIT]

| Colonne | Contenu |
|---------|---------|
| 1 | Astuces De Pomme + Services à la personne + court texte présentation + icônes réseaux / contact |
| 2 | Navigation : Accueil · Prestations · Formations · À propos · Avis · Contact |
| 3 | Liens légaux : CGV · Informations fiscales · Politique de confidentialité · Tarifs & prestations · Mentions légales [FAIT — menu footer WordPress configuré, vérifié ddev 2026-04-25] |
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

**Inconnues couleurs** : [RÉSOLU PARTIEL — I-07] Tokens V1 fermes : `#1e3264` (primaire) + `#0070c8` (accent) + `#ffffff` (blanc). Tons complémentaires proposés dans `adp-divi-child/theme.css` : texte `#23344d`, fond section `#f4f8fc`, bordure `#d7e1ec` — [HYPOTHÈSE à valider lors de la recette Divi par Julien HACHE]. Référence visuelle : `adp-app/assets/design/maquette_homepage.png`. Source détaillée : `01-cadrage/05-assets-design.md`.

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
| I-visuels | Image hero + badge "Services à la personne" | Blocs 2, 4 | [FAIT — hero-bg.png + logo-sap.png disponibles dans `adp-app/assets/design/`] |
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

`Text` · `Button` · `Image` · `Blurb` · `Call To Action` · `Divider` · `Icon` · **`Popup`** (D-018/D-019)
CSS uniquement pour pills et finitions responsive. [FAIT]
Pas de module `Code` sauf si indispensable. [FAIT]

> **[D-019]** Les popups Prestations, Formations et À propos utilisent le module Popup natif Divi 5 — éditabilité client à valider en TP-006. Référence technique : voir `04-architecture/03-composants-divi.md` et ADR-003.

---

## Signalement

- **Statut** : Révisé D-018 (2026-04-25) — 10 blocs (Bloc 7 À propos ajouté) ; liens popup ; anchors navigation
- **Hypothèses posées** : préconisation de police (`Inter`) ; texte intro Julien HACHE (placeholder I-16 D-016) ; position Bloc 7 entre Formations et Infos pratiques
- **Inconnues résolues** : logo (I-09), email (I-10), zone géo (I-11), palette primaire/accent (I-07 partiel), hero image, mention légale (I-14), photo Julien (I-15 — D-020)
- **Inconnues restantes** : bio Julien (I-16 — placeholder D-016), badge SAP (placeholder D-016), couleurs complémentaires (tokens `theme.css` à valider client), comportement menu mobile, implémentation popup Divi (mécanisme exact à définir en TP-006)
- **Marqueurs promus** : aucun ajout dans cette révision
- **Points à arbitrer** : forme badge SAP, comportement menu mobile, 3 méthodes popup Divi 5 (voir note D-019 ci-dessus) — à choisir en TP-006 en vérifiant éditabilité client
- **Prochaine étape** : valider cette spec révisée (Eric STOCLET), puis lancer TP-005 (intégration Divi homepage)
