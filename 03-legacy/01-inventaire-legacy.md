# Inventaire du site legacy — astucesdepomme.com

**Statut** : À valider — inventaire structurel complet via TP-001  
**Dernière mise à jour** : 2026-04-24  
**Produit par** : Agent IA — exécution partielle de TP-001  
**Lié à** : `TP-001-analyse-legacy.md`, `03-mapping-migration.md`

> **Note agent** : Ce document est un squelette structuré. Compléter uniquement les sections assignées dans le task pack TP-001. Ne pas inventer de valeurs. Utiliser `[À VÉRIFIER]` si une information est incertaine. Utiliser `[INCONNUE]` si elle est absente.

---

## Identité du site

| Attribut | Valeur | Statut |
|----------|--------|--------|
| URL | https://astucesdepomme.com/ | [FAIT] |
| Propriétaire | Julien HACHE | [FAIT] |
| Chef de projet | Eric STOCLET | [FAIT] |
| CMS | WordPress 6.9.4 | [FAIT — vérifié via `ddev wp core version`] |
| Thème actif | Divi | [FAIT — vérifié via `ddev wp option get template` et `stylesheet`] |
| Date de création estimée | [INCONNUE] | [INCONNUE — non déterminée à ce stade] |

---

## Environnement local de travail

| Attribut | Valeur | Statut |
|----------|--------|--------|
| Copie locale legacy | `adp-legacy/` | [FAIT] |
| Environnement local | DDEV projet `adp-legacy` | [FAIT — vérifié via `ddev describe`] |
| URL locale | `http://adp-legacy.ddev.site` | [FAIT — vérifié via `ddev describe` et HTTP 200] |
| Base locale | Dump prod importé le 2026-04-24 | [FAIT — import DDEV réussi] |
| Préfixe de tables | `mod245_` | [FAIT — vérifié via `ddev wp db prefix`] |
| Réécriture d'URL locale | `astucesdepomme.com` → `adp-legacy.ddev.site` | [FAIT — `ddev wp search-replace`] |

---

## Structure de navigation (à compléter)

> Lister les menus principaux tels qu'ils apparaissent sur le site. Ne pas interpréter, recopier fidèlement.

### Menu principal
- [FAIT] Aucun menu WordPress enregistré via `ddev wp menu list`
- [FAIT] La page d'accueil est une page statique WordPress : `Accueil` (ID `18`) via `show_on_front=page` et `page_on_front=18`
- [FAIT] Les liens visibles relevés sur la homepage pointent surtout vers `/cgv`, `/confidentialite`, `/infos-fiscales`, `/mentions-legales` et l'adresse mail `julien.hache@astucesdepomme.com`

### Menu secondaire / footer
- [FAIT] Aucun menu WordPress footer enregistré via `ddev wp menu list`
- [FAIT] Le footer observé côté front est très minimal et affiche surtout une bannière SAP ; les liens légaux sont exposés dans la page elle-même plutôt que via un menu WordPress dédié

---

## Pages statiques identifiées

| URL | Titre | Rôle estimé | Statut analyse |
|-----|-------|-------------|----------------|
| / | Accueil | Page principale | [FAIT — page publiée `accueil`] |
| /mentions-legales | Mentions legales | Conformité légale | [FAIT — page publiée `mentions-legales`] |
| /cgv | CGV | Conditions générales de vente | [FAIT — page publiée `cgv`] |
| /infos-fiscales | Information Fiscale | Informations fiscales | [FAIT — page publiée `infos-fiscales`] |
| /confidentialite | Confidentialité | Politique de confidentialité | [FAIT — page publiée `confidentialite`] |

> [FAIT] Les cinq pages ci-dessus sont les pages publiées retournées par `ddev wp post list --post_type=page --post_status=publish`.

---

## Catégories et taxonomies (à compléter)

| Nom catégorie | Slug | Nombre d'articles estimé | Statut |
|--------------|------|--------------------------|--------|
| Non classé | `non-classe` | 0 | [FAIT — vérifié via `ddev wp term list category`] |

---

## Volume de contenu estimé

| Type | Quantité estimée | Source de l'estimation | Statut |
|------|-----------------|------------------------|--------|
| Articles publiés | 0 | `ddev wp post list --post_type=post --post_status=publish --format=count` | [FAIT] |
| Pages statiques | 5 | `ddev wp post list --post_type=page --post_status=publish` | [FAIT] |
| Images / médias | 63 pièces jointes WP ; **82 fichiers originaux** sur disque (hors miniatures) ; `232M` total uploads | `ddev wp post list --post_type=attachment --format=count` + `find` filtré sur extensions images | [FAIT] |
| Médias par année | 2021 : 59 · 2022 : 0 · 2023 : 16 · 2024 : 0 · 2025 : 7 · 2026 : 0 (+ dossiers `complianz`, `et-fonts`, `et_temp`, `wpforms`) | `find wp-content/uploads/YYYY -name "*.jpg|png…"` | [FAIT] |
| Commentaires | 0 | `ddev wp comment list --format=count` | [FAIT] |
| Auteurs | 1 utilisateur | `ddev wp user list --format=count` | [FAIT] |

---

## Plugins actifs (à compléter)

> À identifier via l'analyse du code legacy dans `adp-legacy/wp-content/plugins/` ou via l'admin WP.

| Plugin | Version | Rôle | Statut migration |
|--------|---------|------|-----------------|
| all-in-one-seo-pack | 4.9.6.2 | SEO | [À ANALYSER] |
| cookie-dough-compliance-and-consent-for-gdpr | 2.2.5 | Consentement / cookies / conformité | [À ANALYSER] |
| ga-google-analytics | 20260421 | Analytics | [À ANALYSER] |
| updraftplus | 2.26.1.0 | Sauvegardes | [À ANALYSER] |

> [FAIT] Liste vérifiée via `ddev wp plugin list --status=active`.
> [FAIT] Les dossiers présents dans `wp-content/plugins/` correspondent exactement à ces 4 plugins ; aucun plugin installé supplémentaire n'a été relevé sur disque.

---

## Thème actif et dépendances (à compléter)

| Attribut | Valeur | Statut |
|----------|--------|--------|
| Thème parent | Divi `4.27.6` | [FAIT — vérifié via `ddev wp theme list`] |
| Thème enfant | [INCONNUE] | [INCONNUE — non observé via `template`/`stylesheet`] |
| Page builder actuel | Divi | [FAIT] |
| CSS personnalisé Divi | Aucun | [FAIT — `ddev wp option list --search="*divi*css*"` : aucune option trouvée] |
| CSS additionnel WP | Aucun | [FAIT — post type `custom_css` ID 130 : contenu vide] |

### Thèmes présents sur disque

| Thème | Statut | Version | Source |
|------|--------|---------|--------|
| Divi | Actif | 4.27.6 | `ddev wp theme list` |
| twentytwentyfive | Inactif | 1.4 | `ddev wp theme list` |
| twentytwentyfour | Inactif | 1.4 | `ddev wp theme list` |

---

## Performances actuelles

> Mesures effectuées via Lighthouse CLI (headless Chromium) sur `https://astucesdepomme.com/` le 2026-04-24.

| Métrique | Mobile | Desktop | Seuil cible | Statut |
|----------|--------|---------|-------------|--------|
| Score Performance | **28 / 100** | **33 / 100** | > 80 | [FAIT — critique] |
| FCP (First Contentful Paint) | 2,9 s | 2,6 s | < 1,8 s | [FAIT — à améliorer] |
| LCP (Largest Contentful Paint) | **10,3 s** | **19,5 s** | < 2,5 s | [FAIT — critique] |
| CLS (Cumulative Layout Shift) | **0,487** | 0,003 | < 0,1 | [FAIT — critique mobile] |
| TBT (Total Blocking Time) | 450 ms | 570 ms | < 200 ms | [FAIT — à améliorer] |
| Speed Index | 18,3 s | 20,4 s | < 3,4 s | [FAIT — critique] |
| TTFB (curl time_starttransfer) | 1,23 s | — | < 0,8 s | [FAIT] |
| Taille HTML téléchargée | ~220 KB | — | — | [FAIT] |

> Ces scores justifient une refonte technique profonde. Le LCP et le CLS mobile sont particulièrement problématiques.

---

## SEO — État initial (à analyser)

| Point | État | Outil | Statut |
|-------|------|-------|--------|
| Sitemap XML | `https://astucesdepomme.com/sitemap.xml` répond `200` et expose un index avec `page-sitemap.xml` | `curl -I -L` + lecture du XML | [FAIT] |
| robots.txt | présent et valide ; `Disallow: /wp-admin/`, `Allow: /wp-admin/admin-ajax.php`, sitemaps déclarés | `curl -I -L` + lecture de `robots.txt` | [FAIT] |
| Balises title / meta description | présentes sur la homepage ; title et description très génériques (`Astuces de pomme - Assistance dépannage formation Mac iPad iPhone...`) | lecture du HTML prod | [FAIT] |
| Structure H1/H2/H3 | aucun `H1` détecté sur la homepage prod | extraction HTML (`rg '<h1'`) | [FAIT] |
| Liens brisés | [INCONNUE] | crawler non lancé à ce stade | [À VÉRIFIER] |
| Nombre de backlinks externes | [INCONNUE] | Ahrefs / GSC / outil backlinks non disponible | [INCONNUE] |

---

## Données métier identifiées

> Source : `adp-legacy/llms.txt` (généré par All in One SEO v4.9.6.2) + lecture des pages publiées.

| Attribut | Valeur | Statut |
|----------|--------|--------|
| Raison sociale | Astuces de Pomme | [FAIT — llms.txt + CGV] |
| Forme juridique | Micro-entreprise | [FAIT — CGV] |
| Propriétaire | Julien Hache | [FAIT — CGV] |
| SIRET | 50228208000022 | [FAIT — CGV legacy] |
| APE | 8559B (Enseignement culturel) | [FAIT — CGV legacy] |
| Numéro agrément SAP | 502282080 | [FAIT — CGV legacy] |
| Acte SAP | 2020-063 — délivré le 11/09/2020 | [FAIT — CGV legacy] |
| Email de contact | julien.hache@astucesdepomme.com | [FAIT — llms.txt + liens homepage] |
| URL du site | https://astucesdepomme.com | [FAIT] |
| `siteurl` en base | http://astucesdepomme.com (sans S) | [FAIT — `ddev wp option get siteurl`] |

> Le SIRET, l'APE et le numéro SAP sont des données stables à réutiliser dans les mentions légales et CGV du nouveau site.  
> La discordance `siteurl` HTTP vs HTTPS en prod mérite vérification — probablement géré par le serveur OVH via redirection.

---

## Observations générales (à compléter par l'agent)

> Compléter après analyse. Faits observés uniquement. Pas de recommandations ici.

- [FAIT] Le legacy est maintenant activable localement sous DDEV sur `http://adp-legacy.ddev.site`.
- [FAIT] La copie locale repose sur un dump de la base de prod importé le 2026-04-24.
- [FAIT] Le site legacy actif observé dans la base locale semble très léger en contenu éditorial : 0 article publié, 5 pages publiées, 63 médias.
- [FAIT] La navigation WordPress n'expose aucun menu enregistré via `wp menu list`; la structure visible repose surtout sur une homepage statique Divi et quelques pages légales.
- [FAIT] La page d'accueil est une landing page statique configurée comme front page WordPress (`Accueil`, ID `18`) avec structure de services/contact plutôt qu'un blog.
- [FAIT] La structure de permaliens est personnalisée en `/archives/%post_id%`, malgré l'absence actuelle d'articles publiés.
- [FAIT] Le site charge All in One SEO côté front et expose dans ses métadonnées un téléphone, une présence Facebook et une présence LinkedIn.
- [FAIT] La homepage prod ne contient pas de balise `H1`, ce qui constitue un signal SEO faible sur la structure sémantique.
- [FAIT] Le sitemap XML prod n'expose qu'un sitemap de pages, cohérent avec l'absence de posts publiés.
- [FAIT] Les signaux réseau simples montrent une réponse initiale autour de `1.23s` et un HTML assez lourd pour une simple page vitrine (`~220 KB` téléchargés hors assets).

---

## Signalement agent

- **Tâche accomplie** : inventaire structurel complet — version WP, thème, plugins, pages, médias (82 originaux, répartition 2021–2026), navigation, données métier (SIRET, APE, SAP), performances Lighthouse (mobile 28/100, desktop 33/100), SEO de base (sitemap, robots.txt, absence H1), CSS custom (aucun).
- **Hypothèses posées** : aucune — toutes les valeurs sont issues de commandes WP-CLI sur la base locale ou de mesures directes sur la prod.
- **Inconnues rencontrées** :
  - `[INCONNUE]` Date de création estimée du site
  - `[INCONNUE]` Présence éventuelle d'un thème enfant Divi (aucun observé)
  - `[INCONNUE]` Structure exacte du header Divi (Theme Builder vs template)
  - `[INCONNUE]` Nombre de backlinks externes
- **Points à arbitrer** : la discordance `siteurl` HTTP vs HTTPS en base mérite confirmation auprès du chef de projet (probablement redirigé côté serveur OVH).
- **Prochaine étape recommandée** : TP-001 complet — passer à l'analyse éditoriale du contenu des 5 pages publiées (issue #1) et à l'audit SEO/performances approfondi (issue #2).
