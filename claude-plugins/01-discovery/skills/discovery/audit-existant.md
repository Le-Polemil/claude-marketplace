---
name: audit-existant
description: Template du livrable d'audit de l'existant (refonte)
---

# Audit de l'existant — {NOM_DU_PROJET}

> URL analysée : {URL}
> Date de l'audit : {DATE}

## Crawl technique

### Santé du site

| Métrique | Valeur | Évaluation |
|----------|--------|------------|
| Nombre de pages indexées | {N} | {OK/WARNING/KO} |
| Erreurs 404 | {N} | {OK/WARNING/KO} |
| Redirections 301 | {N} | {OK/WARNING/KO} |
| Pages sans balise title | {N} | {OK/WARNING/KO} |
| Pages sans meta description | {N} | {OK/WARNING/KO} |
| Temps de chargement moyen | {N}s | {OK/WARNING/KO} |

### Performance (Lighthouse)

| Métrique | Score | Objectif |
|----------|-------|----------|
| Performance | {SCORE} | > 90 |
| Accessibility | {SCORE} | > 90 |
| Best Practices | {SCORE} | > 90 |
| SEO | {SCORE} | > 90 |

## Analyse analytics

### Pages les plus visitées

| Page | Visites/mois | Taux de rebond |
|------|-------------|----------------|
| {PAGE_1} | {N} | {N}% |

### Parcours principaux

{DESCRIPTION_DES_PARCOURS_OBSERVES}

### Points de friction identifiés

{POINTS_DE_FRICTION}

## Audit UX heuristique

### Forces

{LISTE_DES_FORCES}

### Faiblesses / irritants

| Irritant | Sévérité | Impact utilisateur |
|----------|----------|-------------------|
| {IRRITANT_1} | 🔴 Critique / 🟠 Majeur / 🟡 Mineur | {IMPACT} |

## Inventaire des contenus

### À conserver

{CONTENUS_A_CONSERVER}

### À réécrire

{CONTENUS_A_REECRIRE}

### À supprimer

{CONTENUS_A_SUPPRIMER}

## Dette technique

{DESCRIPTION_DETTE_TECHNIQUE}

## Recommandations

{RECOMMANDATIONS_PRIORISEES}
