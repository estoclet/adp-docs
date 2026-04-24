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
| Bleu principal | Boutons, accents, pictos actifs | `#1e3264` | [FAIT — extrait du logo] |
| Bleu accent | Détails, surlignages, icônes secondaires | `#0070c8` | [FAIT — extrait de la maquette] |
| Blanc | Fonds principaux, cartes | `#ffffff` | [FAIT] |
| Bleu nuit / tons sombres | Header, bandeau CTA final | voir maquette et assets de référence | [FAIT — référence visuelle] |
| Tons clairs complémentaires | Fonds secondaires, bandeaux d'info | voir maquette et assets de référence | [FAIT — référence visuelle] |
| Neutres texte / bordures | Texte courant, séparateurs | voir maquette et assets de référence | [FAIT — référence visuelle] |

> [FAIT] Pour la V1, les tokens fermes sont `#1e3264`, `#0070c8` et `#ffffff`. Les autres nuances suivent la maquette validée et les assets documentés dans `01-cadrage/05-assets-design.md`.

### Typographie

- **Style** : sans-serif moderne, sobre, très lisible
- **Police retenue en V1** : `Inter`
- **Alternative crédible** : `DM Sans`
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
- la maquette reste la référence pour certaines nuances secondaires non promues en tokens autonomes
- si une police Google Fonts est choisie, elle impacte légèrement la performance (préférer preload)

---

## Actions requises avant développement

| Action | Qui | Bloque |
|--------|-----|--------|
| Utiliser les tokens `#1e3264`, `#0070c8`, `#ffffff` et la maquette comme référence complémentaire | Équipe projet | Non |
| Utiliser `Inter` comme police V1 | Équipe projet | Non |
| Utiliser les assets versionnés dans `adp-app/assets/design/` | Équipe projet | Non |

---

## Révision

Cette décision sera révisée si le client change d'identité visuelle ou décide d'une refonte graphique complète.

---

## Historique

| Date | Auteur | Changement |
|------|--------|-----------|
| 2026-04-23 | Eric STOCLET | Création — décisions validées en réunion client |
| 2026-04-24 | Eric STOCLET | Formalisation dans ADR-002 |
| 2026-04-24 | Eric STOCLET | Palette et typographie V1 précisées depuis les assets et validations projet |
