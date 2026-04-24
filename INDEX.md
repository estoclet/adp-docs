# INDEX — Carte de navigation pour agents

**Usage** : Ce fichier permet à un agent de localiser rapidement le bon document.  
**Règle** : Ne pas écrire de contenu ici. Uniquement des pointeurs vers d'autres fichiers.  
**Priorité de lecture** : `00-initialisation-projet.md` → `02-gouvernance-ia/01-regles-ia.md` → ce fichier.

---

## Démarrage obligatoire

| Étape | Fichier | Contenu |
|-------|---------|---------|
| 1 | `00-initialisation-projet.md` | Contexte, décisions prises, inconnues bloquantes |
| 2 | `02-gouvernance-ia/01-regles-ia.md` | Règles opérationnelles pour tout agent |
| 3 | `02-gouvernance-ia/02-conventions-redaction.md` | Marqueurs et discipline d'écriture |
| 4 | `02-gouvernance-ia/03-perimetre-agents.md` | Ce que l'agent peut et ne peut pas faire |
| 5 | `02-gouvernance-ia/04-anti-patterns.md` | Catalogue des dérives récurrentes à éviter |

---

## Cadrage projet

| Sujet | Fichier |
|-------|---------|
| Périmètre, objectifs, exclusions | `01-cadrage/01-perimetre-projet.md` |
| Architecture technique cible | `01-cadrage/02-architecture-cible.md` |
| Backoffice et gestion de contenu | `01-cadrage/03-backoffice-gestionnaire.md` |
| Stratégie de migration legacy → nouveau | `01-cadrage/04-strategie-migration.md` |
| Assets design (logo, palette, maquette) | `01-cadrage/05-assets-design.md` |

## Analyse de l'existant (legacy)

| Sujet | Fichier | État |
|-------|---------|------|
| Inventaire structure et contenu | `03-legacy/01-inventaire-legacy.md` | Terminé — à valider (TP-001) |
| Analyse éditoriale du contenu | `03-legacy/02-analyse-contenu.md` | Terminé — à valider |
| Mapping pages legacy → nouveau site | `03-legacy/03-mapping-migration.md` | Terminé — à valider (1 proposition) |

## Architecture cible

| Sujet | Fichier |
|-------|---------|
| Arborescence du site | `04-architecture/01-arborescence-site.md` |
| Types de contenus WordPress | `04-architecture/02-types-contenus.md` |
| Composants Divi réutilisables | `04-architecture/03-composants-divi.md` |
| Conventions Divi et CSS | `04-architecture/04-conventions-divi.md` |

## Specs fonctionnelles et pages

| Sujet | Fichier | État |
|-------|---------|------|
| Page d'accueil | `05-specs/pages/homepage.md` | Validé client (2026-04-23) |
| Template spec de page | `05-specs/pages/_template-page-spec.md` | Prêt |
| Brief fonctionnel : recherche | `05-specs/fonctionnelles/recherche.md` | Ébauche initiale |
| Template brief fonctionnel | `05-specs/fonctionnelles/_template-brief-fonctionnel.md` | Prêt |

## Décisions (ADRs)

| Décision | Fichier | Statut |
|----------|---------|--------|
| ADR-001 : WordPress + Divi | `06-decisions/ADR-001-wordpress-divi.md` | Acceptée |
| ADR-002 : Identité visuelle et charte Divi | `06-decisions/ADR-002-identite-visuelle.md` | Acceptée — palette précisée dans `01-cadrage/05-assets-design.md` |
| Template ADR | `06-decisions/_template-adr.md` | Prêt |

## Pilotage

| Sujet | Fichier / URL |
|-------|--------------|
| **GitHub Issues** (tickets) | https://github.com/estoclet/adp-docs/issues |
| **Tableau de bord** (GitHub Pages) | https://estoclet.github.io/adp-docs/ |
| Gouvernance GitHub Issues + labels | `07-pilotage/03-github-issues-gouvernance.md` |
| Plan de travail / lotissement | `07-pilotage/01-lotissement.md` |
| Journal des décisions | `07-pilotage/02-journal-decisions.md` |
| Template task pack | `07-pilotage/task-packs/_template-task-pack.md` |
| TP-001 : Analyse du legacy | `07-pilotage/task-packs/TP-001-analyse-legacy.md` |
| TP-005 : Intégration Divi homepage | `07-pilotage/task-packs/TP-005-homepage-divi.md` |

## Handoffs

| Sujet | Fichier |
|-------|---------|
| Template de passation entre agents | `08-handoffs/_template-handoff.md` |

---

## Légende des états

| Marqueur | Sens |
|----------|------|
| [FAIT] | Information vérifiée, sourcée |
| [HYPOTHÈSE] | À valider — ne pas traiter comme un fait |
| [À ARBITRER] | Décision humaine requise |
| [DÉPENDANCE] | Bloqué par un autre travail ou une autre décision |
| [INCONNUE] | Information manquante, impact à évaluer |
| [RÉSOLU] | Inconnue levée — valeur et source citées |
| [RÉSOLU PARTIEL] | Inconnue partiellement levée — reste une portion à confirmer |
| [OBSOLÈTE] | Plus valide — ne pas utiliser |
