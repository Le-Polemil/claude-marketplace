# 🏪 Web Project Toolkit — Claude Code Marketplace

> Marketplace privée de plugins Claude Code pour piloter un projet web de A à Z.

## Concept

Chaque plugin correspond à une phase du cycle de vie d'un projet web. Les plugins sont **hybrides** : ils posent les questions clés, puis génèrent les livrables correspondants avec validation stricte.

Toutes les données du projet sont centralisées dans un dossier `work/` avec un fichier `projet.md` qui sert de fil rouge entre les phases.

## Les 11 plugins

| Plugin | Commande | Description |
|--------|----------|-------------|
| project-init | `/project-init` | Initialise work/ et projet.md |
| 01-discovery | `/discovery` | Cadrage, audit, benchmark, UX, specs, RGPD |
| 02-business | `/business` | Business model, pricing, GTM, fundraising |
| 03-architecture | `/architecture` | Stack, hébergement, schéma, a11y, SEO |
| 04-setup | `/setup` | Repo, CI/CD, conventions, secrets, analytics, IA |
| 05-design | `/design` | Wireframes, maquettes, proto, review, handoff |
| 06-ticketing | `/ticketing` | DoD, épiques, tickets, estimation, priorisation |
| 07-development | `/development` | Env local, Storybook, front, back, analytics, review |
| 08-qa | `/qa` | Tests, E2E, cross-browser, a11y, sécu, perf |
| 09-deployment | `/deployment` | Staging, mise en prod, monitoring, redirections |
| 10-post-launch | `/post-launch` | Doc technique, maintenance, rétro, analytics, itérations |

## Installation

```bash
# Ajouter la marketplace
claude plugin marketplace add Le-Polemil/claude-marketplace

# Installer les plugins via le menu interactif
/plugin
# → Discover → sélectionner les plugins voulus

# Ou en CLI
claude plugin install project-init@web-project-toolkit
claude plugin install 01-discovery@web-project-toolkit
```

## Workflow

```bash
/project-init       # Initialiser le projet
/discovery          # Phase 01
/business           # Phase 02
/architecture       # Phase 03
/setup              # Phase 04
/design             # Phase 05
/ticketing          # Phase 06
/development        # Phase 07
/qa                 # Phase 08
/deployment         # Phase 09
/post-launch        # Phase 10
```

## Qualité des livrables

Chaque plugin applique des règles strictes :
- **Conformité template** : toutes les sections obligatoires sont vérifiées
- **Zéro placeholder** : pas de "À définir" ni "TBD" — l'info manquante est redemandée
- **Validation post-génération** : checklist automatique après chaque livrable
- **Cross-référencement** : les personas, KPIs et parcours sont tracés entre les livrables

## Licence

Usage personnel — Le-Polemil
