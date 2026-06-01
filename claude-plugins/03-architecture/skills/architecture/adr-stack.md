---
name: adr-stack
description: Template d'Architecture Decision Record pour le choix de la stack technique
---

# ADR — Stack technique — {NOM_DU_PROJET}

> Date : {DATE}
> Statut : ⏳ Proposé / ✅ Accepté / ❌ Rejeté / 🔄 Remplacé par {ADR_REMPLACANT}
> Décideurs : {LISTE_DECIDEURS}

## Contexte

{DESCRIPTION_DU_CONTEXTE_ET_DU_PROBLEME_A_RESOUDRE}

Contraintes héritées de la phase Discovery (voir [[cadrage]], [[specs-fonctionnelles]]) :

- {CONTRAINTE_1}
- {CONTRAINTE_2}
- {CONTRAINTE_3}

## Décision

### Stack retenue

| Couche | Choix | Version cible |
|--------|-------|---------------|
| Langage backend | {LANGAGE_BACK} | {VERSION} |
| Framework backend | {FRAMEWORK_BACK} | {VERSION} |
| Langage front | {LANGAGE_FRONT} | {VERSION} |
| Framework front | {FRAMEWORK_FRONT} | {VERSION} |
| Base de données | {BDD} | {VERSION} |
| ORM / data layer | {ORM} | {VERSION} |
| Auth | {AUTH} | — |
| Cache / file d'attente | {CACHE_QUEUE} | — |
| Build / packaging | {BUILD_TOOL} | — |
| Tests | {OUTIL_TESTS} | — |
| Linting / formatting | {OUTIL_LINT} | — |

### Justification

{POURQUOI_CETTE_STACK}

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
- {CONSEQUENCE_POSITIVE_2}

### Négatives / coûts assumés

- {CONSEQUENCE_NEGATIVE_1}
- {CONSEQUENCE_NEGATIVE_2}

### Risques

| Risque | Impact | Probabilité | Mitigation |
|--------|--------|-------------|------------|
| {RISQUE_1} | {IMPACT} | {PROBA} | {MITIGATION} |

## Critères de revisite

Cette décision sera revue si :

- {SIGNAL_DE_REVISITE_1}
- {SIGNAL_DE_REVISITE_2}

## Références

- {LIEN_DOC_1}
- {LIEN_DOC_2}
