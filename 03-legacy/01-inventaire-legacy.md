# Inventaire du site legacy — astucesdepomme.com

**Statut** : En cours — complété partiellement via TP-001  
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
| Images / médias | 63 pièces jointes ; répertoire uploads `232M` ; 10 dossiers de premier niveau (`2021` à `2026`, `complianz`, `et-fonts`, `et_temp`, `wpforms`) | `ddev wp post list --post_type=attachment --format=count` + `du -sh wp-content/uploads` + `find wp-content/uploads` | [FAIT] |
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
| CSS personnalisé | [INCONNUE] | [INCONNUE — non mesuré à ce stade] |

### Thèmes présents sur disque

| Thème | Statut | Version | Source |
|------|--------|---------|--------|
| Divi | Actif | 4.27.6 | `ddev wp theme list` |
| twentytwentyfive | Inactif | 1.4 | `ddev wp theme list` |
| twentytwentyfour | Inactif | 1.4 | `ddev wp theme list` |

---

## Performances actuelles (à mesurer)

> Mesurer idéalement via PageSpeed Insights ou Lighthouse. En attendant, quelques signaux de base ont été relevés directement sur la prod.

| Métrique | Valeur | Outil | Date |
|----------|--------|-------|------|
| PageSpeed mobile | [INCONNUE] | PageSpeed Insights non lancé à ce stade | 2026-04-24 |
| PageSpeed desktop | [INCONNUE] | PageSpeed Insights non lancé à ce stade | 2026-04-24 |
| LCP | [INCONNUE] | Lighthouse / PSI non lancé à ce stade | 2026-04-24 |
| CLS | [INCONNUE] | Lighthouse / PSI non lancé à ce stade | 2026-04-24 |
| Time to first byte approximatif | `1.23s` | `curl -w time_starttransfer` sur `https://astucesdepomme.com/` | 2026-04-24 |
| Temps de réponse total approximatif | `1.32s` | `curl -w time_total` sur `https://astucesdepomme.com/` | 2026-04-24 |
| Taille HTML téléchargée | `220468` octets | `curl -w size_download` sur `https://astucesdepomme.com/` | 2026-04-24 |

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

- **Tâche accomplie** : activation locale du legacy sous DDEV, import du dump prod, vérification du thème actif, des plugins/thèmes installés, des pages publiées, des volumes de contenu, de la front page et de la structure front observable.
- **Hypothèses posées** : aucune hypothèse structurante ajoutée ; seules des valeurs vérifiées ont été renseignées.
- **Inconnues rencontrées** : date de création du site, présence éventuelle d'un thème enfant, volume exact par type de média, structure précise du header si une partie est injectée par Divi Theme Builder plutôt que par un menu WordPress classique.
- **Points à arbitrer** : aucun arbitrage immédiat issu de cette étape technique ; la suite dépend surtout de l'analyse du legacy front et éditorial.
- **Prochaine étape recommandée** : considérer TP-001 comme quasi complété, puis enchaîner avec l'analyse éditoriale (`#1`) et l'audit SEO/performance (`#2`) du legacy.
