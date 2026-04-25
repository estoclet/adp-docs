# Périmètre et objectifs du projet

**Statut** : Cadrage initial — à valider avec le client  
**Dernière mise à jour** : 2026-04-25 — iter.8 (normalisation marqueurs), R-27 appliqué  
**Lié à** : `00-initialisation-projet.md`, `ADR-001`

---

## Objectifs du projet

### Objectifs métier

| # | Objectif | Priorité | Statut |
|---|----------|----------|--------|
| O-01 | Améliorer la réassurance des visiteurs (crédibilité, professionnalisme) | Haute | [FAIT — exprimé client] |
| O-02 | Améliorer la lisibilité et l'accessibilité du contenu | Haute | [FAIT — exprimé client] |
| O-03 | Améliorer la conversion (contact, abonnement, demande d'aide) | Haute | [FAIT — exprimé client] |
| O-04 | Donner une image plus structurée et professionnelle | Haute | [FAIT — exprimé client] |

### Objectifs techniques

| # | Objectif | Priorité | Statut |
|---|----------|----------|--------|
| T-01 | Conserver WordPress + Divi comme stack | Haute | [FAIT — décision client] |
| T-02 | Assurer la reprise du contenu utile du legacy | Haute | [FAIT] |
| T-03 | Garantir une bonne performance (Core Web Vitals) | Moyenne | [HYPOTHÈSE — à spécifier] |
| T-04 | Assurer la continuité SEO (redirections, structure URLs) | Haute | [FAIT — I-03 résolu : domaine conservé, redirections 301 suffisantes] |

---

## Périmètre IN (ce qui est dans le projet)

- Conception et développement du nouveau site WordPress + Divi dans `adp-app/`
- Analyse du site legacy dans `adp-legacy/`
- Migration du contenu utile (articles, pages, médias)
- Gouvernance documentaire dans `adp-docs/`
- Architecture de l'information et arborescence cible
- Specs des pages principales
- Charte Divi (typographie, couleurs, composants) [HYPOTHÈSE — à confirmer si inclus]
- SEO on-page de base

---

## Périmètre OUT (ce qui n'est pas dans le projet)

- Rédaction de contenu nouveau (sauf si explicitement commandé) [HYPOTHÈSE]
- Refonte de la charte graphique complète (logo, identité) [FAIT — I-07 résolu : conservation de l'identité existante, pas de refonte]
- Développement d'une application mobile
- Mise en place d'un espace client / extranet
- Intégration d'un CRM ou outil de ticketing
- Hébergement et infogérance (sauf si inclus explicitement) [HYPOTHÈSE]
- Formation du client à WordPress (sauf si commandée) [HYPOTHÈSE]

> **Note agent** : Les éléments marqués [HYPOTHÈSE] dans cette section doivent être confirmés avec le client avant d'être traités comme des exclusions fermes.

---

## Contraintes connues

| Contrainte | Type | Source |
|------------|------|--------|
| Stack WordPress + Divi imposé | Technique | Décision client |
| Contenu legacy à reprendre (pas de départ de zéro) | Contenu | Contexte projet |
| Hébergement OVHcloud Hébergement Pro | Technique | [FAIT — I-01 résolu : VPS OVH préprod + mutualisé OVH prod] |
| Budget et délais non communiqués | Gestion | [À ARBITRER — I-04] |

---

## Parties prenantes

| Rôle | Responsabilité | Statut info |
|------|----------------|-------------|
| Client / propriétaire du site | Décisions finales, contenu, arbitrages | [FAIT — Julien HACHE, indépendant] |
| Chef de projet | Pilotage, gouvernance documentaire | [FAIT] |
| Agents IA | Production de contenu bornée, analyse | [FAIT] |
| Développeur WP/Divi | Intégration technique | [À IDENTIFIER] |

---

## Critères de succès

Ces critères permettront de valider que le projet a atteint ses objectifs.  
[HYPOTHÈSE — à valider avec le client]

- Le nouveau site remplace l'ancien sans perte de contenu utile identifié
- Les pages principales respectent les specs validées
- Le temps de chargement est inférieur à 3 s sur mobile (LCP)
- Les URLs legacy sont redirigées (301) vers les nouvelles URLs
- Le client est autonome sur la gestion du contenu WordPress

---

## Ce que ce document ne contient pas

- Le backlog (vit dans l'outil de gestion de projet)
- Les specs détaillées de pages (voir `05-specs/pages/`)
- L'architecture technique (voir `01-cadrage/02-architecture-cible.md`)
- Les décisions d'architecture (voir `06-decisions/`)
