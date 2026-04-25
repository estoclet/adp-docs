# Conventions de rédaction pour agents

**Statut** : Actif — s'applique à tous les documents produits par des agents  
**Dernière mise à jour** : 2026-04-25 — renforcé par boucle gouvernance itérations 1, 3, 4, 8 et 10 (champ Signalement étendu)  
**Lié à** : `01-regles-ia.md`, `03-perimetre-agents.md`

---

## Les marqueurs obligatoires

Chaque affirmation dans un document produit ou modifié par un agent doit être qualifiée.  
Ces marqueurs sont des **signaux de confiance épistémique**, pas des décorations.

| Marqueur | Quand l'utiliser | Exemple |
|----------|-----------------|---------|
| `[FAIT]` | Information vérifiée, issue d'une source explicite (brief client, fichier de référence, analyse réelle) | "[FAIT] Stack : WordPress + Divi — voir ADR-001" |
| `[HYPOTHÈSE]` | Supposition raisonnée non confirmée, à valider | "[HYPOTHÈSE] La cible principale est des utilisateurs de 45 ans et plus" |
| `[À ARBITRER]` | Point de décision qui requiert un choix humain | "[À ARBITRER] Faut-il un Custom Post Type pour les démarches administratives ?" |
| `[DÉPENDANCE]` | Ce point est bloqué par un autre fichier, une décision ou une inconnue | "[DÉPENDANCE] Dépend de I-03 (stratégie domaine)" |
| `[INCONNUE]` | Information manquante dont l'absence est connue | "[INCONNUE] Volume de trafic actuel non communiqué" |
| `[INCONNUE BLOQUANTE]` | Inconnue qui empêche de compléter la tâche en cours | "[INCONNUE BLOQUANTE] Sans accès à la BDD legacy (I-06), l'inventaire des articles est impossible" |
| `[RÉSOLU]` | Inconnue (I-XX) levée — valeur et source traçable citées dans le même document | "[RÉSOLU — I-06 — dump prod importé 2026-04-24]" |
| `[RÉSOLU PARTIEL]` | Inconnue partiellement levée : une portion est confirmée, le reste est à compléter — citer ce qui est connu et ce qui manque | "[RÉSOLU PARTIEL — I-07 — bleu marine #1e3264 extrait du logo ; tons complémentaires à confirmer]" |
| `[OBSOLÈTE]` | Information qui ne fait plus autorité — ne pas utiliser | "[OBSOLÈTE] Cette décision a été remplacée par ADR-003" |
| `[RECOMMANDÉ]` | Suggestion de l'agent, non décidée | "[RECOMMANDÉ] Utiliser Rank Math plutôt que Yoast pour sa légèreté" |
| `[SANS OBJET]` | Métrique ou champ non applicable dans ce contexte (ex. qualité de contenu quand le volume est 0) | "[SANS OBJET — aucun article publié]" |

---

## Règles d'usage des marqueurs

### Placement
- Placer le marqueur **en début de phrase ou de cellule de tableau** pour qu'il soit immédiatement visible.
- Ne pas noyer le marqueur en milieu de paragraphe.
- Dans les tableaux, la colonne "Statut" porte le marqueur.

### Combinaison
Un fait peut avoir une dépendance : `[FAIT — DÉPENDANCE]` est acceptable.  
Un fait ne peut pas être une hypothèse simultanément : choisir le marqueur le plus restrictif.

### Marqueurs d'annotation (non épistémiques)

Ces marqueurs ne qualifient pas le niveau de confiance — ils annotent le type de contenu. Ils sont autorisés en blockquote (`>`) uniquement.

| Marqueur | Usage |
|----------|-------|
| `[CONSÉQUENCE]` | Conséquence directe d'une décision déjà actée |
| `[RÈGLE]` | Règle opérationnelle du projet (en complément des règles de `02-gouvernance-ia/`) |

> **Note** : `[À VALIDER]` peut apparaître dans le champ `**Statut**` des en-têtes de document et dans les tables de suivi comme indicateur de validation humaine en attente. Ce n'est pas un marqueur épistémique — ne pas l'utiliser dans des cellules portant sur la confiance d'une information.

### Marqueurs non officiels — interdit
Un agent n'invente pas de nouveaux marqueurs. Seuls les marqueurs listés dans ce tableau et les marqueurs d'annotation ci-dessus sont autorisés.

**Interdit** : `[VALIDÉ]`, `[PROPOSITION]`, `[À VÉRIFIER]`, `[À CONFIRMER]`, `[RÉSOLU OPÉRATIONNELLEMENT]`, ou tout autre marqueur absent de ce tableau.  
**Si aucun marqueur officiel ne convient** : utiliser `[À ARBITRER]` et expliquer pourquoi dans le bloc Signalement.

### Marqueurs interdits pour les agents
Les agents ne marquent jamais quelque chose `[FAIT]` sans pouvoir citer la source dans le même document ou en référence à un fichier existant dans `adp-docs/`.

### Promotion et rétrogradation des marqueurs
Un agent ne peut pas **promouvoir** un marqueur (`[HYPOTHÈSE]` → `[FAIT]`) sans ajouter simultanément la source traçable dans le document (pas seulement dans le Signalement). Voir R-28 pour les conditions complètes :

- La promotion est réservée aux **faits techniques ou observables** (existence d'une page, état d'un plugin, valeur d'un réglage) — mesure directe conforme à R-01.
- Les hypothèses éditoriales, stratégiques ou clients ne peuvent être promues en `[FAIT]` que par le chef de projet.

Un agent peut **rétrograder** un marqueur (`[FAIT]` → `[OBSOLÈTE]`) uniquement si la décision de révision est enregistrée dans `07-pilotage/02-journal-decisions.md`.  
Toute promotion ou rétrogradation doit être signalée dans le champ "Marqueurs promus" du bloc "Signalement agent" avec la justification.

**Cycle de vie de `[RÉSOLU PARTIEL]`** : ce marqueur est une étape intermédiaire entre `[INCONNUE]` et `[RÉSOLU]`. Un agent peut promouvoir `[INCONNUE]` → `[RÉSOLU PARTIEL]` si une portion est confirmée avec source, en citant explicitement ce qui reste à confirmer. La promotion `[RÉSOLU PARTIEL]` → `[RÉSOLU]` suit les mêmes règles que `[HYPOTHÈSE]` → `[FAIT]` : source traçable obligatoire pour la portion manquante.

### Résolution des inconnues (I-XX)

Quand une inconnue identifiée par un identifiant `I-XX` est résolue :

1. Dans `00-initialisation-projet.md` : remplacer `[À ARBITRER]` ou `[INCONNUE]` par `[RÉSOLU — voir décision N]` ou `[RÉSOLU — confirmé le DATE]`. Ne pas supprimer la ligne (traçabilité).
2. Dans les documents qui citaient l'inconnue : remplacer `[DÉPENDANCE] Dépend de I-XX` par `[FAIT — I-XX résolu : valeur]` avec la source.
3. Signaler la résolution dans le bloc "Signalement agent" : "I-XX résolu : valeur = X, source = Y."
4. Ne pas réutiliser un identifiant I-XX pour une nouvelle inconnue — les identifiants sont uniques et permanents.

---

## Règles de formulation

### Formulations à éviter

| Formulation interdite | Problème | Alternative |
|----------------------|----------|-------------|
| "Il est évident que…" | Postule une évidence non vérifiée | Supprimer ou sourcer |
| "Généralement, les sites comme celui-ci…" | Généralisation non sourcée | "[HYPOTHÈSE] Sur des sites similaires…" |
| "Le client souhaite probablement…" | Invention de besoin | "[À ARBITRER] Faut-il…" |
| "Nous pourrions envisager…" | Formulation floue | "Je recommande X pour Y raison. [RECOMMANDÉ]" |
| "Il faudrait sans doute…" | Vague, non actionnable | "[HYPOTHÈSE] X semble pertinent si Y est confirmé" |
| "Comme convenu…" | Supposer un accord non documenté | Citer le document ou le journal de décision |
| "Le site actuel est…" | Affirmation sur legacy non vérifiée | "[HYPOTHÈSE — à vérifier via analyse legacy]" |
| "D'après mes connaissances…" | Source externe non valide dans ce repo | "[HYPOTHÈSE] …" + citer I-XX si pertinent |
| "Typiquement pour un site WordPress…" | Généralisation hors repo | "[HYPOTHÈSE] Sur des projets similaires…" |
| "On peut supposer que…" | Supposition non assumée | "[HYPOTHÈSE] …" explicite |
| "Il est probable que…" | Probabilité non sourcée | "[HYPOTHÈSE] …" avec condition de vérification |
| "Ce type de client…" | Stéréotype non sourcé | "[HYPOTHÈSE] …" ou `[INCONNUE]` si non documenté |
| "Comme dit précédemment…" | Référence vague sans pointeur | Citer le fichier ou la section exacte |

### Formulations recommandées

- Préférer les tournures actives et directes.
- Préférer les tableaux aux listes à puces pour les informations structurées.
- Nommer les fichiers de référence explicitement (`voir 00-initialisation-projet.md`).
- Citer les inconnues par leur identifiant (`I-01`, `I-02`…).

---

## Découpage des documents trop longs

Si un document en cours de rédaction dépasse **250 lignes** ou traite de **plus d'un sujet distinct**, l'agent doit :

1. Compléter le document actuel jusqu'à un point logique
2. Signaler dans son output : "Ce document couvre maintenant X. Le sujet Y devrait faire l'objet d'un fichier séparé : `[nom-proposé].md`."
3. Ne pas créer le fichier séparé sans validation humaine

---

## En-tête obligatoire pour tout document agent

Tout fichier créé ou modifié significativement par un agent doit comporter cet en-tête :

```markdown
# [Titre du document]

**Statut** : [Brouillon / En cours / À valider / Validé / Obsolète]  
**Dernière mise à jour** : [DATE]  
**Produit par** : [Nom de l'agent ou "Agent IA — task pack TP-XXX"]  
**Lié à** : [Références aux documents connexes]
```

---

## Signalement en fin de document

Tout document produit par un agent pour une tâche bornée doit se terminer par un bloc de signalement :

```markdown
---
## Signalement agent

- **Tâche accomplie** : [Ce qui a été fait]
- **Hypothèses posées** : [Liste — ou "aucune"]
- **Inconnues rencontrées** : [Liste avec identifiants — ou "aucune"]
- **Marqueurs promus** : [Toute promotion [HYPOTHÈSE]→[FAIT] avec source citée (R-28) — ou "aucune"]
- **Points à arbitrer** : [Liste — ou "aucun"]
- **Prochaine étape recommandée** : [Suggestion]
```

Ce bloc permet au chef de projet de valider avant de passer à la suite.

---

## Ce que ce document ne contient pas

- Les règles de périmètre (voir `01-regles-ia.md`)
- Le périmètre des agents (voir `03-perimetre-agents.md`)
