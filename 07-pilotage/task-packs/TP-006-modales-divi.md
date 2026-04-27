# TP-006 — Implémentation des modales Divi

**Statut** : À lancer  
**Date de création** : 2026-04-27  
**Agent assigné** : Agent IA (Claude ou Codex) + développeur WP/Divi  
**Durée estimée** : Moyen  
**Lié au lot** : Lot 3 — Développement et intégration

---

## Objectif unique

Implémenter les 5 modales du site (Prestations, Formations, À propos, Avis, Contact) dans Divi 5 en utilisant la Méthode A (Interactions + Visibilité), conformément à l'ADR-003 et aux spécifications de contenu.

---

## Contexte minimal

- Projet : Refonte d'astucesdepomme.com (WordPress + Divi)
- Client : Julien HACHE
- Chef de projet : Eric STOCLET
- Architecture : One-page (ADR-003). La homepage déclenche des modales pour le contenu détaillé.
- Technique : Divi 5 popup natif. Les modales doivent être éditables par le client dans le Visual Builder.
- Instance : `adp-app/` (DDEV local : `http://adp.ddev.site`)

---

## Fichiers à lire (inputs)

| Fichier | Pourquoi |
|---------|---------|
| `adp-docs/02-gouvernance-ia/01-regles-ia.md` | Règles obligatoires (R-17, R-18, R-25) |
| `adp-docs/06-decisions/ADR-003-architecture-one-page.md` | Décision structurante one-page |
| `adp-docs/04-architecture/03-composants-divi.md` | Méthode technique popup Divi 5 |
| `adp-docs/05-specs/pages/homepage.md` | Déclencheurs (IDs des boutons/liens) |
| `adp-docs/05-specs/pages/prestations.md` | Contenu de la modale Prestations |
| `adp-docs/05-specs/pages/formations.md` | Contenu de la modale Formations |
| `adp-docs/05-specs/pages/a-propos.md` | Contenu de la modale À propos |
| `adp-docs/05-specs/pages/avis.md` | Contenu de la modale Avis |
| `adp-docs/05-specs/pages/contact.md` | Contenu de la modale Contact |

---

## Fichiers à produire ou modifier (outputs)

Ce task pack travaille dans `adp-app/` (code et exports du site).

| Cible | Action | Description |
|-------|--------|-------------|
| Page d'accueil Divi | Modifier | Ajouter les conteneurs de modales et configurer les interactions |
| Divi Library | Sauvegarder | Exporter chaque modale en tant que composant de bibliothèque |
| `adp-app/divi-exports/` | Créer/Compléter | Exports JSON des modales pour versionnement |

---

## Ordre de construction recommandé

1. Créer la modale **Prestations** (ID `#modal-prestations`) : structure scrollable, 6 sections.
2. Créer la modale **Formations** (ID `#modal-formations`) : approche pédagogique + thématiques.
3. Créer la modale **À propos** (ID `#modal-a-propos`) : photo Julien HACHE + bio + SAP.
4. Créer la modale **Avis** (ID `#modal-avis`) : sélection d'avis (placeholders).
5. Créer la modale **Contact** (ID `#modal-contact`) : formulaire WPForms Lite + coordonnées.
6. Configurer les déclencheurs (Interactions Divi) sur les boutons de la homepage.
7. Tester la fermeture (croix, clic extérieur, boutons de sortie).
8. Vérifier l'éditabilité dans le Visual Builder (conformité D-019).

---

## Contraintes impératives

- [ ] Utiliser exclusivement la **Méthode A** (Interactions + Visibilité) pour permettre l'édition directe par le client.
- [ ] Respecter les IDs définis dans les specs pour assurer la liaison avec la homepage.
- [ ] Pas de CSS inline : utiliser les classes du thème enfant si nécessaire.
- [ ] Les modales doivent être responsives (défilement vertical fluide sur mobile).
- [ ] Sauvegarder chaque modale dans la Divi Library.
- [ ] Exporter en JSON vers `adp-app/divi-exports/` après finalisation.
- [ ] Ne pas modifier `adp-docs/` pendant ce task pack.

---

## Critères de validation (pour le chef de projet)

- [ ] Les 5 modales s'ouvrent correctement depuis leurs déclencheurs respectifs.
- [ ] Le contenu est conforme aux spécifications (Prestations, Formations, À propos).
- [ ] La modale Contact contient un formulaire fonctionnel (ou placeholder WPForms).
- [ ] La fermeture est intuitive et fonctionnelle sur tous les supports.
- [ ] Les modales sont éditables par un non-technicien dans le Visual Builder.
- [ ] Les exports JSON sont présents dans `adp-app/divi-exports/`.

---

## Ce que cet agent ne doit pas faire

- Modifier la structure globale des blocs de la homepage (hors ajout des modales).
- Inventer des textes biographiques pour Julien HACHE (utiliser les placeholders).
- Configurer les APIs réelles pour les avis Google (statique/placeholder en V1).
- Modifier `00-initialisation-projet.md`.

---

## Prochaine étape après validation

Recette globale avec le client (Julien HACHE) sur l'instance de préprod.
