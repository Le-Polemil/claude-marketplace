---
name: ateliers-ux
description: Template du livrable des ateliers UX
required_sections:
  - Personas
  - User stories
  - Parcours utilisateurs
  - Priorisation des parcours à prototyper
---

# Ateliers UX — {NOM_DU_PROJET}

> Date : {DATE}

## Personas

> Chaque persona DOIT être distinct des autres sur minimum 3 critères (âge, besoin, device, budget, canal).

### Persona 1 — {NOM_PERSONA}

| Attribut | Détail |
|----------|--------|
| Âge | {AGE} |
| Métier / situation | {METIER} |
| Contexte | {CONTEXTE} |
| Device principal | {DEVICE} |
| Budget | {BUDGET} |
| Canal d'acquisition | {CANAL} |

**Besoins principaux :**
{BESOINS_DETAILLES}

**Frustrations :**
{FRUSTRATIONS_DETAILLEES}

**Citation type :**
> "{CITATION_ILLUSTRATIVE}"

---

### Persona 2 — {NOM_PERSONA}

_Même structure. DOIT être clairement différent du Persona 1._

---

## User stories

> Obligatoire — fait le lien entre personas et spécifications fonctionnelles.

### Épique : {NOM_EPIQUE}

| ID | En tant que… | Je veux… | Afin de… | Priorité |
|----|-------------|----------|----------|----------|
| US-001 | {NOM_PERSONA} | {ACTION_CONCRETE} | {BENEFICE_MESURABLE} | 🔴 Must / 🟠 Should / 🟡 Could |
| US-002 | {NOM_PERSONA} | {ACTION_CONCRETE} | {BENEFICE_MESURABLE} | 🔴 / 🟠 / 🟡 |

### Épique : {NOM_EPIQUE_2}

| ID | En tant que… | Je veux… | Afin de… | Priorité |
|----|-------------|----------|----------|----------|
| US-003 | {NOM_PERSONA} | {ACTION_CONCRETE} | {BENEFICE_MESURABLE} | 🔴 / 🟠 / 🟡 |

---

## Parcours utilisateurs

### Parcours 1 — {NOM_DU_PARCOURS}

**Persona concerné :** {NOM_PERSONA}
**Objectif :** {OBJECTIF}
**Priorité de prototypage :** 🔴 Haute / 🟠 Moyenne / 🟡 Basse

#### Happy path

1. {ETAPE_1}
2. {ETAPE_2}
3. {ETAPE_3}
4. {ETAPE_4}

#### Edge cases

| Cas | Déclencheur | Comportement attendu |
|-----|------------|---------------------|
| {EDGE_CASE_1} | {DECLENCHEUR_TECHNIQUE_OU_CONTEXTUEL} | {COMPORTEMENT_UX_CONCRET} |
| {EDGE_CASE_2} | {DECLENCHEUR} | {COMPORTEMENT} |

---

## Priorisation des parcours à prototyper

| Parcours | Persona | Priorité | Complexité | À prototyper |
|----------|---------|----------|------------|-------------|
| {PARCOURS_1} | {PERSONA} | 🔴 Haute | S / M / L | ✅ |
| {PARCOURS_2} | {PERSONA} | 🟠 Moyenne | S / M / L | ✅ / ❌ |
