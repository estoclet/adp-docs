# Architecture web cible

**Statut** : Cadrage initial — éléments fermes + hypothèses  
**Dernière mise à jour** : 2026-04-24  
**Lié à** : `ADR-001`, `04-architecture/`, `01-perimetre-projet.md`

---

## Stack technique retenu

| Composant | Valeur | Statut |
|-----------|--------|--------|
| CMS | WordPress (dernière version stable) | [FAIT — décision client] |
| Page builder | Divi (Elegant Themes) | [FAIT — décision client] |
| Hébergement | Inconnu | [À ARBITRER — I-01] |
| PHP | >= 8.1 recommandé | [HYPOTHÈSE — dépend hébergeur] |
| Base de données | MySQL / MariaDB | [FAIT — standard WP] |
| CDN | Non défini | [À ARBITRER] |
| SSL | Obligatoire (HTTPS) | [FAIT — standard] |

> **Pour les agents** : Ne pas proposer de stack alternative. WordPress + Divi est une décision ferme (ADR-001). Si une contrainte technique rend cette stack inadaptée, créer un ADR et soumettre à validation humaine.

---

## Hébergement (inconnue I-01)

Options possibles [HYPOTHÈSE — non arbitré] :

| Option | Pour | Contre |
|--------|------|--------|
| Hébergement mutualisé WP | Économique, simple | Limites de performance, peu de contrôle |
| VPS (OVH, Infomaniak…) | Flexible, performant | Maintenance requise |
| WP Engine / Kinsta | Optimisé WP, CDN intégré | Coût plus élevé |
| Infomaniak Site Creator WP | Français, conforme RGPD | Moins flexible |

> [À ARBITRER] : Le choix de l'hébergeur impacte la configuration Divi, la mise en place du CDN et la stratégie de cache.

---

## Plugins WordPress prévus

Les plugins suivants sont **recommandés** pour ce type de projet [HYPOTHÈSE — à valider].  
Aucun plugin ne doit être ajouté sans validation dans ce document ou dans un ADR.

| Plugin | Rôle | Statut |
|--------|------|--------|
| Divi Builder | Page builder | [FAIT — inclus dans le thème] |
| Yoast SEO ou Rank Math | SEO on-page | [RECOMMANDÉ] |
| WP Rocket ou W3 Total Cache | Cache et performance | [RECOMMANDÉ] |
| Smush ou Imagify | Optimisation images | [RECOMMANDÉ] |
| UpdraftPlus | Sauvegardes | [RECOMMANDÉ] |
| Wordfence ou iThemes Security | Sécurité | [RECOMMANDÉ] |
| Contact Form 7 ou WPForms | Formulaire de contact | [RECOMMANDÉ] |
| Redirection | Gestion des redirections 301 | [RECOMMANDÉ — critique pour migration] |

> **Pour les agents** : Ne pas ajouter de plugins à cette liste sans validation. Ne pas supposer qu'un plugin est installé s'il n'est pas marqué [FAIT].

---

## Performance et Core Web Vitals

Objectifs cibles [HYPOTHÈSE — à confirmer avec le client] :

| Métrique | Cible | Notes |
|----------|-------|-------|
| LCP (Largest Contentful Paint) | < 2,5 s | Mobile prioritaire |
| FID / INP | < 200 ms | Divi peut alourdir le JS |
| CLS | < 0,1 | Attention aux blocs Divi dynamiques |
| PageSpeed Insights mobile | > 80 | Objectif raisonnable avec Divi |

> **Note** : Divi génère un CSS et un JS volumineux. La performance devra être travaillée (cache CSS Divi, désactivation des modules inutiles, lazy loading images).

---

## Sécurité

| Exigence | Priorité | Statut |
|----------|----------|--------|
| HTTPS obligatoire | Haute | [FAIT — standard] |
| Mises à jour WP / plugins automatisées ou surveillées | Haute | [À SPÉCIFIER] |
| Sauvegardes régulières | Haute | [À SPÉCIFIER] |
| Protection wp-admin | Haute | [À SPÉCIFIER] |
| RGPD : cookies, mentions légales | Haute | [À SPÉCIFIER] |

---

## SEO technique

| Point | Statut | Notes |
|-------|--------|-------|
| URLs permanentes (slugs propres) | [RECOMMANDÉ] | À configurer dès l'installation WP |
| Sitemap XML | [RECOMMANDÉ] | Via Yoast/Rank Math |
| Robots.txt | [RECOMMANDÉ] | À personnaliser |
| Redirections 301 legacy | [CRITIQUE] | [DÉPENDANCE] → I-03 + mapping legacy |
| Schema.org | [HYPOTHÈSE] | À évaluer selon types de contenu |

---

## Ce que ce document ne contient pas

- L'arborescence des pages (voir `04-architecture/01-arborescence-site.md`)
- Les types de contenus WP (voir `04-architecture/02-types-contenus.md`)
- Les composants Divi (voir `04-architecture/03-composants-divi.md`)
- Les specs de pages individuelles (voir `05-specs/pages/`)
