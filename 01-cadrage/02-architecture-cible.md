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
| Environnement local | DDEV projet `adp` | [FAIT — voir `adp-app/.ddev/config.yaml`] |
| Hébergement | OVHcloud `Hébergement Pro` | [FAIT — validation client 2026-04-24] |
| PHP | 8.3 en local | [FAIT — voir `adp-app/.ddev/config.yaml`] |
| Base de données | MariaDB 11.8 en local | [FAIT — voir `adp-app/.ddev/config.yaml`] |
| Web server local | nginx-fpm | [FAIT — voir `adp-app/.ddev/config.yaml`] |
| Docroot local | `web` | [FAIT — voir `adp-app/.ddev/config.yaml`] |
| QA automatisée locale | Playwright + `axe-playwright` | [FAIT — voir `adp-app/package.json`] |
| CDN | Non défini | [À ARBITRER] |
| SSL | Obligatoire (HTTPS) | [FAIT — standard] |

> **Pour les agents** : Ne pas proposer de stack alternative. WordPress + Divi est une décision ferme (ADR-001). Si une contrainte technique rend cette stack inadaptée, créer un ADR et soumettre à validation humaine.

---

## Environnement local actuellement en place

| Élément | Valeur | Statut |
|---------|--------|--------|
| Nom DDEV | `adp` | [FAIT — voir `adp-app/.ddev/config.yaml`] |
| Type de projet DDEV | `wordpress` | [FAIT — voir `adp-app/.ddev/config.yaml`] |
| URL locale de base | `http://adp.ddev.site` | [FAIT — voir `adp-app/playwright.config.ts`, `adp-app/bin/screenshot.js`] |
| Docroot | `web` | [FAIT — voir `adp-app/.ddev/config.yaml`] |
| PHP local | `8.3` | [FAIT — voir `adp-app/.ddev/config.yaml`] |
| Base locale | MariaDB `11.8` | [FAIT — voir `adp-app/.ddev/config.yaml`] |
| Web server local | `nginx-fpm` | [FAIT — voir `adp-app/.ddev/config.yaml`] |

> [FAIT] L'environnement local applicatif est opérationnel dans `adp-app/` avec DDEV.  
> [FAIT] La configuration actuelle vise explicitement une base locale WordPress consultable par navigateur et par outils de QA automatisée.

---

## Outillage QA actuellement en place

| Outil / chemin | Rôle | Statut |
|----------------|------|--------|
| `adp-app/package.json` | Déclare les dépendances et scripts QA | [FAIT] |
| `@playwright/test` | Exécution des tests E2E navigateur | [FAIT — voir `adp-app/package.json`] |
| `axe-playwright` | Base pour contrôles d'accessibilité automatisés | [FAIT — voir `adp-app/package.json`] |
| `adp-app/playwright.config.ts` | Configuration Playwright locale | [FAIT] |
| `adp-app/bin/screenshot.js` | Capture PNG desktop / tablet / mobile | [FAIT] |
| `adp-app/tests/screenshots/` | Dossier de sortie des captures | [FAIT — voir `adp-app/playwright.config.ts`, `adp-app/bin/screenshot.js`] |
| `adp-app/tests/results/` | Sortie des résultats Playwright | [FAIT — voir `adp-app/playwright.config.ts`] |
| `adp-app/tests/report/` | Rapport HTML Playwright | [FAIT — voir `adp-app/playwright.config.ts`] |

### Scripts disponibles

| Script | Commande | Rôle | Statut |
|--------|----------|------|--------|
| `test` | `playwright test` | Lance les tests E2E | [FAIT — voir `adp-app/package.json`] |
| `test:e2e` | `playwright test` | Alias E2E | [FAIT — voir `adp-app/package.json`] |
| `test:e2e:headed` | `playwright test --headed` | Exécution non headless | [FAIT — voir `adp-app/package.json`] |
| `screenshot` | `node bin/screenshot.js` | Capture par défaut desktop + mobile | [FAIT — voir `adp-app/package.json`, `adp-app/bin/screenshot.js`] |
| `screenshot:desktop` | `node bin/screenshot.js --desktop` | Capture desktop | [FAIT — voir `adp-app/package.json`] |
| `screenshot:mobile` | `node bin/screenshot.js --mobile` | Capture mobile | [FAIT — voir `adp-app/package.json`] |
| `screenshot:all` | `node bin/screenshot.js --all` | Capture desktop + tablet + mobile | [FAIT — voir `adp-app/package.json`] |

### Couverture de navigation configurée

| Cible | Détail | Statut |
|-------|--------|--------|
| Desktop | Chrome desktop, viewport `1440x900` | [FAIT — voir `adp-app/playwright.config.ts`, `adp-app/bin/screenshot.js`] |
| Mobile | Profil `iPhone 12` + viewport mobile dédié dans le script | [FAIT — voir `adp-app/playwright.config.ts`, `adp-app/bin/screenshot.js`] |
| Tablet | Profil `iPad (gen 7)` dans Playwright | [FAIT — voir `adp-app/playwright.config.ts`] |
| Trace | `on-first-retry` | [FAIT — voir `adp-app/playwright.config.ts`] |

> [RECOMMANDÉ] Conserver cet outillage comme socle minimal de recette visuelle locale avant toute implémentation Divi plus avancée.

---

## Hébergement (I-01 validé)

| Élément | Valeur | Statut |
|--------|--------|--------|
| Hébergeur retenu | OVHcloud | [FAIT — validation client 2026-04-24] |
| Offre retenue | `Hébergement Pro` | [FAIT — validation client 2026-04-24] |
| URL de référence offre | `https://www.ovhcloud.com/fr/web-hosting/professional-offer/` | [FAIT — fournie par le chef de projet] |
| Type d'hébergement | Mutualisé / web hosting managé | [FAIT] |

> [FAIT] Le client conserve son service actuel `Hébergement Pro` chez OVHcloud.  
> [CONSÉQUENCE] L'architecture V1 ne doit pas supposer un VPS ni une plateforme WordPress managée tierce.  
> [CONSÉQUENCE] La performance, le cache, les sauvegardes et les plugins doivent rester compatibles avec un hébergement mutualisé OVH.

### Impacts techniques

| Point | Décision de travail | Statut |
|------|----------------------|--------|
| Stack serveur | Rester compatible hébergement mutualisé OVH | [FAIT] |
| Préprod | VPS OVH — `ssh vps-adp` — chemin : `/homez.31/astucesdib/www/dev/web` | [FAIT — confirmé 2026-04-24] |
| Cache / perf | Choisir des solutions WordPress compatibles mutualisé | [DÉPENDANCE] |
| Exploitation | Éviter les besoins d'administration système | [FAIT] |

---

## Plugins WordPress prévus

Le socle V1 doit rester **minimal** et compatible avec un mutualisé OVH.  
Aucun plugin ne doit être ajouté sans validation dans ce document ou dans un ADR.

### Socle V1 recommandé

| Plugin | Rôle | Statut |
|--------|------|--------|
| Divi | Thème / builder principal | [FAIT — décision ferme] |
| All in One SEO | SEO on-page + sitemap | [FAIT — continuité avec le legacy] |
| UpdraftPlus | Sauvegardes | [FAIT — continuité avec le legacy] |
| Redirection | Gestion des redirections 301 | [FAIT — critique pour migration] |
| WPForms Lite | Formulaire de contact | [FAIT] |
| Imagify | Optimisation média | [FAIT] |
| Complianz | Bannière / consentement | [FAIT — remplace l'héritage legacy] |

### Plugins explicitement non retenus par défaut en V1

| Plugin / famille | Position projet | Motif |
|------------------|-----------------|-------|
| Rank Math | non retenu par défaut | doublon inutile avec AIOSEO si on garde la continuité legacy |
| WP Rocket | non retenu par défaut | potentiellement pertinent plus tard, mais pas à imposer avant mesures sur la V1 |
| W3 Total Cache | non retenu par défaut | configuration plus lourde et risque de complexité sur mutualisé |
| Wordfence / iThemes Security | non retenus par défaut | coût perf / complexité non justifiés à ce stade |

> **Règle V1** : commencer avec le minimum viable. Ajouter un plugin seulement s'il couvre un besoin réel non couvert par WordPress, Divi ou l'hébergement.

> **Pour les agents** : Ne pas ajouter de plugins à cette liste sans validation. Ne pas supposer qu'un plugin est installé s'il n'est pas marqué [FAIT].

> [FAIT] Information fournie par le chef de projet le 2026-04-24 : l'instance legacy contient une licence Divi existante qui devra être reprise dans `adp-app`.  
> [DÉPENDANCE] L'activation de Divi dans le nouveau site doit réutiliser cette licence au lieu d'introduire une nouvelle licence non tracée.

## Reprise de licence Divi

La licence Divi existante du legacy doit être **réutilisée** dans `adp-app` sans exposer ni versionner les secrets associés.

### Procédure projet retenue

| Étape | Action | Règle |
|------|--------|-------|
| 1 | vérifier que le legacy dispose bien d'une licence Divi active | contrôle humain ou WP admin, sans copier le secret dans Git |
| 2 | récupérer les identifiants de licence via le canal habituel du projet | stockage hors Git, hors exports publics |
| 3 | activer Divi dans `adp-app` avec cette licence | pas de nouvelle licence ad hoc |
| 4 | tester mises à jour et accès aux ressources Elegant Themes | vérification en local ou préprod |
| 5 | documenter uniquement le fait de l'activation et la date | jamais la clé ou les identifiants eux-mêmes |

### Règles de sécurité

- ne pas stocker la clé Divi dans `adp-docs/`, `adp-app/`, un export JSON versionné ou un commentaire GitHub
- ne pas capturer de secret Divi dans un transcript d'agent si une simple vérification suffit
- si une valeur de licence doit être saisie, elle l'est manuellement dans l'environnement concerné
- toute reprise de licence doit être testée d'abord en local ou préprod, jamais directement en production

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
| Redirections 301 legacy | [CRITIQUE] | domaine conservé, dépend du mapping legacy uniquement |
| Schema.org | [HYPOTHÈSE] | À évaluer selon types de contenu |

---

## Domaine public

| Élément | Valeur | Statut |
|--------|--------|--------|
| Domaine canonique | `https://astucesdepomme.com` | [FAIT — validation client 2026-04-24] |
| Variante `www` | redirigée vers l'apex | [FAIT — observé en prod] |
| Variante `http` | redirigée vers `https` | [FAIT — observé en prod] |

> [FAIT] La refonte conserve le domaine actuel `astucesdepomme.com`.  
> [CONSÉQUENCE] La stratégie de migration porte sur les URLs internes et les redirections `301`, pas sur un changement de domaine.

---

## Ce que ce document ne contient pas

- L'arborescence des pages (voir `04-architecture/01-arborescence-site.md`)
- Les types de contenus WP (voir `04-architecture/02-types-contenus.md`)
- Les composants Divi (voir `04-architecture/03-composants-divi.md`)
- Les specs de pages individuelles (voir `05-specs/pages/`)
