# Plan de marquage GA4 — Astuces De Pomme

**Statut** : Brouillon [RECOMMANDÉ]  
**Date de création** : 2026-04-27  
**Produit par** : Agent IA  
**Lié à** : `01-initialisation-projet.md`, `ADR-003` (one page)

---

## Objectif

Mesurer l'engagement des utilisateurs sur la homepage *one-page* et l'efficacité des modales de conversion. Les "Pages vues" classiques ne suffisant pas, nous devons suivre les interactions.

---

## Événements recommandés (GA4)

| Nom de l'événement | Paramètres | Déclencheur (Trigger) |
|-------------------|------------|------------------------|
| `open_modal` | `modal_name` : prestations, formations, a_propos, avis, contact | Clic sur un bouton "Voir plus" ou "En savoir plus" |
| `contact_click` | `contact_method` : phone, email | Clic sur le numéro de téléphone ou l'adresse email |
| `form_submission` | `form_id` : contact_form | Envoi réussi du formulaire WPForms |
| `section_scroll` | `section_id` : prestations, formations, a_propos | Arrivée de la section dans le viewport (plus de 50% visible) |

---

## Configuration Redirection & SEO

### Redirections 301 (Legacy → Nouveau)

| Source | Destination |
|--------|-------------|
| `/mentions-legales` | `/mentions-legales/` |
| `/cgv` | `/cgv/` |
| `/infos-fiscales` | `/infos-fiscales/` |
| `/confidentialite` | `/politique-confidentialite/` |

---

## Recommandations techniques

1. **GTM (Google Tag Manager)** : Utiliser GTM pour centraliser les déclencheurs de modales sans modifier le code Divi.
2. **Événements Divi** : Utiliser les classes CSS spécifiques (`.adp-btn-secondary`, etc.) comme sélecteurs dans GTM.
3. **Anonymisation** : S'assurer que les données personnelles (email dans l'URL par exemple) ne sont pas envoyées à GA4 (Conformité RGPD).

---

## Signalement agent

- **Proposition** : Ajout d'un plan de marquage pour compenser la perte de visibilité liée à l'architecture one-page.
- **Hypothèse** : Julien HACHE souhaite suivre la performance de ses services.
- **Prochaine étape** : Validation par Eric STOCLET pour intégration dans le Lot 4 (Recette et Analytics).
