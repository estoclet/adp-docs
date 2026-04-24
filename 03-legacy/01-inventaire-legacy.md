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
- [INCONNUE] Aucun menu WordPress listé via `ddev wp menu list`

### Menu secondaire / footer
- [INCONNUE] Aucun menu WordPress listé via `ddev wp menu list`

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
| Images / médias | 63 pièces jointes ; répertoire uploads `232M` ; 10 dossiers de premier niveau | `ddev wp post list --post_type=attachment --format=count` + `du -sh wp-content/uploads` + `find wp-content/uploads` | [FAIT] |
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

---

## Thème actif et dépendances (à compléter)

| Attribut | Valeur | Statut |
|----------|--------|--------|
| Thème parent | Divi | [FAIT] |
| Thème enfant | [INCONNUE] | [INCONNUE — non observé via `template`/`stylesheet`] |
| Page builder actuel | Divi | [FAIT] |
| CSS personnalisé | [INCONNUE] | [INCONNUE — non mesuré à ce stade] |

---

## Performances actuelles (à mesurer)

> Mesurer via PageSpeed Insights, GTmetrix ou similaire sur la page d'accueil.

| Métrique | Valeur | Outil | Date |
|----------|--------|-------|------|
| PageSpeed mobile | [INCONNUE] | | |
| PageSpeed desktop | [INCONNUE] | | |
| LCP | [INCONNUE] | | |
| CLS | [INCONNUE] | | |

---

## SEO — État initial (à analyser)

| Point | État | Outil | Statut |
|-------|------|-------|--------|
| Sitemap XML | [À VÉRIFIER] | | |
| robots.txt | [À VÉRIFIER] | | |
| Balises title / meta description | [À VÉRIFIER] | | |
| Structure H1/H2/H3 | [À VÉRIFIER] | | |
| Liens brisés | [À VÉRIFIER] | | |
| Nombre de backlinks externes | [INCONNUE] | | |

---

## Observations générales (à compléter par l'agent)

> Compléter après analyse. Faits observés uniquement. Pas de recommandations ici.

- [FAIT] Le legacy est maintenant activable localement sous DDEV sur `http://adp-legacy.ddev.site`.
- [FAIT] La copie locale repose sur un dump de la base de prod importé le 2026-04-24.
- [FAIT] Le site legacy actif observé dans la base locale semble très léger en contenu éditorial : 0 article publié, 5 pages publiées, 63 médias.
- [FAIT] La navigation WordPress n'expose aucun menu enregistré via `wp menu list`, ce qui suggère soit une navigation gérée autrement, soit une configuration minimaliste du site.

---

## Signalement agent

- **Tâche accomplie** : activation locale du legacy sous DDEV, import du dump prod, vérification du thème actif, des plugins actifs, des pages publiées, des volumes de contenu et des métriques structurelles simples.
- **Hypothèses posées** : aucune hypothèse structurante ajoutée ; seules des valeurs vérifiées ont été renseignées.
- **Inconnues rencontrées** : date de création du site, présence éventuelle d'un thème enfant, volume exact par type de média, structure de navigation rendue côté front si non pilotée par les menus WordPress.
- **Points à arbitrer** : aucun arbitrage immédiat issu de cette étape technique ; la suite dépend surtout de l'analyse du legacy front et éditorial.
- **Prochaine étape recommandée** : poursuivre TP-001 côté navigation/front réel, puis enchaîner avec l'analyse éditoriale et SEO du legacy.
