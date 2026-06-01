---
name: rgpd
description: GDPR compliance — data processing inventory, consent, forms audit, user rights, legal notices, privacy policy
cross_references:
  - specs-fonctionnelles.features → forms and data collection points
required_sections:
  - data_processing_inventory
  - cookie_consent
  - forms_audit
  - user_rights
  - legal_notices
  - privacy_policy_structure
  - hosting_and_transfers
  - action_items
light_sections:
  - data_processing_inventory
  - cookie_consent
  - legal_notices
  - action_items
output_file: work/01-discovery/rgpd.md
---

# RGPD — {project_name}

date: {YYYY-MM-DD}
dpo: {name} — {contact}

## data_processing_inventory

| processing | data_collected | legal_basis | retention_period |
|-----------|---------------|-------------|-----------------|
| {processing} | {data} | consent / contract / legitimate_interest / legal_obligation | {duration} |

## cookie_consent

- tool: {tool_name} — {justification}
- categories:
  - strictly_necessary: {list}
  - analytics: {list}
  - marketing: {list_or_none}

## forms_audit

Cross-ref with specs-fonctionnelles features.

| form | required_fields | explicit_consent | privacy_policy_link |
|------|----------------|-----------------|-------------------|
| {form} | {fields} | yes / no | yes / no |

## user_rights

| right | implementation |
|-------|---------------|
| access | {how} |
| rectification | {how} |
| deletion | {how} |
| portability | {how} |
| objection | {how} |

## legal_notices

```
publisher: {company_name}
address: {address}
siret: {siret}
publication_director: {name}
contact: {email}
host: {host_name} — {host_address}
```

## privacy_policy_structure

Required 10 points:
1. data_controller_identity
2. data_collected_and_purposes
3. legal_basis
4. retention_periods
5. data_recipients
6. non_eu_transfers
7. user_rights
8. cookies_and_trackers
9. dpo_contact
10. complaint_right (CNIL — https://www.cnil.fr)

## hosting_and_transfers

- eu_hosting: yes / no — {host}, {country}
- non_eu_subprocessors:

| subprocessor | country | service | safeguards |
|-------------|---------|---------|-----------|
| {name} | {country} | {service} | standard_contractual_clauses / adequacy_decision |

## action_items

- [ ] Write final legal notices
- [ ] Write full privacy policy
- [ ] Configure {consent_tool}
- [ ] Add privacy policy links to all forms
- [ ] Implement user rights mechanisms
