# Stratégie de migration legacy → nouveau site

**Statut** : Hypothèses initiales — dépend de l'analyse legacy  
**Dernière mise à jour** : 2026-04-24  
**Lié à** : `03-legacy/`, `04-architecture/01-arborescence-site.md`, I-02, I-03, I-06

> **Note agent** : Ce document définit l'approche de migration. Il sera affiné après l'analyse legacy (TP-001 et TP-002). Ne pas engager de migration sans validation humaine des priorités et du mapping (voir `03-legacy/03-mapping-migration.md`).

---

## Principe directeur

La migration est **sélective, pas exhaustive**.  
Objectif : reprendre le contenu qui a de la valeur, pas tout migrer mécaniquement.

---

## Approche retenue (hypothèse)

[HYPOTHÈSE — à valider après analyse legacy]

**Migration par lots progressifs** :
1. Inventorier le contenu existant (TP-001)
2. Qualifier chaque contenu (garder / réécrire / archiver / supprimer)
3. Prioriser par trafic SEO, valeur métier et effort
4. Migrer par ordre de priorité, valider avant de passer au lot suivant

> [À ARBITRER] : Migration simultanée (remplacement en une fois) ou progressive (coexistence temporaire) ? La réponse dépend du budget, des délais et du risque SEO accepté.

---

## Qualification du contenu

Chaque contenu legacy sera classé dans l'une de ces catégories :

| Catégorie | Définition | Action |
|-----------|-----------|--------|
| **Garder** | Contenu à jour, trafic, valeur | Migrer tel quel ou avec mise à jour mineure |
| **Réécrire** | Sujet valable mais contenu obsolète/faible | Réécriture avant migration |
| **Archiver** | Contenu hors sujet ou périmé | Ne pas migrer, ne pas rediriger |
| **Supprimer** | Contenu de faible qualité sans valeur | Supprimer, rediriger vers page de catégorie si URL connue |

> **Règle** : Toute décision de suppression doit être validée par un humain. Les agents ne suppriment pas de contenu sans autorisation explicite.

---

## Risques SEO et mitigation

| Risque | Probabilité | Mitigation |
|--------|-------------|------------|
| Perte de trafic sur URLs supprimées | Haute | Redirections 301 vers pages équivalentes |
| Perte de backlinks externes | Moyenne | Inventaire des backlinks avant migration |
| Duplicate content pendant transition | Haute si coexistence | Canonicals, noindex temporaires |
| Désindexation accidentelle | Faible si maîtrisé | Vérifier robots.txt + GSC après mise en ligne |

> [DÉPENDANCE] : La stratégie de redirections 301 dépend de I-03 (changement de domaine ?) et du mapping `03-legacy/03-mapping-migration.md`.

---

## Prérequis avant migration

| Prérequis | Statut | Bloque |
|-----------|--------|--------|
| Inventaire legacy complet | [À FAIRE — TP-001] | Tout |
| Analyse éditoriale du contenu | [À FAIRE — TP-002] | Qualification |
| Mapping URL legacy → nouvelle URL | [À FAIRE] | Redirections |
| Arbitrage I-03 (domaine) | [À ARBITRER] | Redirections |
| Accès BDD legacy (I-06) | [À CONFIRMER] | Export WP XML ou migration directe |
| Arborescence cible validée | [À VALIDER] | Mapping URLs |

---

## Méthode d'export du contenu legacy

[HYPOTHÈSE — dépend de I-06]

Options possibles :

| Méthode | Conditions | Avantages | Risques |
|---------|-----------|-----------|---------|
| Export XML WordPress natif | Accès WP admin legacy | Simple, natif | Importe aussi les médias liés |
| Export direct BDD MySQL | Accès BDD (I-06) | Plus complet | Complexe, risque de données parasites |
| Copie manuelle | Toujours possible | Sélectif | Long, erreurs |
| Plugin WPAllImport | Accès WP admin legacy | Flexible | Plugin payant |

> [À ARBITRER] : La méthode d'export doit être choisie après confirmation de I-06.

---

## Checklist de mise en ligne

[HYPOTHÈSE — à compléter selon le contexte]

- [ ] Redirections 301 configurées et testées
- [ ] Sitemap XML soumis à Google Search Console
- [ ] robots.txt vérifié (aucun noindex accidentel)
- [ ] Test performance mobile (PageSpeed > 80)
- [ ] Test formulaires de contact
- [ ] Test navigation et liens internes
- [ ] Sauvegarde complète avant bascule
- [ ] DNS pointant vers le nouveau site
- [ ] Ancien site désactivé ou en maintenance

---

## Ce que ce document ne contient pas

- L'inventaire du contenu legacy (voir `03-legacy/01-inventaire-legacy.md`)
- Le mapping URL détaillé (voir `03-legacy/03-mapping-migration.md`)
- Les specs des pages cibles (voir `05-specs/pages/`)
