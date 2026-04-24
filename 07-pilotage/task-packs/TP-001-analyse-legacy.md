# TP-001 — Analyse structurelle du site legacy

**Statut** : À lancer  
**Date de création** : 2026-04-24  
**Agent assigné** : Claude (ou autre agent d'analyse)  
**Durée estimée** : Moyen (1 à 3 h selon volume)  
**Lié au lot** : Lot 1 — Analyse du legacy

---

## Objectif unique

Produire un inventaire structurel complet du site legacy (astucesdepomme.com / `adp-legacy/`) : navigation, types de pages, plugins, thème, volume de contenu estimé.

---

## Contexte minimal

- Projet : Refonte d'astucesdepomme.com
- Client : Julien HACHE — site d'astuces Apple et démarches administratives
- Chef de projet : Eric STOCLET
- Le site legacy est disponible localement dans `adp-legacy/` (WordPress)
- Ce task pack couvre uniquement l'inventaire structurel — l'analyse éditoriale est en TP-002
- Repo documentaire : git@github.com:estoclet/adp-docs.git

---

## Fichiers à lire (inputs)

| Fichier | Pourquoi |
|---------|---------|
| `adp-docs/02-gouvernance-ia/01-regles-ia.md` | Règles obligatoires — lire en premier |
| `adp-docs/02-gouvernance-ia/02-conventions-redaction.md` | Marqueurs à utiliser |
| `adp-docs/03-legacy/01-inventaire-legacy.md` | Fichier squelette à compléter |
| `adp-legacy/` (répertoire) | Source à analyser |

**Sources à explorer dans adp-legacy/** :

| Chemin | Quoi chercher |
|--------|--------------|
| `adp-legacy/wp-content/themes/` | Thème(s) actifs |
| `adp-legacy/wp-content/plugins/` | Plugins installés |
| `adp-legacy/wp-content/uploads/` | Volume de médias (approximation par dossiers) |
| `adp-legacy/wp-config.php` | Version WP, nom de la BDD |
| `adp-legacy/wp-includes/version.php` | Version exacte de WordPress |

---

## Fichiers à produire ou modifier (outputs)

| Fichier | Action | Description |
|---------|--------|-------------|
| `adp-docs/03-legacy/01-inventaire-legacy.md` | Compléter | Remplir toutes les sections du squelette avec les informations trouvées |

---

## Méthode de travail

1. Lire `02-gouvernance-ia/01-regles-ia.md` intégralement.
2. Ouvrir `adp-docs/03-legacy/01-inventaire-legacy.md` — c'est le fichier à compléter.
3. Explorer `adp-legacy/wp-content/plugins/` — lister tous les dossiers (un dossier = un plugin).
4. Explorer `adp-legacy/wp-content/themes/` — identifier le thème actif (chercher `stylesheet` dans `wp-config.php` ou README du thème).
5. Lire `adp-legacy/wp-includes/version.php` pour la version WP.
6. Explorer `adp-legacy/wp-content/uploads/` — estimer le volume par dossiers annuels.
7. Tenter d'accéder au fichier `adp-legacy/llms.txt` s'il existe — peut contenir des métadonnées utiles.
8. Compléter le fichier d'inventaire section par section.
9. Signaler `[INCONNUE]` pour tout ce qui ne peut pas être déterminé sans accès BDD ou admin WP.
10. Rédiger le bloc "Signalement agent" en fin de document.

---

## Contraintes impératives

- [ ] Utiliser les marqueurs définis dans `02-conventions-redaction.md`
- [ ] Ne pas modifier de fichiers hors de la liste outputs
- [ ] Ne pas accéder à `adp-app/`
- [ ] Ne pas modifier `adp-legacy/` (lecture seule)
- [ ] Ne pas inventer de volumes ou de métriques — utiliser `[INCONNUE]` si non disponible
- [ ] Signaler toute information qui nécessiterait un accès BDD avec `[INCONNUE BLOQUANTE — requiert I-06]`
- [ ] Terminer par un bloc "Signalement agent"

---

## Critères de validation (Eric STOCLET)

Après exécution, vérifier :

- [ ] La section "Plugins actifs" est complétée (liste réelle des dossiers plugins)
- [ ] La section "Thème actif" est complétée
- [ ] La version WordPress est renseignée
- [ ] Le volume de médias est estimé (même approximativement)
- [ ] Les sections non accessibles sont marquées `[INCONNUE]` ou `[INCONNUE BLOQUANTE]`
- [ ] Le bloc "Signalement agent" est présent et complet
- [ ] Aucun fichier hors périmètre n'a été modifié

---

## Ce que cet agent ne doit pas faire

- Modifier le contenu de `adp-legacy/` de quelque façon que ce soit
- Écrire dans `adp-app/`
- Rédiger des recommandations de migration dans ce fichier (c'est TP-002 et TP-004)
- Modifier `00-initialisation-projet.md`
- Créer de nouveaux fichiers non listés dans les outputs

---

## Prochaine étape après validation

Lancer **TP-002 — Analyse éditoriale du contenu legacy** sur la base de l'inventaire complété.
