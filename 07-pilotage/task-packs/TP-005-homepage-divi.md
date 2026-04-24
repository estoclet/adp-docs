# TP-005 — Intégration Divi de la page d'accueil

**Statut** : À lancer — prérequis remplis (2026-04-24)
**Date de création** : 2026-04-24
**Agent assigné** : Agent IA (Claude ou Codex) + développeur WP/Divi
**Durée estimée** : Long (dépend de la disponibilité des assets client)
**Lié au lot** : Lot 3 — Développement et intégration

---

## Objectif unique

Construire la page d'accueil complète dans Divi (dans `adp-app/`) conformément à la spec validée, avec tous les blocs, les composants globaux (header/footer), et le CSS custom nécessaire.

---

## Prérequis avant de lancer ce task pack

Ce task pack **ne peut pas démarrer** tant que les éléments suivants ne sont pas disponibles :

| Prérequis | Fournisseur | Statut |
|-----------|------------|--------|
| WordPress installé et configuré dans `adp-app/` | Projet | [FAIT — DDEV adp-app, WP 6.9.4 fr_FR] |
| Divi 5.3.3 installé et actif dans `adp-app/` | Projet | [FAIT — commit 069d734 adp-app, zip fourni 2026-04-24] |
| Thème enfant `adp-divi-child` actif | Projet | [FAIT — commit 7a389ee adp-app] |
| Logo / monogramme PNG fond transparent | Julien HACHE | [FAIT — `adp-app/assets/design/logo-dark.png` + `logo-white.png`] |
| Palette V1 documentée | Projet | [FAIT — `#1e3264` + `#0070c8` — voir `01-cadrage/05-assets-design.md`] |
| Police validée | Projet (carte blanche client) | [FAIT — `Inter`] |
| Adresse email de contact | Julien HACHE | [FAIT — julien.hache@astucesdepomme.com] |
| Zone / communes d'intervention | Julien HACHE | [FAIT — Région Lilloise, 60km autour d'Houplines] |
| Textes descriptifs cartes (blocs 3 et 5) | Projet | [FAIT — propositions dans `05-specs/pages/homepage.md`] |
| Image hero | Projet | [FAIT — `adp-app/assets/design/hero-bg.png`] |
| Mention légale crédit d'impôt | Source legacy | [FAIT — "Dans les limites prévues à l'article 199 sexdecies du CGI"] |
| Spec homepage complète | Projet | [FAIT — `05-specs/pages/homepage.md` validée client] |
| Specs pages secondaires | Projet | [FAIT — `05-specs/pages/prestations.md`, `formations.md`, `a-propos.md`, `avis.md`, `contact.md`] |

---

## Contexte minimal

- Projet : Refonte d'astucesdepomme.com
- Client : Julien HACHE — assistance Apple, formation, réseau, démarches, services à la personne
- Chef de projet : Eric STOCLET
- Stack : WordPress + Divi dans `adp-app/`
- Information projet : une licence Divi existe déjà sur l'instance legacy et doit être réutilisée dans `adp-app`
- Repo applicatif : git@github.com:estoclet/adp-app.git
- Brief homepage complet : `adp-docs/05-specs/pages/homepage.md`
- Charte visuelle : `adp-docs/06-decisions/ADR-002-identite-visuelle.md`
- Composants Divi : `adp-docs/04-architecture/03-composants-divi.md`

---

## Fichiers à lire (inputs)

| Fichier | Pourquoi |
|---------|---------|
| `adp-docs/02-gouvernance-ia/01-regles-ia.md` | Règles obligatoires |
| `adp-docs/02-gouvernance-ia/02-conventions-redaction.md` | Conventions |
| `adp-docs/05-specs/pages/homepage.md` | Spec complète à implémenter — source de vérité |
| `adp-docs/06-decisions/ADR-002-identite-visuelle.md` | Charte visuelle |
| `adp-docs/04-architecture/03-composants-divi.md` | Modules, presets, CSS à prévoir |
| `adp-docs/04-architecture/01-arborescence-site.md` | URLs cibles pour les liens |

---

## Fichiers à produire ou modifier (outputs)

Ce task pack travaille dans `adp-app/` (code du site), pas dans `adp-docs/`.

| Cible | Action | Description |
|-------|--------|-------------|
| Theme Builder Divi | Créer | Header global + Footer global |
| Page d'accueil Divi | Créer | 9 blocs conformes à la spec homepage |
| Presets Divi | Créer | Bouton principal, bouton secondaire, titre H2, carte |
| CSS custom Divi | Ajouter | Selon liste dans `03-composants-divi.md` |
| Divi Library | Sauvegarder | Composants réutilisables (carte, CTA, bandeau) |

---

## Ordre de construction recommandé

1. Configurer la police dans les réglages Divi
2. Créer les presets boutons et titres dans Divi
3. Construire le Header global (Theme Builder)
4. Construire le Footer global (Theme Builder)
5. Créer la page d'accueil — bloc par bloc dans l'ordre de la spec
6. Ajouter le CSS custom (coins, hover, pills, responsive)
7. Tester en desktop, tablette, mobile
8. Corriger les problèmes de responsive

---

## Contraintes impératives

- [ ] Respecter strictement la spec `homepage.md` — pas de blocs supplémentaires
- [ ] Réutiliser la licence Divi issue du legacy lors de l'activation de Divi dans `adp-app`
- [ ] Ne jamais versionner ni documenter en clair un secret de licence Divi
- [ ] Ne pas inventer de texte hors cadre documenté : utiliser les textes validés dans `homepage.md` ou des placeholders `[TEXTE_À_FOURNIR]` si un contenu reste vraiment manquant
- [ ] Pas de couleurs inventées — utiliser les valeurs hex fournies uniquement
- [ ] Utiliser uniquement les modules Divi listés dans `03-composants-divi.md`
- [ ] Sauvegarder les composants réutilisables en Divi Library
- [ ] Tester le responsive sur les 3 breakpoints Divi (desktop, tablette, mobile)
- [ ] Ne pas modifier `adp-docs/` pendant ce task pack

---

## Critères de validation (Eric STOCLET)

- [ ] Header présent sur toutes les pages, sticky, fond sombre
- [ ] Footer présent sur toutes les pages, 4 colonnes, clair
- [ ] 9 blocs homepage présents dans le bon ordre
- [ ] Palette de couleurs respectée
- [ ] Numéro de téléphone cliquable (`tel:0651311537`)
- [ ] CTA "Prendre rendez-vous" visible dès le hero
- [ ] Bandeau 50% crédit d'impôt visible et lisible
- [ ] Coins arrondis cohérents (16-24px)
- [ ] Ombres légères uniquement
- [ ] Rendu mobile satisfaisant (empilement propre)
- [ ] Aucun texte inventé — placeholders visibles pour les contenus manquants

---

## Ce que cet agent ne doit pas faire

- Inventer des textes de contenu (descriptions de prestations, textes "À propos"…)
- Inventer des valeurs hex
- Ajouter des blocs non prévus dans la spec
- Modifier les fichiers de `adp-docs/`
- Créer des pages autres que la page d'accueil

---

## Prochaine étape après validation

Créer les pages secondaires : `/prestations/`, `/formations/`, `/contact/` — sur la base de leurs specs respectives (à rédiger).
