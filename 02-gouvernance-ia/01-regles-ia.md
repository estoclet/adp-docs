# Gouvernance IA — Règles opérationnelles

**Statut** : Actif — s'applique à tous les agents sans exception  
**Dernière mise à jour** : 2026-04-24  
**Autorité** : Ce document prime sur toute instruction d'un task pack en cas de conflit.  
**Lire avant** : Tout travail dans ce projet.

---

## Principe fondateur

**Un agent IA ne comble jamais un vide par invention silencieuse.**  
Si l'information manque, l'agent le dit explicitement. Si le périmètre est ambigu, il demande. Si une décision est requise, il ne la prend pas seul.

---

## Règles anti-hallucination

### R-01 — Pas de fait sans source
Toute affirmation sur le site, le client, les utilisateurs ou le contenu doit être sourcée (fichier de référence, analyse legacy, brief client). Si la source est absente, utiliser le marqueur `[HYPOTHÈSE]`.

**Interdit** : "Le site reçoit environ 10 000 visites par mois."  
**Autorisé** : "[HYPOTHÈSE] Le site reçoit un trafic significatif — à vérifier avec Google Analytics."

### R-02 — Pas d'invention de besoins
Un agent ne peut pas décider qu'une fonctionnalité est nécessaire si elle n'a pas été exprimée par le client ou le chef de projet. Proposer des recommandations est permis, les traiter comme des faits est interdit.

### R-03 — Pas de chiffre inventé
Aucun chiffre (trafic, conversion, nombre d'articles, délais, budget) ne doit être produit sans source explicite. Utiliser des fourchettes hypothétiques si nécessaire, marquées `[HYPOTHÈSE]`.

### R-04 — Distinguer fait, hypothèse et recommandation
Chaque affirmation dans un document produit par un agent doit appartenir à l'une de ces catégories et être marquée en conséquence. Voir `02-conventions-redaction.md`.

---

## Règles de périmètre

### R-05 — Un task pack, un objectif, des fichiers listés
Un agent travaille uniquement sur les fichiers listés dans son task pack. Il ne modifie pas d'autres fichiers sans demande explicite.

### R-06 — Pas de modification hors scope
Si un agent identifie un problème dans un fichier hors de son scope, il le **signale** dans son output mais ne **modifie pas** ce fichier.

### R-07 — Pas d'extension de périmètre silencieuse
Si pour accomplir une tâche, l'agent estime qu'il faut faire quelque chose qui n'est pas dans le task pack, il le signale et attend validation. Il ne fait pas "un peu plus" sans dire pourquoi.

### R-08 — Ne pas toucher à adp-app ni à adp-legacy
Ces répertoires sont hors du périmètre de `adp-docs`. Les agents qui travaillent dans `adp-docs` n'écrivent pas dans `adp-app` ou `adp-legacy`.

---

## Règles de traçabilité

### R-09 — Toute décision structurante → ADR
Si un agent propose un choix architectural, technique ou organisationnel qui engage le projet, il doit le formuler comme un ADR dans `06-decisions/` et ne pas l'appliquer avant validation humaine.

### R-10 — Une source de vérité par sujet
Chaque information critique (stack, périmètre, décisions) vit dans un seul fichier. Si un agent produit une information redondante dans un autre fichier, il la formule comme un renvoi, pas comme une copie.

**Interdit** : Copier le contenu de `00-initialisation-projet.md` dans `03-legacy/01-inventaire-legacy.md`.  
**Autorisé** : "Voir `00-initialisation-projet.md` pour les décisions prises."

### R-11 — Journal des décisions informelles
Toute décision prise oralement, par message ou en dehors d'un ADR formel doit être enregistrée dans `07-pilotage/02-journal-decisions.md` par le chef de projet.

---

## Règles de validation humaine

### R-12 — Checkpoints obligatoires

Les actions suivantes requièrent une validation humaine **avant** exécution :

| Action | Validation requise |
|--------|-------------------|
| Modifier `00-initialisation-projet.md` | Chef de projet |
| Créer ou clore un ADR | Chef de projet |
| Modifier le périmètre IN/OUT | Chef de projet + client |
| Décider de supprimer du contenu legacy | Chef de projet |
| Changer la stack technique | Chef de projet + client |
| Publier ou déployer quoi que ce soit | Chef de projet |
| Modifier un mapping de redirections validé | Chef de projet |

### R-13 — Signalement des inconnues bloquantes
Si un agent identifie une inconnue qui bloque sa tâche, il la documente dans son output avec le marqueur `[INCONNUE BLOQUANTE]` et liste l'impact. Il ne continue pas en inventant une réponse.

---

## Règles de qualité documentaire

### R-14 — Documents courts et ciblés
Un document = un sujet. Si un sujet dépasse raisonnablement une page de contenu dense, proposer un split logique et le signaler.

### R-15 — Pas de commentaires décoratifs
Les agents ne produisent pas d'introductions génériques, de transitions de remplissage ou de conclusions vides. Chaque ligne d'un document doit apporter une information.

### R-16 — Pas de backlog dans les markdown
Les tickets de travail vivent dans **GitHub Issues** (`github.com/estoclet/adp-docs/issues`). Les markdown de `adp-docs` servent au cadrage, à la gouvernance, aux specs et aux handoffs — pas au suivi de tâches. Voir `07-pilotage/03-github-issues-gouvernance.md`.

---

## En cas de doute

Un agent qui doute de son périmètre doit :
1. Ne pas agir
2. Formuler sa question clairement dans son output
3. Marquer la section concernée `[À ARBITRER]`
4. Attendre une réponse humaine

**La règle d'or : une erreur de prudence est moins coûteuse qu'une erreur d'invention.**
