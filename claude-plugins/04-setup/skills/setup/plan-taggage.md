---
name: plan-taggage
description: Template de plan de tagging analytics (events, propriétés, conventions, RGPD-friendly)
---

# Plan de tagging analytics — {NOM_DU_PROJET}

> Date : {DATE}
> Statut : ⏳ Proposé / ✅ Validé
> Référence métriques : voir North Star Metric et KPIs en [[business-model]] et [[cadrage]]

## Principes de tagging

1. **Ne tracker que ce qui sert une décision** — chaque event doit pouvoir répondre à une question business
2. **Anonymisation par défaut** — IP hashée, pas de données nominatives sauf nécessité
3. **Pas de payload contenu utilisateur** — jamais le texte lu, jamais l'image, jamais les emails dans les events
4. **Convention stricte de nommage** — voir section "Conventions"
5. **Documentation à jour** — chaque event est documenté ici avant d'être implémenté
6. **Opt-out respecté** — si l'utilisateur désactive l'analytics dans ses settings, aucun event n'est envoyé

## Outils retenus

| Catégorie | Outil | Localisation données | Pourquoi |
|-----------|-------|----------------------|----------|
| Analytics produit | {PLAUSIBLE / MATOMO / POSTHOG / MIXPANEL} | {EU/US} | {JUSTIFICATION} |
| Observabilité erreurs | {SENTRY / GLITCHTIP / BUGSNAG} | {EU/US} | {JUSTIFICATION} |
| Uptime monitoring | {UPTIME_KUMA / BETTERSTACK / PINGDOM} | {LOCALISATION} | {JUSTIFICATION} |
| Session replay (si applicable) | {OUTIL_OU_AUCUN} | {LOC} | {JUSTIFICATION} |
| Logs centralisés | {OUTIL} | {LOC} | {JUSTIFICATION} |

## Conventions de nommage

### Events

- **Format** : `{snake_case_ou_dot.notation}` — choisir une seule convention et s'y tenir
- **Préfixe par domaine** : `auth_*`, `billing_*`, `feature_*`
- **Pattern** : `{objet}_{action}` (ex. `signup_completed`, `description_triggered`)
- **Pas de timestamps dans le nom** (le timestamp est une propriété)

### Propriétés

- Snake_case
- Types simples : string, number, boolean (pas d'objets imbriqués profonds)
- Préfixes par contexte : `user_`, `page_`, `device_`

## Catalogue d'events

### Domaine — Acquisition / Onboarding

| Event | Description | Quand | Propriétés clés |
|-------|-------------|-------|----------------|
| `landing_viewed` | Page d'accueil vue | Au chargement | `referrer`, `utm_*` |
| `signup_started` | Formulaire d'inscription ouvert | Au focus du champ email | `source` |
| `signup_completed` | Compte créé | Email validé | `signup_method`, `time_to_complete_seconds` |
| `onboarding_step_completed` | Étape onboarding finie | À chaque step | `step_number`, `step_name`, `time_spent_seconds` |
| `onboarding_abandoned` | Onboarding interrompu | Fermeture sans terminer | `last_step_completed` |

### Domaine — Engagement / North Star

> S'appuyer sur la **North Star Metric** définie dans [[business-model]]. Ces events doivent permettre de la calculer.

| Event | Description | Quand | Propriétés clés |
|-------|-------------|-------|----------------|
| `{NSM_EVENT_1}` | {DESC} | {QUAND} | {PROPS} |

### Domaine — Conversion / Pricing

| Event | Description | Quand | Propriétés clés |
|-------|-------------|-------|----------------|
| `pricing_viewed` | Page tarifs vue | Au chargement | `referrer` |
| `pricing_tier_clicked` | Clic sur un tier | Au clic | `tier`, `billing_cycle` |
| `checkout_started` | Stripe Checkout ouvert | Redirection | `tier`, `billing_cycle`, `price_eur` |
| `subscription_created` | Abonnement actif | Webhook Stripe | `tier`, `billing_cycle`, `mrr_eur` |
| `subscription_canceled` | Annulation demandée | Webhook Stripe | `tier`, `tenure_days`, `reason` (si captée) |
| `subscription_upgraded` | Bascule tier supérieur | Webhook | `from_tier`, `to_tier`, `mrr_delta_eur` |
| `subscription_downgraded` | Bascule tier inférieur | Webhook | `from_tier`, `to_tier`, `mrr_delta_eur` |

### Domaine — Erreurs / Performance

> Ces events vont aussi côté Sentry pour les détails, mais on garde des compteurs côté analytics produit pour les vues d'ensemble.

| Event | Description | Propriétés |
|-------|-------------|------------|
| `error_displayed` | Erreur visible utilisateur | `error_type`, `error_code`, `context` |
| `feature_failed` | Une feature a échoué côté serveur | `feature`, `failure_reason` |

### Domaine — Settings / Configuration

| Event | Description | Propriétés |
|-------|-------------|------------|
| `setting_changed` | Modification d'un setting | `setting_name`, `new_value_anonymized` |

## Propriétés globales (envoyées avec tous les events)

| Propriété | Source | Sensibilité |
|-----------|--------|-------------|
| `app_version` | Version build | ❌ |
| `platform` | `extension_chrome` / `app_android` / `web` | ❌ |
| `locale` | Langue utilisateur | ❌ |
| `is_authenticated` | Boolean | ❌ |
| `user_tier` | `free` / `pro` / `pro_plus` / `byok` | ❌ |
| `account_age_days` | Durée depuis signup | ❌ |
| `session_id` | UUID éphémère | ❌ (pas d'IP) |

## Ce qu'on NE TRACK PAS (RGPD + éthique)

- ❌ Contenu utilisateur (texte lu, image envoyée, description générée)
- ❌ Email en clair dans les propriétés
- ❌ IP non hashée
- ❌ URL des pages tierces lues (juste un compteur agrégé)
- ❌ Données de santé / handicap au-delà du strict utile à l'amélioration produit
- ❌ Tracking cross-site (pas de cookies tiers, pas de fingerprinting)

## Conformité RGPD (cf. [[rgpd]])

- **Base légale** : intérêt légitime (analytics anonymisé) ou consentement explicite si données identifiables
- **Solution de consentement** : voir [[rgpd]] section consentement
- **Durée de conservation** : 13 mois rolling, puis agrégat anonymisé
- **DPA signé** avec chaque outil tiers
- **Localisation** : préférer hébergement EU pour minimiser les transferts

## Implémentation

### Library de tracking (wrapper maison)

Créer un module `analytics/` qui :
- Centralise tous les events (un seul endroit pour les nommer et les typer)
- Respecte le opt-out utilisateur (lecture `user.settings.analytics_opt_out`)
- Tape les propriétés avec TypeScript (impossible d'envoyer un event mal formé)
- Bufferise et batch les envois (réduire les requêtes)

### Exemple d'API attendue

```typescript
import { track } from '@/analytics'

track('signup_completed', {
  signup_method: 'magic_link',
  time_to_complete_seconds: 47,
})
```

### Tests

- **Tests unitaires** sur le wrapper analytics : opt-out, format, batching
- **Tests d'intégration** : vérifier que les events critiques sont bien envoyés au bon moment

## Monitoring du tracking lui-même

| Indicateur | Cible | Outil |
|------------|-------|-------|
| Taux d'events perdus | < 1 % | Mesure côté server (réception) vs client (émission) |
| Latence envoi event | < 100 ms p95 | Sentry / Plausible API monitoring |
| Outage outil analytics | Alertes | Uptime Kuma sur Plausible |

## Plan de validation

- [ ] Implémentation library analytics
- [ ] Implémentation des events Domaine "Acquisition / Onboarding"
- [ ] Implémentation des events Domaine "Engagement / North Star"
- [ ] Implémentation des events Domaine "Conversion / Pricing"
- [ ] Test E2E : un parcours utilisateur génère bien tous les events attendus
- [ ] Audit RGPD : vérifier que rien d'interdit n'est tracé
- [ ] Dashboard Plausible / outil configuré avec les métriques business
- [ ] Documentation utilisateur sur l'opt-out

## Évolution du plan

| Quand | Action |
|-------|--------|
| Post-MVP, après 100 users actifs | Revue de la pertinence de chaque event (rentabilité du tracking) |
| À chaque feature majeure | Ajout des events spécifiques en même temps que le dev |
| Annuel | Audit RGPD complet + purge des events non utilisés |

## Références

- [Plausible Analytics — Custom events](https://plausible.io/docs/custom-event-goals)
- [Sentry SDK](https://docs.sentry.io)
- [GDPR — analytics guidance EU](https://edpb.europa.eu)
- {AUTRE_REFERENCE}
