---
name: adr-hebergement
description: Template d'Architecture Decision Record pour le choix d'hébergement et d'infrastructure
---

# ADR — Hébergement & infrastructure — {NOM_DU_PROJET}

> Date : {DATE}
> Statut : ⏳ Proposé / ✅ Accepté / ❌ Rejeté
> Décideurs : {LISTE_DECIDEURS}

## Contexte

{DESCRIPTION_DES_BESOINS_INFRA}

Contraintes héritées (voir [[cadrage]], [[rgpd]] si présent) :

- **Localisation des données** : {EU_REQUIS_OUI_NON}
- **Niveau de disponibilité attendu** : {SLA_CIBLE}
- **Budget mensuel infra** : {BUDGET}
- **Volumétrie estimée (MVP)** : {USERS_RPS_STORAGE}
- **Composants à héberger** : {LISTE_COMPOSANTS}

## Décision

### Hébergement retenu

| Composant | Hébergeur | Région | Type | Coût estimé (€/mois) |
|-----------|-----------|--------|------|---------------------|
| Backend API | {HEBERGEUR} | {REGION} | {VPS/SERVERLESS/CONTAINER} | {COUT} |
| Base de données | {HEBERGEUR} | {REGION} | {MANAGED/SELF_HOSTED} | {COUT} |
| Cache / queue | {HEBERGEUR} | {REGION} | — | {COUT} |
| Stockage (fichiers, backups) | {HEBERGEUR} | {REGION} | {S3-compatible} | {COUT} |
| CDN / static | {HEBERGEUR} | {REGION} | — | {COUT} |
| Email transactionnel | {OUTIL} | — | SaaS | {COUT} |
| **Total** | — | — | — | **{TOTAL}** |

### Sous-traitants externes (au-delà de l'hébergement)

| Service | Usage | Localisation | Conformité RGPD |
|---------|-------|--------------|-----------------|
| {SERVICE_1} | {USAGE} | {LOC} | {CCT/DPA} |
| {SERVICE_2} | {USAGE} | {LOC} | {CCT/DPA} |

### Stratégie de déploiement

- **CI/CD** : {OUTIL_CI}
- **Build** : {STRATEGIE_BUILD}
- **Déploiement** : {STRATEGIE_DEPLOIEMENT}
- **Environnements** : {DEV / STAGING / PROD}

### Sauvegardes & restauration

- **Fréquence backups BDD** : {FREQUENCE}
- **Rétention** : {DUREE}
- **Restauration testée** : {OUI_NON_FREQUENCE}
- **Backups répliqués hors région principale** : {OUI_NON}

### Monitoring & alerting

- **Métriques** : {OUTIL}
- **Logs centralisés** : {OUTIL}
- **Erreurs applicatives** : {OUTIL}
- **Uptime** : {OUTIL}
- **Alertes** : {CANAUX_DESTINATAIRES}

## Alternatives considérées

### Alternative 1 — {NOM_ALTERNATIVE_1}

- **Forces** : {FORCES}
- **Faiblesses** : {FAIBLESSES}
- **Pourquoi écartée** : {RAISON}

### Alternative 2 — {NOM_ALTERNATIVE_2}

- **Forces** : {FORCES}
- **Faiblesses** : {FAIBLESSES}
- **Pourquoi écartée** : {RAISON}

## Conséquences

### Positives

- {CONSEQUENCE_POSITIVE_1}

### Négatives / coûts assumés

- {CONSEQUENCE_NEGATIVE_1}

### Risques

| Risque | Impact | Probabilité | Mitigation |
|--------|--------|-------------|------------|
| {RISQUE_1} | {IMPACT} | {PROBA} | {MITIGATION} |

## Critères de revisite

- {SIGNAL_DE_REVISITE_1}

## Plan de migration / scalabilité

{DESCRIPTION_DE_LA_TRAJECTOIRE_SI_LE_PROJET_GROSSIT}
