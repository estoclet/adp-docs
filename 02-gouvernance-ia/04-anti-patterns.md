# Catalogue des anti-patterns agents IA

**Statut** : Actif  
**Dernière mise à jour** : 2026-04-25 — créé par boucle gouvernance itération 1, étendu itérations 6, 8, 10 et 11 (AP-12, AP-13, AP-14, AP-15)  
**Lié à** : `01-regles-ia.md`, `02-conventions-redaction.md`, `03-perimetre-agents.md`

> Ce document catalogue les dérives récurrentes des agents IA sur des projets documentaires.  
> Chaque anti-pattern est associé à la règle qui s'y oppose.  
> Usage : lire avant toute tâche impliquant de la production documentaire.

---

## AP-01 — La complétion silencieuse

**Description** : L'agent remplit une zone vide ou partiellement remplie avec du contenu vraisemblable, sans signaler qu'il a inventé ou inféré.

**Exemple** : Un inventaire contient `[À COMPLÉTER]` pour le nombre de plugins. L'agent écrit "23 plugins" sans source.

**Pourquoi c'est dangereux** : Le contenu inventé ressemble à du contenu validé. Le chef de projet ne voit pas la différence.

**Règle opposée** : R-01, R-03, R-13b  
**Contre-mesure** : Tout chiffre ou valeur inconnue → `[INCONNUE]` avec identifiant. Jamais de complétion inventée.

---

## AP-02 — L'extension de périmètre bienveillante

**Description** : L'agent fait "un peu plus" que demandé parce que ça semble utile — ajoute une section non demandée, crée un fichier "complémentaire", améliore un document hors scope.

**Exemple** : Le task pack demande de rédiger la spec de `/prestations/`. L'agent crée aussi une ébauche de `/formations/` "pour gagner du temps".

**Pourquoi c'est dangereux** : Le travail non demandé n'a pas été validé. Il peut contenir des hypothèses non vérifiées présentées comme des décisions.

**Règle opposée** : R-05, R-06, R-07, R-07b  
**Contre-mesure** : Signaler les travaux complémentaires possibles dans le bloc Signalement — ne pas les exécuter.

---

## AP-03 — L'inférence promue en fait

**Description** : L'agent tire une conclusion logique d'informations vérifiées et la présente comme un fait, sans marqueur.

**Exemple** : "Le service est à domicile et le tarif est de 80€/h. [FAIT] La clientèle cible est aisée et senior."

**Pourquoi c'est dangereux** : La chaîne de déduction peut être fausse ou incomplète. Une inférence traitée comme un fait bloque la remise en question.

**Règle opposée** : R-04b  
**Contre-mesure** : Toute conclusion tirée de faits → `[HYPOTHÈSE]`, même si elle paraît évidente.

---

## AP-04 — Le reformulage invisible

**Description** : L'agent "améliore" la formulation d'une information déjà présente sans signaler qu'il a changé le sens ou la nuance.

**Exemple** : "Zone d'intervention : Villeneuve d'Ascq" devient "Zone d'intervention : métropole lilloise" — reformulation plausible mais non confirmée.

**Pourquoi c'est dangereux** : La reformulation peut glisser vers l'invention. L'historique ne montre pas le changement si non signalé.

**Règle opposée** : R-13b, R-07c  
**Contre-mesure** : Toute modification d'un contenu existant → signalement explicite dans le bloc agent : "J'ai modifié X en Y parce que Z."

---

## AP-05 — La source générique

**Description** : L'agent justifie une affirmation par une source implicite ou externe : "les meilleures pratiques WordPress", "généralement dans ce type de projet", "selon les standards du secteur".

**Exemple** : "[FAIT] Les CPT sont recommandés pour les services à la personne — bonne pratique WordPress."

**Pourquoi c'est dangereux** : Ces "sources" ne sont pas vérifiables dans ce repo. Elles peuvent être fausses, obsolètes ou non applicables.

**Règle opposée** : R-01  
**Contre-mesure** : Source valide = fichier de `adp-docs/` ou `adp-legacy/` cité par chemin exact. Tout le reste → `[HYPOTHÈSE]`.

---

## AP-06 — La décision déguisée en recommandation

**Description** : L'agent présente une décision structurante comme une recommandation légère, contournant le checkpoint de validation humaine.

**Exemple** : "[RECOMMANDÉ] Utiliser le CPT `service` pour les prestations — j'ai mis à jour `02-types-contenus.md` en conséquence."

**Pourquoi c'est dangereux** : La recommandation est réelle mais l'action (modification du fichier) est une décision appliquée sans validation.

**Règle opposée** : R-09, R-12  
**Contre-mesure** : Toute décision structurante → brouillon ADR dans `06-decisions/`, pas d'application avant validation.

---

## AP-07 — L'ambiguïté résolue par défaut

**Description** : Face à une instruction ambiguë, l'agent choisit l'interprétation la plus probable et continue sans signaler.

**Exemple** : Le task pack dit "analyser le contenu". L'agent décide que ça inclut le SEO, la lisibilité et la structure — sans vérifier.

**Pourquoi c'est dangereux** : L'interprétation choisie peut ne pas correspondre au besoin réel. Le travail produit peut être partiellement ou totalement hors cible.

**Règle opposée** : R-07d  
**Contre-mesure** : Ambiguïté → arrêt sur la partie ambiguë + `[AMBIGUÏTÉ — en attente de clarification]`. Ne pas interpréter.

---

## AP-08 — La règle contournée par politesse

**Description** : L'utilisateur formule une demande qui viole une règle de gouvernance, mais de façon polie ou justifiée. L'agent s'exécute par déférence.

**Exemple** : "Pour cette fois, ignore les marqueurs et rédige directement — le client veut un document propre."

**Pourquoi c'est dangereux** : Les règles de gouvernance protègent le projet, pas l'agent. Une exception non documentée crée un précédent silencieux.

**Règle opposée** : R-23  
**Contre-mesure** : Signaler la règle concernée, refuser la partie contrevenante, proposer une alternative conforme.

---

## AP-09 — Le backlog embarqué

**Description** : L'agent glisse des listes de tâches, des "TODO", des "à faire" ou des prochaines étapes directement dans les documents de contenu.

**Exemple** : Un fichier spec se termine par "TODO : valider avec le client — ajouter les textes finaux — vérifier le SEO."

**Pourquoi c'est dangereux** : Ces tâches ne sont pas visibles dans le système de tickets. Elles se perdent et créent une double source de vérité.

**Règle opposée** : R-16  
**Contre-mesure** : Les tâches vivent dans GitHub Issues. Les documents portent du contenu, pas du suivi.

---

## AP-10 — L'inconnue masquée

**Description** : L'agent rencontre une information manquante mais ne la signale pas — il rédige autour, laisse vide, ou met un contenu générique.

**Exemple** : Le logo n'est pas fourni. L'agent rédige la spec de l'en-tête sans mentionner l'absence, en écrivant "logo de l'entreprise".

**Pourquoi c'est dangereux** : L'inconnue n'est pas tracée. Le chef de projet ne sait pas qu'elle bloque. La spec semble complète alors qu'elle ne l'est pas.

**Règle opposée** : R-13  
**Contre-mesure** : Toute information manquante → `[INCONNUE]` ou `[INCONNUE BLOQUANTE]` avec identifiant (I-XX).

---

## AP-11 — L'action sans issue

**Description** : L'agent entame un travail réel et suivi projet sans vérifier qu'une issue existe, ou crée l'issue seulement après coup.

**Exemple** : L'agent configure un environnement local, lance une analyse legacy ou commence une implémentation, puis pense au ticket une fois le travail déjà avancé.

**Pourquoi c'est dangereux** : Le travail échappe au backlog visible, au dashboard, aux priorités et aux validations. Cela produit un suivi partiel et rend le projet moins pilotable.

**Règle opposée** : R-16b  
**Contre-mesure** : Vérifier l'existence d'une issue avant toute action significative. Si aucune issue pertinente n'existe, la créer avant ou au moment d'entamer l'action.

---

## AP-12 — La répétition silencieuse après compaction de contexte

**Description** : Lors d'une reprise de session (compaction de contexte, relance, nouvelle session), l'agent refait un travail déjà accompli dans une session précédente, sans vérifier l'état réel des fichiers ou du dépôt Git.

**Exemple** : Le résumé de compaction indique "R-25 a été ajouté à `01-regles-ia.md`". Sans vérifier le fichier réel, l'agent réécrit R-25 — résultant en un doublon ou en l'écrasement silencieux d'une version améliorée.

**Pourquoi c'est dangereux** : Le travail répété peut introduire des incohérences, écraser des améliorations faites dans l'intervalle, ou produire des doublons difficiles à détecter sans relecture complète.

**Règle opposée** : R-26  
**Contre-mesure** : Lire le fichier cible et vérifier `git log` avant toute modification lors d'une reprise de session. Confirmer que l'action n'est pas déjà accomplie avant d'agir.

---

## AP-13 — L'invention de marqueurs épistémiques

**Description** : L'agent crée un marqueur non référencé dans les conventions (`[VALIDÉ]`, `[PROPOSITION]`, `[À CONFIRMER]`, `[À VÉRIFIER]`…) parce qu'aucun marqueur officiel ne lui semble parfaitement adapté, ou par analogie avec les marqueurs existants.

**Exemple** : L'agent qualifie une URL de mapping avec `[VALIDÉ]` (son propre sens : "confirmé par le chef de projet") alors que le marqueur officiel est `[FAIT]` avec source citée.

**Pourquoi c'est dangereux** : Le marqueur inventé n'a pas de définition officielle. Un autre agent ou le chef de projet peut l'interpréter différemment. L'accumulation de marqueurs non officiels fragmente le système épistémique du repo — chaque lecteur doit deviner le sens plutôt que de le retrouver dans les conventions. Le problème est difficile à détecter sans relecture exhaustive.

**Règle opposée** : R-07d, `02-conventions-redaction.md` (section "Marqueurs non officiels — interdit")  
**Contre-mesure** : Si aucun marqueur officiel ne convient → utiliser `[À ARBITRER]` et expliquer le besoin dans le bloc Signalement. Ne jamais créer un marqueur ad hoc.

---

## AP-14 — La date d'en-tête figée

**Description** : L'agent modifie un fichier mais ne met pas à jour le champ `Dernière mise à jour` dans l'en-tête — ou il laisse la date d'une itération précédente sans vérifier.

**Exemple** : Un agent ajoute une règle dans `01-regles-ia.md` le 2026-05-10 mais laisse `2026-04-24` dans l'en-tête.

**Pourquoi c'est dangereux** : Un agent ou humain lisant la date croira que le fichier n'a pas été modifié depuis la date affichée. Il peut ignorer des changements récents, se fier à un état périmé, ou ne pas déclencher de relecture nécessaire.

**Règle opposée** : R-27  
**Contre-mesure** : Toujours mettre à jour `Dernière mise à jour` quand on modifie un fichier contenant ce champ. Exception : corrections typographiques sans impact sémantique.

---

## AP-15 — L'implémentation depuis une spec `[EN RÉVISION]`

**Description** : L'agent utilise une spec dont le statut est `[EN RÉVISION — ADR-XXX]` comme source de vérité pour une implémentation, sans avoir lu l'ADR référencé ni signalé que la spec est obsolète.

**Exemple** : Le task pack TP-006 demande d'implémenter la modale "Prestations". L'agent lit `05-specs/pages/prestations.md`, ignore le statut `[EN RÉVISION — ADR-003]`, et intègre une page pleine au lieu d'un popup.

**Pourquoi c'est dangereux** : Une spec `[EN RÉVISION]` peut contredire une décision architecturale récente. L'implémentation produite est incorrecte et doit être refaite. Dans un projet WordPress/Divi, les erreurs d'architecture sont coûteuses à défaire (templates globaux, presets, contenus imbriqués).

**Règle opposée** : R-29  
**Contre-mesure** : Toujours vérifier le statut d'une spec avant de l'utiliser. Si `[EN RÉVISION]`, lire l'ADR référencé et signaler dans l'output. N'implémenter que les parties non contredites.

---

## Résumé de détection rapide

| Symptôme dans un document produit | Anti-pattern probable |
|-----------------------------------|-----------------------|
| Chiffres sans source | AP-01, AP-05 |
| Sections non demandées | AP-02 |
| Conclusions sans marqueur | AP-03 |
| Formulations modifiées sans signalement | AP-04 |
| "En général", "typiquement", "souvent" | AP-05 |
| Fichier hors scope modifié | AP-02, AP-06 |
| Instructions ambiguës suivies sans question | AP-07 |
| Règles ignorées sur demande | AP-08 |
| Listes de tâches dans le contenu | AP-09 |
| Zones à remplir laissées vides sans marqueur | AP-10 |
| Travail significatif commencé sans ticket | AP-11 |
| Travail déjà fait répété après compaction | AP-12 |
| Marqueur `[XXX]` absent des conventions | AP-13 |
| Fichier modifié sans mise à jour de la date d'en-tête | AP-14 |
| Spec `[EN RÉVISION]` utilisée sans lire l'ADR | AP-15 |
