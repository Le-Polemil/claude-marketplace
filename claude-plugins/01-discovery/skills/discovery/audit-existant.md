---
name: audit-existant
description: Existing site audit (refonte only) — tech health, analytics, UX, content inventory, recommendations
condition: projet.refonte == true
required_sections:
  - tech_health
  - lighthouse
  - analytics
  - ux_audit
  - content_inventory
  - tech_debt
  - recommendations
light_sections:
  - tech_health
  - ux_audit
  - content_inventory
  - recommendations
output_file: work/01-discovery/audit-existant.md
---

# Audit existant — {project_name}

url: {site_url}
date: {YYYY-MM-DD}

## tech_health

| metric | value | status |
|--------|-------|--------|
| indexed_pages | {n} | ok / warning / critical |
| 404_errors | {n} | ok / warning / critical |
| 301_redirects | {n} | ok / warning / critical |
| missing_title_or_meta | {n} | ok / warning / critical |
| avg_load_time_seconds | {n} | ok / warning / critical |

## lighthouse

| metric | score | target |
|--------|-------|--------|
| performance | {n}/100 | >90 |
| accessibility | {n}/100 | >90 |
| best_practices | {n}/100 | >90 |
| seo | {n}/100 | >90 |

## analytics

top_pages:

| page | monthly_visits | bounce_rate |
|------|---------------|-------------|
| {page} | {n} | {n}% |

friction_points:

| issue | pages | impact |
|-------|-------|--------|
| {issue} | {pages} | high / medium / low |

## ux_audit

strengths:
- {strength}

weaknesses:

| issue | severity | recommendation |
|-------|----------|---------------|
| {issue} | critical / major / minor | {recommendation} |

## content_inventory

| content | action | reason |
|---------|--------|--------|
| {content} | keep / rewrite / delete | {reason} |

## tech_debt

| item | type | severity | impact |
|------|------|----------|--------|
| {item} | obsolete_tech / perf / security / maintainability | high / medium / low | {impact} |

## recommendations

| priority | recommendation | effort |
|----------|---------------|--------|
| high / medium / low | {recommendation} | S / M / L |
