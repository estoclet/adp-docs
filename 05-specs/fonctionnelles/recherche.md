# Recherche — Brief fonctionnel

**Statut** : Brouillon — [À VALIDER]  
**Dernière mise à jour** : 2026-04-24  
**Produit par** : Chef de projet — hypothèse initiale  
**Fonctionnalité** : Recherche de contenu  
**Priorité** : Haute [HYPOTHÈSE — site avec contenu volumineux]  
**Lié à** : `04-architecture/01-arborescence-site.md`, `01-cadrage/02-architecture-cible.md`

---

## Contexte et besoin

**Problème utilisateur** : Un visiteur qui cherche une astuce sur un sujet précis (ex: "comment faire une capture d'écran sur Mac") doit pouvoir trouver rapidement sans naviguer dans toutes les catégories.

**Besoin exprimé** : [HYPOTHÈSE — non exprimé explicitement, déduit du type de site]

**Périmètre** : Recherche dans les articles et pages du site. Accessible depuis le header (toutes les pages).

---

## Comportement attendu

### Cas principal
1. L'utilisateur clique sur l'icône de recherche dans le header
2. Un champ de saisie s'affiche (dans le header ou en overlay)
3. L'utilisateur saisit sa recherche
4. Les résultats s'affichent sur une page de résultats dédiée
5. Les résultats montrent : titre, extrait, catégorie, date de l'article

### Cas secondaires
- Si aucun résultat : message explicite + suggestions de catégories
- Si la recherche est vide et soumise : ne rien faire ou retourner les résultats récents
- Sur mobile : champ de recherche pleine largeur ou overlay

---

## Critères d'acceptation

- [ ] Le champ de recherche est accessible depuis toutes les pages (header)
- [ ] La recherche renvoie des résultats pertinents dans les articles ET les pages
- [ ] Les résultats affichent titre, extrait et lien vers l'article
- [ ] Le temps de réponse est < 2 secondes
- [ ] La page de résultats est indexable par Google (ou noindex si souhaité)
- [ ] Un message explicite s'affiche en cas de résultat vide
- [ ] Le champ est accessible (attribut aria-label, focus visible)

---

## Contraintes techniques

| Contrainte | Détail | Source |
|-----------|--------|--------|
| Moteur de recherche | Recherche native WP (suffisante pour le volume attendu) | [HYPOTHÈSE] |
| Plugin optionnel | SearchWP ou FacetWP si la recherche native est insuffisante | [RECOMMANDÉ si > 500 articles] |
| Divi | Le champ de recherche peut être un module Divi Search | [FAIT — module natif Divi] |
| Performance | Éviter de charger un moteur JS lourd inutilement | [RECOMMANDÉ] |

> [À ARBITRER] : La recherche native WP est suffisante si le volume d'articles est raisonnable. Si le legacy révèle + de 300 articles, évaluer SearchWP ou similaire.

---

## Maquette / wireframe

[INCONNUE — aucune maquette disponible]

Disposition textuelle proposée [HYPOTHÈSE] :
- Header desktop : icône loupe à droite du menu principal → clic → champ s'expand
- Header mobile : icône loupe visible → clic → overlay pleine largeur
- Page résultats : titre H1 "Résultats pour "[terme]"" + liste d'articles (titre, extrait, catégorie, lien)

---

## Dépendances

| Dépendance | Type | Impact |
|-----------|------|--------|
| Volume réel d'articles (inventaire legacy) | Décision technique | Choix moteur recherche |
| Composant Header Divi (global) | Composant | Intégration du champ |
| Plugin SearchWP (si retenu) | Plugin tiers | Budget, configuration |

---

## Hors périmètre de ce brief

- Recherche vocale
- Filtres avancés par catégorie / date sur la page de résultats [HYPOTHÈSE — à évaluer en v2]
- Autocomplétion / suggestions en temps réel [HYPOTHÈSE — à évaluer en v2]

---

## Signalement agent

- **Tâche accomplie** : Brief fonctionnel recherche rédigé sur la base du contexte projet
- **Hypothèses posées** : Moteur natif WP suffisant, volume d'articles modéré, intégration header
- **Inconnues rencontrées** : Volume réel d'articles (déterminant pour le choix du moteur)
- **Points à arbitrer** : Moteur de recherche natif vs plugin, présence de filtres avancés
- **Prochaine étape recommandée** : Valider après connaissance du volume legacy (TP-001)
