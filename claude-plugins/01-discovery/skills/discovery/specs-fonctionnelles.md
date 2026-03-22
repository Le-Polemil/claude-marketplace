---
name: specs-fonctionnelles
description: Template du livrable de spécifications fonctionnelles
required_sections:
  - Périmètre — In scope
  - Périmètre — Out of scope
  - Fonctionnalités détaillées
  - Règles métier
  - Contraintes techniques
  - Contraintes réglementaires
  - Matrice de priorisation
---

# Spécifications fonctionnelles — {NOM_DU_PROJET}

> Date : {DATE}
> Version : 1.0
> Statut : ✅ Validé / ⏳ En attente de validation

## Périmètre

### In scope

{LISTE_DETAILLEE_DE_CE_QUI_EST_INCLUS}

### Out of scope

{LISTE_DETAILLEE_DE_CE_QUI_EST_EXCLU — avec justification}

## Fonctionnalités

> Chaque fonctionnalité référence le(s) persona(s) concerné(s) depuis ateliers-ux.md.

### {NOM_FONCTIONNALITE_1}

| Attribut | Détail |
|----------|--------|
| Priorité | 🔴 Must / 🟠 Should / 🟡 Could / ⚪ Won't |
| Complexité | S / M / L / XL |
| Persona(s) concerné(s) | {NOM_PERSONA_1}, {NOM_PERSONA_2} |
| User stories liées | US-{XXX}, US-{XXX} |
| Dépendances | {DEPENDANCES} |

**Description :**
{DESCRIPTION_DETAILLEE}

**Règles métier :**
- {REGLE_1}
- {REGLE_2}

**Critères d'acceptation :**
- [ ] {CRITERE_1}
- [ ] {CRITERE_2}
- [ ] {CRITERE_LIE_AU_KPI_DU_CADRAGE_SI_PERTINENT}

---

## Règles métier transversales

| Règle | Fonctionnalités impactées | Comportement attendu |
|-------|--------------------------|---------------------|
| {REGLE} | {FEATURES} | {COMPORTEMENT_DETAILLE} |

## Contraintes techniques

| Contrainte | Détail | Impact |
|-----------|--------|--------|
| {CONTRAINTE} | {DETAIL} | {IMPACT_SUR_LE_PROJET} |

## Contraintes réglementaires

| Réglementation | Exigence | Fonctionnalités impactées |
|----------------|----------|--------------------------|
| RGPD | {EXIGENCE_CONCRETE} | {FONCTIONNALITES} |
| Accessibilité (RGAA/WCAG) | {EXIGENCE_CONCRETE} | {FONCTIONNALITES} |
| {AUTRE} | {EXIGENCE} | {FONCTIONNALITES} |

## Matrice de priorisation

| Fonctionnalité | Priorité | Complexité | Persona(s) | Sprint estimé |
|----------------|----------|------------|------------|---------------|
| {FEATURE_1} | 🔴 Must | M | {PERSONA} | Sprint 1 |
| {FEATURE_2} | 🟠 Should | L | {PERSONA} | Sprint 2 |
