# Conventions de rédaction pour agents

**Statut** : Actif — s'applique à tous les documents produits par des agents  
**Dernière mise à jour** : 2026-04-24 — renforcé par boucle gouvernance itération 1  
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
| `[OBSOLÈTE]` | Information qui ne fait plus autorité — ne pas utiliser | "[OBSOLÈTE] Cette décision a été remplacée par ADR-003" |
| `[RECOMMANDÉ]` | Suggestion de l'agent, non décidée | "[RECOMMANDÉ] Utiliser Rank Math plutôt que Yoast pour sa légèreté" |

---

## Règles d'usage des marqueurs

### Placement
- Placer le marqueur **en début de phrase ou de cellule de tableau** pour qu'il soit immédiatement visible.
- Ne pas noyer le marqueur en milieu de paragraphe.
- Dans les tableaux, la colonne "Statut" porte le marqueur.

### Combinaison
Un fait peut avoir une dépendance : `[FAIT — DÉPENDANCE]` est acceptable.  
Un fait ne peut pas être une hypothèse simultanément : choisir le marqueur le plus restrictif.

### Marqueurs interdits pour les agents
Les agents ne marquent jamais quelque chose `[FAIT]` sans pouvoir citer la source dans le même document ou en référence à un fichier existant dans `adp-docs/`.

### Promotion et rétrogradation des marqueurs
Un agent ne peut pas **promouvoir** un marqueur (`[HYPOTHÈSE]` → `[FAIT]`) sans ajouter simultanément la source traçable.  
Un agent peut **rétrograder** un marqueur (`[FAIT]` → `[OBSOLÈTE]`) uniquement si la décision de révision est enregistrée dans `07-pilotage/02-journal-decisions.md`.  
Toute promotion ou rétrogradation doit être signalée dans le bloc "Signalement agent" avec la justification.

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
| "Le site actuel est…" | Affirmation sur legacy non vérifiée | "[À VÉRIFIER — analyse legacy]" |
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
- **Hypothèses posées** : [Liste]
- **Inconnues rencontrées** : [Liste avec identifiants]
- **Points à arbitrer** : [Liste]
- **Prochaine étape recommandée** : [Suggestion]
```

Ce bloc permet au chef de projet de valider avant de passer à la suite.

---

## Ce que ce document ne contient pas

- Les règles de périmètre (voir `01-regles-ia.md`)
- Le périmètre des agents (voir `03-perimetre-agents.md`)
