---
name: ateliers-ux
description: UX workshops — personas, user stories, user journeys, prototyping priorities
required_sections:
  - personas
  - user_stories
  - user_journeys
  - journey_prioritization
light_sections:
  - personas
  - user_stories
  - user_journeys
output_file: work/01-discovery/ateliers-ux.md
---

# Ateliers UX — {project_name}

date: {YYYY-MM-DD}

## personas

Constraint: each persona must differ from others on at least 3 attributes.

### {persona_name}

- profile: {age, job, situation}
- device: {primary_device}
- acquisition_channel: {channel}
- needs: {needs}
- frustrations: {frustrations}

---

### {persona_name_2}

Same structure. Must be clearly distinct from persona 1.

---

## user_stories

Format: As {persona_name}, I want {action} so that {benefit}.

| id | persona | action | benefit | priority |
|----|---------|--------|---------|----------|
| US-001 | {persona_name} | {action} | {benefit} | must / should / could |

## user_journeys

### {journey_name}

- persona: {persona_name}
- goal: {goal}

happy_path:
1. {step}
2. {step}
3. {step}

edge_cases:

| case | trigger | expected_behavior |
|------|---------|------------------|
| {case} | {trigger} | {behavior} |

---

## journey_prioritization

| journey | persona | priority | complexity | prototype |
|---------|---------|----------|-----------|-----------|
| {journey} | {persona} | high / medium / low | S / M / L | yes / no |
