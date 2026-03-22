---
name: audit-existant
description: Template du livrable d'audit de l'existant (refonte)
required_sections:
  - Crawl technique — Santé du site
  - Crawl technique — Performance Lighthouse
  - Analyse analytics — Pages les plus visitées
  - Analyse analytics — Parcours principaux
  - Analyse analytics — Points de friction
  - Audit UX heuristique — Forces
  - Audit UX heuristique — Faiblesses
  - Inventaire des contenus — À conserver
  - Inventaire des contenus — À réécrire
  - Inventaire des contenus — À supprimer
  - Dette technique
  - Recommandations
---

# Audit de l'existant — {NOM_DU_PROJET}

> URL analysée : {URL_COMPLETE}
> Date de l'audit : {DATE}

## Crawl technique

### Santé du site

| Métrique | Valeur | Évaluation |
|----------|--------|------------|
| Nombre de pages indexées | {N} | 🟢 OK / 🟠 Warning / 🔴 KO |
| Erreurs 404 | {N} | 🟢 / 🟠 / 🔴 |
| Redirections 301 | {N} | 🟢 / 🟠 / 🔴 |
| Pages sans balise title | {N} | 🟢 / 🟠 / 🔴 |
| Pages sans meta description | {N} | 🟢 / 🟠 / 🔴 |
| Temps de chargement moyen | {N}s | 🟢 / 🟠 / 🔴 |

### Performance (Lighthouse)

| Métrique | Score | Objectif | Écart |
|----------|-------|----------|-------|
| Performance | {SCORE}/100 | > 90 | {ECART} |
| Accessibility | {SCORE}/100 | > 90 | {ECART} |
| Best Practices | {SCORE}/100 | > 90 | {ECART} |
| SEO | {SCORE}/100 | > 90 | {ECART} |

## Analyse analytics

### Pages les plus visitées

| # | Page | Visites/mois | Taux de rebond | Temps moyen |
|---|------|-------------|----------------|-------------|
| 1 | {PAGE} | {N} | {N}% | {N}s |

### Parcours principaux

{DESCRIPTION_DETAILLEE_DES_PARCOURS_OBSERVES}

### Points de friction identifiés

| Point de friction | Page(s) concernée(s) | Impact estimé |
|-------------------|---------------------|---------------|
| {FRICTION_1} | {PAGES} | 🔴 Fort / 🟠 Moyen / 🟡 Faible |

## Audit UX heuristique

### Forces

| Force | Détail |
|-------|--------|
| {FORCE_1} | {EXPLICATION} |

### Faiblesses / irritants

| Irritant | Sévérité | Impact utilisateur | Recommandation |
|----------|----------|-------------------|----------------|
| {IRRITANT_1} | 🔴 Critique / 🟠 Majeur / 🟡 Mineur | {IMPACT} | {RECOMMANDATION} |

## Inventaire des contenus

### À conserver

| Contenu | Raison | Action requise |
|---------|--------|---------------|
| {CONTENU} | {RAISON} | Migrer tel quel / Adapter |

### À réécrire

| Contenu | Raison | Priorité |
|---------|--------|----------|
| {CONTENU} | {RAISON} | 🔴 / 🟠 / 🟡 |

### À supprimer

| Contenu | Raison |
|---------|--------|
| {CONTENU} | {RAISON} |

## Dette technique

| Élément | Type de dette | Sévérité | Impact sur le projet |
|---------|-------------|----------|---------------------|
| {ELEMENT} | Techno obsolète / Perf / Sécu / Maintenabilité | 🔴 / 🟠 / 🟡 | {IMPACT} |

## Recommandations

| # | Recommandation | Priorité | Effort estimé |
|---|---------------|----------|---------------|
| 1 | {RECO} | 🔴 Haute / 🟠 Moyenne / 🟡 Basse | S / M / L |
