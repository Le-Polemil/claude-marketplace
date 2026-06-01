---
name: specs-fonctionnelles
description: Functional specs — scope, features with persona/KPI refs, business rules, constraints, prioritization matrix
cross_references:
  - cadrage.kpis → feature acceptance criteria
  - ateliers-ux.personas → feature persona mapping
  - ateliers-ux.user_stories → feature user story links
required_sections:
  - scope
  - features
  - business_rules
  - tech_constraints
  - regulatory_constraints
  - prioritization_matrix
light_sections:
  - scope
  - features
  - prioritization_matrix
output_file: work/01-discovery/specs-fonctionnelles.md
---

# Specs fonctionnelles — {project_name}

date: {YYYY-MM-DD}
version: 1.0

## scope

in:
- {included_item}

out:
- {excluded_item} — {reason}

## features

Reference personas from ateliers-ux.md and KPIs from cadrage.md where relevant.

### {feature_name}

- priority: must / should / could / wont
- complexity: S / M / L / XL
- personas: {persona_names from ateliers-ux}
- user_stories: US-{nnn}
- dependencies: {dependencies or none}

description: {description}

acceptance_criteria:
- [ ] {criterion}
- [ ] {criterion_linked_to_kpi_if_relevant}

---

## business_rules

| rule | affected_features | expected_behavior |
|------|------------------|------------------|
| {rule} | {features} | {behavior} |

## tech_constraints

| constraint | detail | impact |
|-----------|--------|--------|
| {constraint} | {detail} | {impact} |

## regulatory_constraints

| regulation | requirement | affected_features |
|-----------|------------|------------------|
| {regulation} | {requirement} | {features} |

## prioritization_matrix

| feature | priority | complexity | personas | estimated_sprint |
|---------|----------|-----------|----------|-----------------|
| {feature} | must / should / could | S / M / L | {persona} | sprint_{n} |
