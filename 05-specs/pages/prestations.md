# Modale Prestations — Spec (Contenu)

**Statut** : [FAIT] Révisé ADR-003 (D-018 one page) — prêt pour intégration  
**Dernière mise à jour** : 2026-04-27 — Transformation page → contenu de modale  
**Produit par** : Agent IA  
**Déclencheur** : Lien "Voir plus" du Bloc 3 (Prestations) ou Bloc 5 (Services SAP) de la Homepage  
**ID Modale cible** : `#modal-prestations`  
**Template Divi** : Popup Divi 5 (Méthode A — Interactions + Visibilité)  
**Lié à** : `ADR-003`, `05-specs/pages/homepage.md`, `04-architecture/03-composants-divi.md`

---

## Objectif du contenu

Détailler les 6 domaines d'intervention d'Astuces De Pomme pour les visiteurs souhaitant approfondir après le résumé de la homepage. Le contenu doit être riche, structuré et inciter à la prise de contact.

---

## Structure du contenu (dans la modale)

La modale est un conteneur défilable (scrollable) reprenant les sections détaillées.

| # | Bloc | Type Divi | Notes |
|---|------|-----------|-------|
| 1 | Titre de la modale | H2 / Titre de section | "Nos services en détail" |
| 2 | Navigation rapide (ancres) | Ligne de pills (optionnel) | Permet de sauter aux sections |
| 3 | Section Assistance Apple | Ligne 2 colonnes | Texte + Icône/Illustration |
| 4 | Section Formation | Ligne 2 colonnes | Texte + Icône/Illustration |
| 5 | Section Réseau & Wi-Fi | Ligne 2 colonnes | Texte + Icône/Illustration |
| 6 | Section Démarches | Ligne 2 colonnes | Texte + Icône/Illustration |
| 7 | Section Sauvegardes | Ligne 2 colonnes | Texte + Icône/Illustration |
| 8 | Section Conseil | Ligne 2 colonnes | Texte + Icône/Illustration |
| 9 | Bouton de fermeture / CTA | Bouton centré | "Fermer et prendre rendez-vous" |

---

## Navigation rapide (ancres internes)

Si la modale est longue, des boutons "pills" permettent de naviguer à l'intérieur :
`Assistance` · `Formation` · `Réseau` · `Démarches` · `Sauvegardes` · `Conseil`

---

## Détail des sections

### Section Assistance Apple
- **Titre** : "Assistance Apple"
- **Texte** : "Votre iPhone ne démarre plus, votre Mac est lent ou votre réseau Wi-Fi ne répond plus ? J'interviens à domicile pour diagnostiquer et résoudre votre problème rapidement, sans jargon."
- **Points clés** : 
    - Diagnostic panne Mac/iPhone/iPad
    - Résolution problèmes iCloud et comptes
    - Nettoyage et optimisation système
    - Récupération de données

### Section Formation Apple
- **Titre** : "Formation personnalisée"
- **Texte** : "Apprenez à maîtriser votre iPhone, Mac ou iPad à votre rythme. Les séances sont personnalisées, adaptées à votre niveau et à vos objectifs."
- **Points clés** :
    - Prise en main débutant
    - Usages avancés et productivité
    - Photos, vidéos et partage familial
    - Sécurité et bonnes pratiques

### Section Réseau & Wi-Fi
- **Titre** : "Réseau & Wi-Fi"
- **Texte** : "Wi-Fi instable, équipements déconnectés, box mal configurée ? J'optimise votre installation pour un fonctionnement fiable."
- **Points clés** :
    - Installation et paramétrage de box
    - Extension de couverture Wi-Fi (Mesh, répéteurs)
    - Connexion TV, imprimantes, objets connectés

### Section Démarches administratives
- **Titre** : "Accompagnement administratif"
- **Texte** : "Je vous accompagne pas à pas pour vos démarches en ligne (Impôts, Ameli, Retraite...) en toute sérénité."
- **Points clés** :
    - Aide aux déclarations en ligne
    - Création et gestion d'identifiants (FranceConnect)
    - Navigation sécurisée sur les portails publics

### Section Sauvegardes & Installation
- **Titre** : "Sauvegardes & Installation"
- **Texte** : "Protégez vos données avec iCloud ou Time Machine. J'installe et configure vos nouveaux appareils pour une transition sans perte."
- **Points clés** :
    - Stratégie de sauvegarde (Cloud + Local)
    - Transfert de données vers nouvel appareil
    - Mises à jour et sécurité

### Section Conseil avant achat
- **Titre** : "Conseil avant achat"
- **Texte** : "Hésitation avant un achat ? Je vous guide avec un avis impartial adapté à votre usage et budget."
- **Points clés** :
    - Aide au choix du modèle (Mac vs iPad...)
    - Analyse des besoins réels
    - Optimisation du budget équipement

---

## CTA de sortie

En bas de modale, un bouton principal :
- **Libellé** : "Prendre rendez-vous"
- **Action** : Fermer la modale et scroller vers `#contact` sur la homepage (ou ouvrir la modale contact si implémentée via ID).

---

## Design & Comportement

- **Fond** : Blanc ou très léger gris (`#f4f8fc`).
- **Typographie** : Identique homepage (`Inter`).
- **Fermeture** : Croix en haut à droite + clic à l'extérieur + bouton de sortie.
- **Mobile** : Contenu empilé verticalement, texte centré.

---

## Signalement agent

- **Modification** : Transformation complète de la spec page en spec contenu modale.
- **Retrait** : Blocs Header, Footer, Hero dédié et sections SEO (devenus sans objet).
- **ID cible** : `#modal-prestations` défini pour l'intégration Divi.
- **Cohérence** : Alignement sur ADR-003.
