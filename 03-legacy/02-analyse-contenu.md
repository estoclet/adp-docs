# Analyse éditoriale du contenu legacy

**Statut** : Terminé — à valider par Eric STOCLET  
**Dernière mise à jour** : 2026-04-24  
**Produit par** : Agent IA — analyse éditoriale initiale  
**Lié à** : `01-inventaire-legacy.md`, `03-mapping-migration.md`, `TP-001-analyse-legacy.md`

> **Note agent** : Ce document est à compléter uniquement sur la base d'une analyse réelle du contenu de `adp-legacy/`. Ne pas supposer la qualité ou le volume du contenu. Utiliser les catégories de qualification définies dans `01-cadrage/04-strategie-migration.md`.

---

## Méthode de qualification

Chaque article ou page legacy est qualifié selon :

| Critère | Éléments à évaluer |
|---------|-------------------|
| Pertinence thématique | Le sujet est-il dans le périmètre du nouveau site ? |
| Fraîcheur | Le contenu est-il encore à jour ? (Apple change vite) |
| Qualité rédactionnelle | Bien écrit ? Compréhensible ? |
| Valeur SEO | L'article a-t-il du trafic ou des backlinks ? |
| Unicité | Est-ce que ce contenu existe déjà ailleurs sur le site ? |

Catégories de décision : **Garder / Réécrire / Archiver / Supprimer**  
(définitions dans `01-cadrage/04-strategie-migration.md`)

---

## Synthèse par catégorie de contenu

> À compléter après analyse.

### Astuces iPhone / iOS
- Nombre d'articles : 0
- Qualité générale : [SANS OBJET — aucun article publié]
- Articles à garder : 0
- Articles à réécrire : 0
- Articles à archiver/supprimer : 0
- Observations : aucun corpus éditorial iPhone/iOS publié n'a été relevé ; seule la homepage contient un bloc très exposé sur les versions Apple actuelles.

### Astuces Mac / macOS
- Nombre d'articles : 0
- Qualité générale : [SANS OBJET — aucun article publié]
- Observations : pas d'articles Mac/macOS publiés ; le site se présente comme une offre de service autour de l'écosystème Apple.

### Astuces iPad
- Nombre d'articles : 0
- Qualité générale : [SANS OBJET — aucun article publié]
- Observations : aucun contenu éditorial iPad autonome publié.

### Démarches administratives en ligne
- Nombre d'articles : 0
- Qualité générale : [SANS OBJET — aucun article publié]
- Observations : le sujet apparaît comme une ligne de service dans la homepage, pas comme un corpus de contenus dédié.

### Autres catégories identifiées
- **Page commerciale principale** : `Accueil` concentre la quasi-totalité du message métier, des offres, du périmètre d'intervention, des tarifs SAP, du contact et d'un bloc d'actualité sur les versions Apple.
- **Pages de conformité** : `Mentions legales`, `CGV`, `Confidentialité`, `Information Fiscale`.
- **Aucun blog actif** : 0 article publié, donc pas de vraie matière éditoriale de type "astuces" à migrer telle quelle.

---

## Contenus à fort potentiel

> Le legacy ne contient pas d'articles publiés. Les contenus prioritaires sont donc des pages statiques.

| URL legacy | Titre | Catégorie | Raison de priorisation | Décision |
|-----------|-------|-----------|----------------------|----------|
| / | Accueil | Page commerciale / conversion | Porte la proposition de valeur, les services, le contact, le positionnement Apple et les éléments SAP | Réécrire |
| /infos-fiscales | Information Fiscale | Conformité / réassurance | Sert d'appui au discours SAP et au crédit d'impôt | Réécrire |
| /cgv | CGV | Conformité contractuelle | Nécessaire juridiquement si le site conserve une logique de vente/prestation | Réécrire |
| /mentions-legales | Mentions legales | Conformité légale | Nécessaire juridiquement | Réécrire |
| /confidentialite | Confidentialité | Conformité RGPD | Nécessaire juridiquement, mais contenu générique à revoir | Réécrire |

---

## Contenu dupliqué ou redondant identifié

> Lister les articles qui traitent du même sujet avec des approches similaires.

| URL 1 | URL 2 | Sujet commun | Recommandation |
|-------|-------|-------------|----------------|
| / | /infos-fiscales | Crédit d'impôt SAP / cadre fiscal | Regrouper la promesse marketing sur la homepage et conserver le détail réglementaire sur la page fiscale |
| / | /cgv | Tarifs, modalités de règlement, cadre d'intervention | Éviter la répétition commerciale ; garder le détail contractuel dans les CGV |
| /mentions-legales | /confidentialite | Données personnelles, cookies, responsabilités | Réécrire avec une séparation plus nette entre mentions, confidentialité et consentement cookies |

---

## Contenu obsolète à fort risque

> Contenu potentiellement incorrect sur des versions Apple dépassées.

| URL | Titre | Version Apple concernée | Recommandation |
|-----|-------|------------------------|----------------|
| / | Accueil — bloc "Le point sur les versions actuelles" | Versions Apple indiquées dans le bloc d'actualité de la homepage | Supprimer ou externaliser dans un contenu maintenu régulièrement |
| /cgv | CGV Edition 10/02/2022 | Référence datée aux CGV et cadre opérationnel antérieur | Réécrire avant reprise |
| /confidentialite | Politique de confidentialité | Mentions génériques et formulations juridiques potentiellement datées ou inadaptées | Réécrire avant reprise |

---

## Observations éditoriales générales

- Ton général : commercial, rassurant, orienté service de proximité et accompagnement à domicile.
- Niveau de difficulté dominant : grand public ; faible technicité rédactionnelle malgré un positionnement Apple.
- Formats existants (texte seul, tutoriel avec images, vidéo…) : pages Divi mêlant textes marketing, blocs réglementaires, visuels, captures et liens externes ; aucune vidéo ni article tutoriel publié.
- Qualité des illustrations / captures d'écran : hétérogène ; mélange d'images de fond, logos, cartes, captures anciennes et visuels plus récents.
- Présence de liens internes : faible ; principalement vers les pages légales et fiscales.
- Cohérence des call-to-action : concentrée sur la prise de contact directe (téléphone / email), sans tunnel éditorial ni maillage de contenus.

---

## Signalement agent

- **Tâche accomplie** : analyse réelle des 5 pages publiées du legacy ; qualification du site comme vitrine de service avec pages légales plutôt que comme site éditorial d'astuces.
- **Hypothèses posées** : aucune hypothèse de trafic ou de performance SEO ; seules les structures et contenus observables ont été retenus.
- **Inconnues rencontrées** : absence de données de trafic, de backlinks et d'historique éditorial ; impossible de prioriser par audience réelle à ce stade.
- **Points à arbitrer** : décider si le bloc "versions Apple actuelles" a vocation à exister dans le futur site ; décider si `infos-fiscales` reste une page autonome ou devient une section de réassurance.
- **Prochaine étape recommandée** : lancer l'audit SEO/performance (`#2`), puis préparer le mapping des seules pages réellement utiles à reprendre.
