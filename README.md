# 🏪 Web Project Toolkit — Claude Code Marketplace

> Marketplace privée de plugins Claude Code pour piloter un projet web de A à Z.

## Concept

Chaque plugin correspond à une phase du cycle de vie d'un projet web. Les plugins sont **hybrides** : ils posent les questions clés, puis génèrent les livrables correspondants.

Toutes les données du projet sont centralisées dans un dossier `work/` avec un fichier `projet.md` qui sert de fil rouge entre les phases.

## Les 10 plugins

| Plugin | Commande | Description |
|--------|----------|-------------|
| project-init | `/project-init` | Initialise work/ et projet.md |
| 01-discovery | `/discovery` | Cadrage, audit, benchmark, UX, specs, RGPD |
| 02-architecture | `/architecture` | Stack, hébergement, schéma, a11y, SEO |
| 03-setup | `/setup` | Repo, CI/CD, conventions, secrets, analytics, IA |
| 04-design | `/design` | Wireframes, maquettes, proto, review, handoff |
| 05-ticketing | `/ticketing` | DoD, épiques, tickets, estimation, priorisation |
| 06-development | `/development` | Env local, Storybook, front, back, analytics, review |
| 07-qa | `/qa` | Tests, E2E, cross-browser, a11y, sécu, perf |
| 08-deployment | `/deployment` | Staging, mise en prod, monitoring, redirections |
| 09-post-launch | `/post-launch` | Doc technique, maintenance, rétro, analytics, itérations |

## Installation

```bash
# Ajouter la marketplace
claude plugin marketplace add Le-Polemil/claude-marketplace

# Installer tous les plugins
/plugin
# → Discover → sélectionner les plugins voulus

# Ou en CLI
claude plugin install project-init@web-project-toolkit
claude plugin install 01-discovery@web-project-toolkit
# ... etc
```

## Workflow

```bash
/project-init       # Initialiser le projet
/discovery          # Phase 01 — Discovery
/architecture       # Phase 02 — Architecture
/setup              # Phase 03 — Setup
/design             # Phase 04 — Design
/ticketing          # Phase 05 — Ticketing
/development        # Phase 06 — Développement
/qa                 # Phase 07 — QA / Tests
/deployment         # Phase 08 — Déploiement
/post-launch        # Phase 09 — Post-lancement
```

Chaque plugin :
1. Lit `work/projet.md` pour le contexte
2. Pose les questions clés
3. Génère les livrables dans `work/[phase]/`
4. Met à jour `work/projet.md`

## Licence

Usage personnel — Le-Polemil
