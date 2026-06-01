---
name: pricing
description: Template de stratégie de pricing & packaging (tiers, valeur perçue, unit economics, anchor strategy)
---

# Pricing & packaging — {NOM_DU_PROJET}

> Date : {DATE}
> Statut : ⏳ Proposé / ✅ Validé
> Stratégie tarifaire : {FREEMIUM / FREE_TRIAL / PAID_ONLY / DONATION / AUTRE}

## Objectifs pricing

| Objectif | Cible |
|----------|-------|
| ARPU (revenu moyen par utilisateur payant) | {CIBLE} |
| Taux de conversion freemium → payant | {%} |
| Churn mensuel | < {%} |
| Ratio LTV/CAC | > 3 |
| Payback period | < {MOIS} mois |

## Stratégie générale

{EXPLICATION_DE_LA_STRATEGIE_GLOBALE}

### Pourquoi cette stratégie ?

{JUSTIFICATION_RATIONNELLE}

### Ce que disent les concurrents

| Concurrent | Modèle | Tarifs | Observations |
|------------|--------|--------|--------------|
| {CONC_1} | {MODELE} | {TARIFS} | {OBSERVATIONS} |

> Référence : voir [[benchmark]] pour l'analyse détaillée.

## Tiers / plans

### Tier 1 — {NOM_TIER_1} ({GRATUIT_OU_PRIX})

| Attribut | Détail |
|----------|--------|
| Cible | {QUI} |
| Promesse | {ONE_LINER} |
| Tarif mensuel | {PRIX_OU_GRATUIT} |
| Tarif annuel (avec remise) | {PRIX} |
| Features incluses | {LISTE} |
| Quotas / limites | {LIMITES} |
| Support | {NIVEAU_SUPPORT} |

**Pourquoi ce tier existe :** {RAISON}

---

### Tier 2 — {NOM_TIER_2}

_Même structure._

---

### Tier 3 — {NOM_TIER_3} (si applicable)

_Même structure._

## Anchor strategy

Le tier "anchor" / "le plus mis en avant" est : **{TIER_NOM}**

**Raison :** {EXPLICATION_DU_CHOIX_VISUEL_ET_DE_LA_MISE_EN_AVANT}

## Politique de tarification

### Mensuel vs annuel

- **Remise annuelle** : -{%}
- **Trésorerie** : {AVANCE_ENCAISSEE}
- **Risque churn vs lock-in** : {ANALYSE}

### Devises supportées

- {DEVISE_1} (principal)
- {DEVISE_2} (futur)

### Taxes

- TVA : {APPLICABLE_OUI_NON}, traitement : {COTE_VENDEUR_OU_REVERSE_CHARGE}
- Outils pour gérer la TVA EU multi-pays : {STRIPE_TAX / PADDLE / LEMON_SQUEEZY / AUTRE}

### Promotions et codes

- Code étudiant / non-profit : {OUI_NON} — réduction {%}
- Programme de parrainage : {OUI_NON} — récompense {DESCRIPTION}
- Free month / trial extension : {OUI_NON}

## Tarification B2B / entreprise (si applicable)

- **Seuil de bascule en B2B custom** : à partir de {N_UTILISATEURS} ou {VOLUME}
- **Mode** : devis sur demande, contrats annuels minimum
- **Valeur ajoutée** : SLA, SSO, support prioritaire, fonctionnalités custom, conformité spécifique
- **Tarification indicative** : {FOURCHETTE}

## Unit economics

### CAC estimé par canal

| Canal | CAC estimé | Hypothèses |
|-------|-----------|------------|
| {CANAL_1} | {CAC} | {HYP} |

### LTV estimée par tier

| Tier | LTV estimée | Hypothèses (rétention, ARPU) |
|------|-------------|------------------------------|
| {TIER_2} | {LTV} | {HYP} |

### Sensibilité

| Variable | Hypothèse de base | Variation testée | Impact sur LTV/CAC |
|----------|-------------------|------------------|---------------------|
| Churn mensuel | {VALEUR} | +1 pt | {IMPACT} |
| ARPU | {VALEUR} | -10 % | {IMPACT} |
| CAC | {VALEUR} | +20 % | {IMPACT} |

## Migration / changement de tier

| Scénario | Comportement |
|----------|--------------|
| Upgrade en cours d'abonnement | Prorata + facturation différentielle immédiate |
| Downgrade | Prend effet à la fin du cycle de facturation |
| Annulation | Garde l'accès jusqu'à fin de période, pas de remboursement (à confirmer selon législation) |
| Réactivation | Reprend au même tier sans pénalité dans les X jours |

## Communication tarifaire

### Page pricing

- Nombre de plans visibles : {N} (au-delà de 4, devient illisible)
- Comparaison features par tier (tableau)
- FAQ avec objections fréquentes traitées
- CTA différencié par tier

### Test A/B prévus

- {TEST_1}
- {TEST_2}

## Évolution du pricing

| Échéance | Évolution prévue | Trigger |
|----------|------------------|---------|
| {DATE} | {EVOLUTION} | {TRIGGER} |

## Risques

| Risque | Impact | Mitigation |
|--------|--------|------------|
| Pricing trop bas → revenu insuffisant | Élevé | Tester un palier supérieur en A/B après MVP |
| Pricing trop haut → conversion faible | Élevé | Free tier généreux pour démontrer la valeur |
| {RISQUE_3} | {IMPACT} | {MITIGATION} |

## Références

- {LIEN_INSPIRATION}
