# ADR-001 — Stack technique : WordPress + Divi

**Statut** : Accepté  
**Date** : 2026-04-24  
**Décideurs** : Julien HACHE (client), Eric STOCLET (chef de projet)  
**Lié à** : `01-cadrage/02-architecture-cible.md`, `01-cadrage/01-perimetre-projet.md`

---

## Contexte

Le projet est la refonte du site astucesdepomme.com. Le client Julien HACHE gère seul (ou quasi-seul) son site et a besoin d'un CMS accessible, qu'il peut maintenir sans développeur pour les opérations courantes (publication d'articles, modification de pages).

Le site existant fonctionne sous WordPress. Le client maîtrise cet environnement [HYPOTHÈSE — à confirmer].

La refonte doit apporter une meilleure structure, une meilleure lisibilité et une meilleure image sans changer radicalement d'environnement de travail pour le client.

---

## Décision

Le nouveau site sera développé avec **WordPress** (CMS) et **Divi** (page builder d'Elegant Themes) comme stack technique principale.

---

## Raisons

- [FAIT] Le client a explicitement demandé de conserver WordPress + Divi.
- WordPress est le CMS le plus répandu pour ce type de site de contenu éditorial.
- Divi offre une interface visuelle adaptée à un gestionnaire non développeur.
- Le legacy est déjà sous WordPress — la migration de contenu sera facilitée (export XML natif WP).
- L'écosystème de plugins WordPress est mature pour les besoins identifiés (SEO, cache, formulaires, sécurité).

---

## Alternatives écartées

| Alternative | Raison d'abandon |
|------------|-----------------|
| WordPress + Elementor | Client a exprimé sa préférence pour Divi |
| WordPress + Gutenberg seul | Moins adapté à la mise en page visuelle souhaitée |
| Webflow | Rupture avec l'environnement existant, courbe d'apprentissage client |
| Ghost | Non adapté à la richesse structurelle requise (taxonomies, CPT) |
| Statique (Hugo, Astro…) | Incompatible avec les besoins de gestion autonome du contenu par le client |

---

## Conséquences

### Positives
- Continuité pour le client — pas de formation à un nouveau CMS
- Migration de contenu facilitée via l'export WP natif
- Large choix de plugins pour les fonctionnalités requises
- Divi permet de construire visuellement sans code

### Négatives / risques
- **Performance** : Divi génère un JS/CSS volumineux — mitigé par WP Rocket + optimisation Divi
- **Maintenance** : WordPress nécessite des mises à jour régulières — à intégrer dans le plan de maintenance
- **Verrouillage** : Divi crée un couplage fort entre le contenu et le builder — risque à long terme si changement de builder
- **Coût licence Divi** : Licence annuelle Elegant Themes — à vérifier si déjà disponible chez le client [À ARBITRER]

---

## Révision

Cette décision sera révisée si :
- Le client change explicitement de préférence
- Une contrainte technique rend WordPress + Divi incompatible avec les exigences de performance après optimisation
- Le coût de la licence Divi est bloquant [À ARBITRER]

---

## Historique

| Date | Auteur | Changement |
|------|--------|-----------|
| 2026-04-24 | Eric STOCLET | Création — formalisation de la décision client |
