# Assets de design disponibles

**Statut** : Actif  
**Dernière mise à jour** : 2026-04-25 — tons complémentaires documentés depuis theme.css, R-27 appliqué  
**Produit par** : Eric STOCLET  
**Lié à** : `00-initialisation-projet.md`, `05-specs/pages/homepage.md`, `04-architecture/04-conventions-divi.md`

---

## Fichiers disponibles

Tous les fichiers sont versionnés dans `adp-app/assets/design/`.

| Fichier | Description | Résout |
|---------|-------------|--------|
| `logo-dark.png` | Monogramme "AdP" bleu marine sur fond blanc/transparent — usage fond clair | I-09 |
| `logo-white.png` | Monogramme "AdP" blanc sur fond transparent — usage fond sombre | I-09 |
| `hero-bg.png` | Photo hero : tablette, MacBook, iPhone sur bureau bois — fond blanc à gauche | Bloc 2 homepage |
| `maquette_homepage.png` | Maquette complète de la homepage validée client (2026-04-23) | Référence visuelle |

[FAIT] Fichiers copiés dans `adp-app/assets/design/` le 2026-04-24.  
[FAIT] Ces fichiers sont la référence visuelle officielle — ils correspondent aux specs documentées dans `05-specs/pages/homepage.md` (ADR-002).

---

## Palette extraite

Palette extraite directement des fichiers sources (mesure directe — Python PIL — 2026-04-24) :

| Rôle | Hex | RGB | Source |
|------|-----|-----|--------|
| Bleu marine (primaire) | `#1e3264` | rgb(30, 50, 100) | logo-dark.png — couleur dominante (36 744 px) |
| Bleu vif (secondaire / accent) | `#0070c8` | rgb(0, 112, 200) | maquette_homepage.png — boutons, icônes (6 300 px) |
| Blanc (fond) | `#ffffff` | rgb(255, 255, 255) | maquette_homepage.png |

[FAIT] I-07 résolue opérationnellement : les deux bleus de référence et le blanc sont extraits avec certitude.  
[FAIT] Pour la V1, la maquette `maquette_homepage.png` fait autorité sur les tons complémentaires (fonds clairs, contrastes, hiérarchie visuelle) si un token hex dédié n'a pas été isolé séparément.

### Tons complémentaires — versionnés dans theme.css

Source : `adp-app/web/wp-content/themes/adp-divi-child/assets/css/theme.css` — commit `7a389ee`. [FAIT — mesure directe, 2026-04-25]

| Rôle | Token CSS | Hex | Notes |
|------|-----------|-----|-------|
| Texte courant | `--adp-color-text` | `#23344d` | Bleu-gris foncé — dérivé du bleu primaire |
| Fond de section | `--adp-color-surface` | `#f4f8fc` | Bleu clair très désaturé — fonds alternés |
| Bordure discrète | `--adp-color-border` | `#d7e1ec` | Bleu-gris clair — séparateurs, cadres |

> [HYPOTHÈSE] Ces tokens ont été proposés par le projet pour la V1 — ils peuvent être ajustés par Julien HACHE lors de la recette Divi. Ils ne proviennent pas d'une extraction de la maquette mais d'une dérivation cohérente du bleu marine primaire.

---

## Notes

- Le logo est un monogramme géométrique (initiales "A", "d", "P" stylisées dans un cercle).
- `logo-white.png` est bien blanc sur fond transparent — invisible sur fond blanc, prévu pour le header sombre.
- La photo `hero-bg.png` est cadrée avec un espace blanc à gauche — conçue pour la colonne droite du hero (55%).
- La typographie visible dans la maquette n'est pas déterminable avec certitude depuis le PNG. [FAIT]
- [FAIT — validation chef de projet / carte blanche client] Le choix de police est laissé au projet. Préconisation actuelle : `Inter`, avec `DM Sans` comme alternative crédible.
