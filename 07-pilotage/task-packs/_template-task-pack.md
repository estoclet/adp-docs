# TP-XXX — [Titre de la tâche]

**Statut** : [À lancer / En cours / Terminé / Bloqué]  
**Date de création** : [DATE]  
**Agent assigné** : [Claude / Codex / Humain / …]  
**Durée estimée** : [Court / Moyen / Long]  
**Lié au lot** : [Lot X]

---

## Objectif unique

> En une phrase : qu'est-ce que cet agent doit produire ou accomplir ?

**[Objectif borné et vérifiable]**

---

## Contexte minimal

> L'agent n'a pas accès à la conversation. Lui donner le contexte strict nécessaire à sa tâche — ni plus, ni moins.

- Projet : Refonte d'astucesdepomme.com (WordPress + Divi)
- Client : Julien HACHE
- Chef de projet : Eric STOCLET
- [Contexte spécifique à cette tâche]

---

## Fichiers à lire (inputs)

> L'agent ne lit que ces fichiers.

| Fichier | Pourquoi |
|---------|---------|
| `adp-docs/02-gouvernance-ia/01-regles-ia.md` | Règles obligatoires |
| `adp-docs/02-gouvernance-ia/02-conventions-redaction.md` | Marqueurs et conventions |
| `adp-docs/02-gouvernance-ia/03-perimetre-agents.md` | Périmètre d'action autorisé |
| `adp-docs/02-gouvernance-ia/04-anti-patterns.md` | Anti-patterns à éviter |
| `[autre fichier]` | [Raison] |

---

## Fichiers à produire ou modifier (outputs)

> L'agent ne modifie que ces fichiers.

| Fichier | Action | Description |
|---------|--------|-------------|
| `[chemin/fichier.md]` | Créer / Compléter | [Ce qu'il doit y écrire] |

---

## Comportement en cas d'ambiguïté

Si une instruction de ce task pack est ambiguë, contradictoire, ou si deux règles semblent s'opposer :

1. **Arrêter** la partie ambiguë — ne pas interpréter, ne pas choisir
2. **Documenter** l'ambiguïté dans l'output : `[AMBIGUÏTÉ — en attente de clarification] Description du problème`
3. **Continuer** les parties claires et indépendantes
4. **Signaler** l'ambiguïté dans le bloc "Signalement agent"

**Les contraintes priment sur l'objectif.** Si accomplir l'objectif implique de violer une règle de `01-regles-ia.md`, l'agent signale l'impossibilité — il ne viole pas la règle.

---

## Contraintes impératives

- [ ] Utiliser les marqueurs définis dans `02-conventions-redaction.md` sur **chaque affirmation** (fait, hypothèse, inconnue, recommandation)
- [ ] Ne pas modifier de fichiers hors de la liste ci-dessus
- [ ] Ne pas inventer de fait sans source explicite dans ce repo
- [ ] Signaler toute inconnue bloquante avec `[INCONNUE BLOQUANTE]`
- [ ] Terminer par un bloc "Signalement agent"
- [ ] Ne pas créer de fichier supplémentaire jugé utile sans validation humaine (R-07b)
- [ ] Vérifier qu'une issue GitHub existe pour cette action avant de commencer (R-16b)
- [ ] Si reprise de session : lire `git log` et les fichiers cibles avant d'agir — ne pas supposer que le résumé est à jour (R-26)
- [ ] Mettre à jour le champ `Dernière mise à jour` dans tout fichier modifié qui contient ce champ (R-27)
- [ ] Toute promotion `[HYPOTHÈSE]` → `[FAIT]` : citer la source directement dans le document (outil + date), pas seulement dans le Signalement (R-28)
- [ ] Avant d'utiliser une spec de `05-specs/pages/` : vérifier que son statut n'est pas `[EN RÉVISION — ADR-XXX]` — si oui, lire l'ADR référencé avant toute implémentation (R-29)
- [ ] [Contrainte spécifique à cette tâche]

---

## Critères de validation (pour le chef de projet)

Après exécution, vérifier :

- [ ] [Critère 1 — vérifiable, concret]
- [ ] [Critère 2]
- [ ] [Critère 3]
- [ ] Le bloc "Signalement agent" est présent et complet
- [ ] Aucun fichier hors périmètre n'a été modifié

---

## Ce que cet agent ne doit pas faire

- [Exclusion 1]
- [Exclusion 2]
- Modifier `00-initialisation-projet.md`
- Écrire dans `adp-app/` ou `adp-legacy/` — sauf si ce task pack est un task pack Lot 3 et liste explicitement `adp-app/` dans ses outputs (R-25)

---

## Prochaine étape après validation

[Tâche ou task pack suivant à lancer après validation de celui-ci]
