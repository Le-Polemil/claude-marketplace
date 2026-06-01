---
name: schema-archi
description: Template de schéma d'architecture (composants, flux de données, schéma de données)
---

# Schéma d'architecture — {NOM_DU_PROJET}

> Date : {DATE}
> Version : 1.0
> Statut : ⏳ Proposé / ✅ Validé

## Vue d'ensemble

{DESCRIPTION_TEXTUELLE_HAUTE_NIVEAU}

```mermaid
graph TB
    {NOEUDS_ET_FLUX_PRINCIPAUX}
```

## Composants

### Composant 1 — {NOM_COMPOSANT}

| Attribut | Détail |
|----------|--------|
| Rôle | {DESCRIPTION_ROLE} |
| Technologie | {TECHNO} (voir [[adr-stack]]) |
| Hébergement | {HEBERGEUR} (voir [[adr-hebergement]]) |
| Dépendances externes | {DEPENDANCES} |
| Interfaces exposées | {INTERFACES_API_OU_UI} |

**Responsabilités :**
- {RESPONSABILITE_1}
- {RESPONSABILITE_2}

**Non-responsabilités (explicitement out of scope) :**
- {OUT_OF_SCOPE_1}

---

### Composant 2 — {NOM_COMPOSANT}

_Même structure que ci-dessus._

---

## Flux de données critiques

### Flux 1 — {NOM_FLUX}

**Déclencheur :** {EVENEMENT_OU_ACTION}
**Acteurs :** {LISTE_ACTEURS_ET_COMPOSANTS}
**Critères de qualité :** {LATENCE_THROUGHPUT_ETC}

```mermaid
sequenceDiagram
    {DIAGRAMME_SEQUENCE}
```

**Étapes :**
1. {ETAPE_1}
2. {ETAPE_2}
3. {ETAPE_3}

**Cas d'erreur :**
| Erreur | Comportement attendu |
|--------|---------------------|
| {ERREUR_1} | {COMPORTEMENT} |

---

### Flux 2 — {NOM_FLUX}

_Même structure que ci-dessus._

---

## Schéma de données

### Entités principales

```mermaid
erDiagram
    {DIAGRAMME_ENTITES_RELATIONS}
```

| Entité | Champs principaux | Sensibilité RGPD | Durée de conservation |
|--------|-------------------|------------------|----------------------|
| {ENTITE_1} | {CHAMPS} | {SENSIBILITE} | {DUREE} |
| {ENTITE_2} | {CHAMPS} | {SENSIBILITE} | {DUREE} |

### Politique de chiffrement

- **At rest** : {STRATEGIE_CHIFFREMENT_BDD}
- **In transit** : {STRATEGIE_TLS}
- **Données spécifiquement chiffrées au niveau applicatif** : {SI_APPLICABLE}

## Points d'intégration externes

| Service | Type | Authentification | Failure mode |
|---------|------|------------------|--------------|
| {SERVICE_1} | {API/WEBHOOK/STREAMING} | {AUTH} | {FALLBACK} |

## Décisions de design notables

- {DECISION_1_AVEC_RAISON}
- {DECISION_2_AVEC_RAISON}

## Évolutions prévisibles

{DESCRIPTION_DES_AXES_D_EVOLUTION_SANS_REECRIRE_TOUT}
