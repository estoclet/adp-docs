# Handoff — Pré-lancement TP-005 : Intégration Divi Homepage

**Date** : 2026-04-25 — mis à jour ; document désormais obsolète depuis la réalisation de TP-005 et les travaux de prise en main client du 2026-04-29  
**De** : Agent IA (boucle gouvernance + maintenance projet)  
**À** : Agent IA ou développeur WP/Divi exécutant TP-005  
**Tâche ou lot** : Lot 3 — TP-005 Intégration Divi Homepage  
**Lié à** : `07-pilotage/task-packs/TP-005-homepage-divi.md`

---

## Ce qui a été accompli

- [x] WordPress 6.9.4 fr_FR installé dans `adp-app/` via DDEV (`http://adp.ddev.site`) — validé
- [x] Divi 5.3.3 (thème parent) installé et actif — commit `069d734`
- [x] `adp-divi-child` v0.1.0 activé (thème enfant) — commit `7a389ee`
- [x] CSS custom de base versionnée dans `adp-divi-child/assets/css/theme.css` : tokens couleurs, `.adp-card-service`, `.adp-pill-theme`, `.adp-btn-secondary`, responsive mobile
- [x] 6 plugins actifs : AIOSEO, Complianz, Imagify, Redirection, UpdraftPlus, WPForms Lite (socle V1 validé — vérifié 2026-04-25)
- [x] 11 pages WordPress publiées avec les bons slugs (vérifié ddev 2026-04-25)
- [x] Structure de permaliens corrigée : `/%postname%/` (anciennement date-based — corrigé 2026-04-25 via ddev wp rewrite)
- [x] Menu principal ordonné : Accueil · Prestations · Formations · À propos · Avis · Contact
- [x] Menu footer configuré (5 liens légaux)
- [x] Assets design versionnés dans `adp-app/assets/design/` : logo-dark.png, logo-white.png, hero-bg.png, maquette_homepage.png
- [x] Homepage intégrée, relue visuellement puis raffinée (hero full width, section Services retravaillée, direction premium local rassurant)
- [x] Documentation client créée dans `adp-app/documentation-client/`
- [x] Documentation client intégrée dans le backoffice WordPress via `adp-client-documentation`

---

## État des fichiers concernés

| Fichier | État | Notes |
|---------|------|-------|
| `adp-docs/05-specs/pages/homepage.md` | Complet — validé client | Source de vérité pour TP-005 |
| `adp-docs/04-architecture/03-composants-divi.md` | Complet | Modules, presets, CSS, Library |
| `adp-docs/04-architecture/04-conventions-divi.md` | Complet | Nommage presets, Library, CSS, tokens et classes versionnés |
| `adp-docs/06-decisions/ADR-002-identite-visuelle.md` | Complet | Palette, typo, style général |
| `adp-docs/04-architecture/01-arborescence-site.md` | Complet | URLs cibles pour les liens internes |
| `adp-app/web/wp-content/themes/adp-divi-child/assets/css/theme.css` | Complet | CSS base déjà versionnée |
| `adp-app/assets/design/maquette_homepage.png` | Disponible | Référence visuelle à consulter |

---

## Ce qui reste à faire (dans TP-005)

> **[OBSOLÈTE — 2026-04-29]** La liste ci-dessous correspond au pré-lancement historique de TP-005. Le task pack est désormais terminé ; conserver ce handoff uniquement comme archive de contexte.

- [ ] Configurer la police `Inter` dans les réglages Divi (Divi → Theme Options → General)
- [ ] Créer les presets boutons et titres dans Divi (4 presets : bouton-primaire, bouton-secondaire, titre-section, carte-service)
- [ ] Construire le Header global dans le Theme Builder (logo blanc + menu + bouton CTA)
- [ ] Construire le Footer global dans le Theme Builder (4 colonnes + réseaux)
- [ ] Créer la page d'accueil — 9 blocs conformes à `05-specs/pages/homepage.md`
- [ ] Ajouter le CSS custom (header sticky) — `.adp-card-service`, `.adp-pill-theme` déjà en place
- [ ] Exporter Theme Builder + Library en JSON vers `adp-app/divi-exports/` (créer le dossier)
- [ ] Tester desktop (1440px) / tablette / mobile
- [ ] Commiter les exports JSON Divi dans adp-app

---

## Hypothèses posées

- La police `Inter` est chargée via Divi (Google Fonts) — pas de fichier local à prévoir en V1
- Le CTA "Prendre rendez-vous" pointe vers `/contact/` en attendant la mise en place de la modale
- Les liens internes (Prestations, Formations, etc.) pointent vers les slugs déjà créés
- La license Divi doit être activée via les identifiants Elegant Themes de Julien HACHE — non automatique depuis le zip

---

## Inconnues non résolues

**Décision Eric STOCLET (2026-04-25, D-016) : toutes les images et zones de texte manquantes sont couvertes par des placeholders — Julien HACHE les remplacera après livraison en préprod.**

> **[FAIT — D-018 + D-019, 2026-04-25]** Site one page confirmé. Spec homepage révisée : 10 blocs (Bloc 7 À propos ajouté), anchors CSS, liens "Voir plus" → popup. ADR-003 créé. Popup Divi 5 **Méthode A (Interactions + Visibilité)** retenue pour toutes les modales — éditabilité client confirmée via documentation Elegant Themes. Voir `04-architecture/03-composants-divi.md`.

> **Prochaine validation** : Eric STOCLET valide `05-specs/pages/homepage.md` (statut "Révisé — à valider") avant de lancer TP-005.

| Inconnue | Impact | Statut |
|----------|--------|--------|
| Licence Divi non activée | Divi peut fonctionner sans licence mais sans mises à jour ni assets premium | En attente Julien HACHE |
| Badge SAP (logo officiel Services à la personne) | **Placeholder acceptable** — utiliser un bloc texte ou un carré coloré | Placeholder en TP-005 |
| Tons complémentaires (gris texte, bleu clair fond) | Proposés dans `theme.css` : texte `#23344d`, fond `#f4f8fc`, bordure `#d7e1ec` — à valider lors de la recette Divi | Julien HACHE |
| Photo Julien HACHE (I-15) | `adp-app/assets/design/julien-hache-portrait.png` — 810×552 px | **[RÉSOLU — D-020]** |
| Bio Julien HACHE (I-16) | Spec `/a-propos/` — **placeholder acceptable** | Placeholder |
| Avis GBP + URL fiche (I-18/19) | Modale Avis — **placeholder acceptable** | Placeholder |
| Implémentation modales Contact/Avis | Hors scope TP-005 — à arbitrer séparément | Eric STOCLET |
| Page draft `politique-de-confidentialite` | Doublon présumé de `politique-confidentialite` publiée — à supprimer | Eric STOCLET |

---

## Points d'attention pour le récepteur

- **Ne jamais versionner** la clé de licence Divi ni les identifiants Elegant Themes (R-19)
- **Utiliser le CSS class** `adp-card-service`, `adp-pill-theme`, `adp-btn-secondary` — déjà définies dans le thème enfant, pas dans les modules Divi
- **Le CSS inline dans les modules Divi est interdit** — voir `04-conventions-divi.md`
- **Exporter en JSON** après chaque composant structurant (Theme Builder, Library) dans `adp-app/divi-exports/`
- **Nommer selon la convention** : `TB - Header - Global`, `LIB - CTA - Dark`, etc.
- La maquette `maquette_homepage.png` est la référence visuelle primaire pour les détails non documentés

---

## Fichiers à lire en priorité avant de commencer

1. `adp-docs/02-gouvernance-ia/01-regles-ia.md` — règles R-17, R-18, R-19, R-25
2. `adp-docs/05-specs/pages/homepage.md` — spec complète (source de vérité TP-005)
3. `adp-docs/04-architecture/03-composants-divi.md` — modules, presets, CSS
4. `adp-docs/06-decisions/ADR-002-identite-visuelle.md` — charte visuelle
5. `adp-docs/04-architecture/01-arborescence-site.md` — URLs cibles

---

## Validation requise avant de poursuivre

- [ ] Eric STOCLET : valider que DDEV est démarré (`ddev start`) avant de lancer TP-005
- [ ] Eric STOCLET : confirmer que la licence Divi peut fonctionner sans activation pour V1 locale (ou prévoir l'activation avec Julien HACHE)
- [ ] Eric STOCLET : valider `05-specs/pages/homepage.md` (révisée D-018 — 10 blocs, statut "Révisé — à valider") — ADR-003 créé, spec révisée par l'agent

---

## Note de clôture

Pour l'état actuel du projet, ne plus utiliser ce handoff comme point d'entrée principal.

Lire à la place :
- `07-pilotage/task-packs/TP-005-homepage-divi.md`
- `01-cadrage/03-backoffice-gestionnaire.md`
- `05-specs/pages/homepage.md`
