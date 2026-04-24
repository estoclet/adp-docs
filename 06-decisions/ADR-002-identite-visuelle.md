# ADR-002 — Identité visuelle et charte Divi

**Statut** : Accepté
**Date** : 2026-04-23 (réunion client)
**Décideurs** : Julien HACHE (client), Eric STOCLET (chef de projet)
**Lié à** : `05-specs/pages/homepage.md`, `04-architecture/03-composants-divi.md`

---

## Contexte

La refonte doit donner une image plus professionnelle, structurée et rassurante au site astucesdepomme.com. Julien HACHE dispose d'une carte de visite existante qui sert de référence visuelle. Le stack retenu (WordPress + Divi) permet de définir une charte appliquée via les presets Divi et un peu de CSS custom.

---

## Décision

L'identité visuelle du nouveau site est basée sur la palette et le style de la carte de visite de Julien HACHE, avec les caractéristiques suivantes :

### Esprit général

**Premium, simple, tech, humain, local.**  
Ambiance "tech de confiance" — propre, respirante, sans surcharge décorative.

### Palette de couleurs

| Rôle | Description | Hex | Statut |
|------|-------------|-----|--------|
| Bleu principal | Bouton principal, accents, pictos actifs | [INCONNUE — extraire de la carte de visite] | [À PRÉCISER] |
| Bleu cyan / électrique | Détails, surlignages, icônes secondaires | [INCONNUE] | [À PRÉCISER] |
| Noir / bleu nuit | Header, bandeau CTA final | [INCONNUE] | [À PRÉCISER] |
| Blanc | Fonds principaux, cartes | #FFFFFF | [FAIT] |
| Bleu très clair / gris bleuté | Fonds secondaires, bandeaux d'info | [INCONNUE] | [À PRÉCISER] |
| Gris foncé | Texte courant | [INCONNUE — approx. #333 ou #444] | [À PRÉCISER] |
| Gris clair | Bordures discrètes | [INCONNUE — approx. #E0E0E0] | [À PRÉCISER] |

> [À PRÉCISER] : Les valeurs hex exactes doivent être extraites de la carte de visite fournie par le client ou définies avec lui lors d'un point dédié.

### Typographie

- **Style** : sans-serif moderne, sobre, très lisible
- **Candidates recommandées** : Inter, DM Sans, Nunito Sans, Poppins [RECOMMANDÉ — à valider]
- **Hiérarchie** :
  - H1 : très grand, gras
  - H2 : bien marqué
  - Corps cartes : court
  - Boutons : bien visibles
  - Interlignage : généreux

### Style général

| Attribut | Valeur |
|----------|--------|
| Coins arrondis | 16 à 24 px (régulier) |
| Ombres | Légères, uniquement sur cartes et CTA |
| Icônes | Fines, cohérentes (une bibliothèque unique) |
| Espacement | Beaucoup d'espace blanc — sections aérées |
| Largeur conteneur | 1200 à 1280 px max |

### Structure header/footer

- **Header** : sombre (bleu nuit / noir), logo blanc, menu centré, bouton CTA bleu à droite
- **Footer** : clair, 4 colonnes, copyright en bas

---

## Raisons

- La carte de visite existante constitue un capital identitaire à valoriser et non à effacer
- L'esprit bleu/cyan sur fond clair est cohérent avec l'univers Apple (tech, clair, fiable)
- Le header sombre crée un contraste fort et une identité mémorisable
- Les coins arrondis et les ombres légères donnent un sentiment de modernité sans lourdeur

---

## Alternatives écartées

| Alternative | Raison d'abandon |
|------------|-----------------|
| Refonte graphique complète (nouveau logo, nouvelle palette) | Client souhaite continuité avec la carte de visite |
| Style skeumorphe ou très coloré | Incompatible avec l'esprit "tech de confiance" |
| Palette monochrome | Moins différenciante, moins chaleureuse |

---

## Conséquences

### Positives
- Cohérence entre les supports physiques (carte) et numériques (site)
- Palette bleu/cyan : lisible, accessible, professionnelle
- Style épuré : performant (moins de ressources graphiques)

### Négatives / risques
- **Valeurs hex non définies** : les hex manquants doivent être fournis avant développement — [INCONNUE BLOQUANTE pour le Lot 3]
- **Police** : si une police Google Fonts est choisie, elle impacte légèrement la performance (préférer preload)

---

## Actions requises avant développement

| Action | Qui | Bloque |
|--------|-----|--------|
| Fournir les hex exacts de la carte de visite | Julien HACHE | Tous les styles Divi |
| Valider la police choisie | Julien HACHE + Eric STOCLET | CSS global |
| Fournir le logo / monogramme PNG fond transparent | Julien HACHE | Header, footer, CTA |

---

## Révision

Cette décision sera révisée si le client change d'identité visuelle ou décide d'une refonte graphique complète.

---

## Historique

| Date | Auteur | Changement |
|------|--------|-----------|
| 2026-04-23 | Eric STOCLET | Création — décisions validées en réunion client |
| 2026-04-24 | Eric STOCLET | Formalisation dans ADR-002 |
