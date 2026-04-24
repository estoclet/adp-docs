# Composants Divi réutilisables

**Statut** : Mis à jour — brief homepage validé (2026-04-23)
**Dernière mise à jour** : 2026-04-24
**Lié à** : `ADR-002-identite-visuelle.md`, `05-specs/pages/homepage.md`

---

## Principe de composantisation Divi

Divi permet de sauvegarder des sections, lignes ou modules comme "Saved Layouts" réutilisables globalement (Divi Library).

**Règle** : Un composant est sauvegardé en Divi Library s'il apparaît sur au moins 3 pages. En deçà, layout local.

---

## Composants globaux (Theme Builder)

Ces éléments sont construits dans le Theme Builder et s'appliquent à toutes les pages. [FAIT — consigne brief]

| Composant | Notes |
|-----------|-------|
| Header global | Fond sombre — logo + menu + bouton CTA — sticky discret |
| Footer global | 4 colonnes — clair — copyright |

### Header — détail de structure

| Zone | Contenu |
|------|---------|
| Gauche | Logo rond / monogramme blanc + "Astuces De Pomme" + "Services à la personne" |
| Centre / droite | Menu : Accueil · Prestations · Formations · À propos · Avis · Blog · Contact |
| Extrême droite | Bouton bleu "Prendre rendez-vous" |

**Modules Divi** : Logo, Menu, Button — dans une ligne 3 zones. [FAIT]

---

## Composants Divi Library (réutilisables entre pages)

Ces sections sont sauvegardées en Divi Library pour être réutilisées. [FAIT — consigne brief]

| Composant | Utilisé sur | Module Divi | Priorité |
|-----------|------------|-------------|----------|
| Carte service / prestation | Homepage blocs 3 + 5, /prestations/ | Blurb | Haute |
| Bandeau "50% crédit d'impôt" | Homepage bloc 4, /prestations/ [HYPOTHÈSE] | Section custom | Haute |
| Pill / badge thématique | Homepage bloc 6, /formations/ | Blurb stylé + CSS | Moyenne |
| Grand CTA de contact (sombre) | Homepage bloc 8, bas de /prestations/ [HYPOTHÈSE] | Call To Action ou Section custom | Haute |
| Bandeau infos pratiques | Homepage bloc 7, /contact/ [HYPOTHÈSE] | Section 4 colonnes | Moyenne |

---

## Modules Divi à utiliser (liste validée)

Ces modules sont les seuls à utiliser sauf besoin spécifique justifié. [FAIT — consigne brief]

| Module | Usage principal |
|--------|----------------|
| Text | Titres, paragraphes, H1/H2/H3 |
| Button | CTA principaux et secondaires |
| Image | Visuel hero, photos, illustrations |
| Blurb | Cartes services + icône + titre + texte |
| Call To Action | Section CTA contact (bloc 8) |
| Divider | Séparateurs visuels |
| Icon | Pictos isolés |
| Blog | Archive articles pour bloc homepage ou page /blog/ |

**Module Code** : uniquement si nécessaire pour les pills / effets non faisables autrement. [FAIT]

---

## CSS personnalisé à prévoir

Le CSS custom est **nécessaire** pour les éléments suivants. [FAIT — consigne brief]

| Cible CSS | Objectif |
|-----------|---------|
| `.card-service` | Uniformiser les coins arrondis (16-24px), hauteur égale |
| `.card-service:hover` | Hover subtil (ombre légère ou légère remontée) |
| `.pill-thematique` | Forme capsule, contour léger, icône gauche |
| `.btn-secondary` | Bouton contour clair + style de survol |
| Media queries mobile | Empilement propre, boutons pleine largeur |
| Header sticky | Transition discrète au scroll |

---

## Charte Divi — Presets à créer

Les presets Divi permettent d'appliquer un style uniforme sans CSS inline. [RECOMMANDÉ]

| Preset | Appliqué à | Description |
|--------|-----------|-------------|
| Bouton principal | Module Button | Bleu principal, coins arrondis, texte blanc |
| Bouton secondaire | Module Button | Contour bleu clair, texte bleu, fond transparent |
| Titre H2 section | Module Text | Couleur principale, centré ou gauche, taille définie |
| Carte | Module Blurb | Fond blanc, ombre légère, coins 16-24px, padding généreux |

> [DÉPENDANCE] : Les valeurs hex pour les presets sont bloquées sur I-hex (voir ADR-002 et homepage spec).

---

## Templates de pages Divi

| Template | Pages | Statut |
|----------|-------|--------|
| Template Accueil | `/` | En cours de spécification |
| Template Page statique | `/a-propos/`, `/contact/`, `/avis/` | À créer — Lot 3 |
| Template Article Blog | `/blog/{slug}/` | À créer — Lot 3 |
| Template Page Prestations | `/prestations/` | À créer — après spec |
| Template Page Formations | `/formations/` | À créer — après spec |
| Template 404 | Toute URL inexistante | À créer — Lot 3 |

---

## Ce que ce document ne contient pas

- Les specs de pages individuelles (voir `05-specs/pages/`)
- La palette hex complète (voir `ADR-002-identite-visuelle.md`)
- Les plugins WP (voir `01-cadrage/02-architecture-cible.md`)
