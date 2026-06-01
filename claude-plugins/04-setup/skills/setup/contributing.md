---
name: contributing
description: Template guide de contribution (structure repo, conventions Git, CI/CD, process review)
---

# Guide de contribution — {NOM_DU_PROJET}

> Date : {DATE}
> Statut : ⏳ Proposé / ✅ Validé

## Vue d'ensemble

{DESCRIPTION_COURTE_DU_PROJET_ET_DE_L_AUDIENCE_DU_GUIDE}

## Prérequis

- {OUTIL_1} version {VERSION}
- {OUTIL_2} version {VERSION}
- Compte sur {SERVICE_1}

## Installation initiale

```bash
# Cloner
git clone {REPO_URL}
cd {NOM_REPO}

# Installer dépendances
{COMMANDE_INSTALL}

# Configurer secrets locaux (voir [[env-example]])
cp .env.example .env
# → éditer .env avec les valeurs requises

# Démarrer en local
{COMMANDE_DEV}
```

## Structure du dépôt

```
{NOM_REPO}/
├── {DIR_1}/         # {DESCRIPTION}
├── {DIR_2}/         # {DESCRIPTION}
└── ...
```

**Type de dépôt :** {MONOREPO / POLYREPO}
**Outil de gestion :** {PNPM_WORKSPACES / TURBO / NX / LERNA / NA}

## Conventions Git

### Branches

- **Branche principale** : `{MAIN_BRANCH}` — protégée, merge uniquement via PR avec CI verte
- **Branches de travail** : `{PATTERN_BRANCHES}` (ex. `feature/<short-slug>`, `fix/<issue-num>-<slug>`, `refactor/<area>`)
- **Stratégie** : {GIT_FLOW / TRUNK_BASED / GITHUB_FLOW}
- **Branches à éviter** : `master`, `dev`, `develop` (sauf si convention historique active)

### Commits

- **Convention** : {CONVENTIONAL_COMMITS / GITMOJI / LIBRE}
- **Préfixes autorisés** : `feat`, `fix`, `refactor`, `chore`, `docs`, `test`, `perf`, `build`, `ci`
- **Format** : `<type>(<scope>): <description courte impératif présent>`
- **Exemple** : `feat(auth): add magic link expiration check`

### Pull Requests

- **Titre** : doit suivre le format Conventional Commits
- **Description** : utiliser le template `PR_TEMPLATE.md`
- **Reviewers requis** : {N_REVIEWERS} ({CODEOWNERS_OU_AUTRE})
- **CI bloquante** : {OUI_NON} (cf. section CI/CD)
- **Stratégie de merge** : {SQUASH / REBASE / MERGE_COMMIT}

## Code style

| Aspect | Outil | Config |
|--------|-------|--------|
| Lint | {OUTIL_LINT} | {FICHIER_CONFIG} |
| Format | {OUTIL_FORMAT} | {FICHIER_CONFIG} |
| Type checking | {OUTIL_TYPE} (si applicable) | {FICHIER_CONFIG} |
| Hooks pre-commit | {OUTIL_HOOKS} | {FICHIER_CONFIG} |

### Règles spécifiques

- {REGLE_1}
- {REGLE_2}

## Tests

| Type | Outil | Quand | Bloquant CI |
|------|-------|-------|-------------|
| Unitaires | {OUTIL_UNIT} | À chaque commit | ✅ |
| Intégration | {OUTIL_INTEG} | À chaque PR | ✅ |
| E2E | {OUTIL_E2E} | À chaque PR | ✅ |
| A11y (cf. [[a11y-rules]]) | {OUTIL_A11Y} | À chaque PR | ✅ |
| Visual regression | {OUTIL_VRT} | Optionnel | ❌ |
| Performance | {OUTIL_PERF} | Nightly | ❌ |

### Coverage minimum

- Cible : ≥ {%} pour les modules critiques
- Outil de mesure : {OUTIL}

## CI/CD

### Plateforme

**{GITHUB_ACTIONS / GITLAB_CI / CIRCLECI / AUTRE}**

### Pipelines

#### Pipeline 1 — Sur chaque push (toutes branches)

| Étape | Action | Bloquante |
|-------|--------|-----------|
| Checkout + setup | {COMMANDE} | ✅ |
| Install deps | {COMMANDE} | ✅ |
| Lint | {COMMANDE} | ✅ |
| Type check | {COMMANDE} | ✅ |
| Tests unitaires | {COMMANDE} | ✅ |
| Build | {COMMANDE} | ✅ |

#### Pipeline 2 — Sur pull request

Inclut Pipeline 1 + :

| Étape | Action | Bloquante |
|-------|--------|-----------|
| Tests intégration | {COMMANDE} | ✅ |
| Tests E2E | {COMMANDE} | ✅ |
| Tests a11y | {COMMANDE} | ✅ |
| Build preview environment | {COMMANDE} | ❌ |

#### Pipeline 3 — Sur push `{MAIN_BRANCH}`

Inclut Pipeline 2 + :

| Étape | Action |
|-------|--------|
| Build production | {COMMANDE} |
| Push image / artefacts | {COMMANDE} |
| Déploiement staging | {COMMANDE} |
| Déploiement prod | {AUTOMATIQUE_OU_MANUEL_OU_TAG} |

### Secrets utilisés en CI

Ces secrets doivent être configurés dans **{LIEU_DES_SECRETS_CI}** :

- `{SECRET_1}` — {USAGE}
- `{SECRET_2}` — {USAGE}

> ⚠️ Voir [[env-example]] pour la liste exhaustive et la procédure de rotation.

### Caches CI

| Cache | Contenu | Clé |
|-------|---------|-----|
| {NOM_CACHE_1} | {CONTENU} | {CLE} |

## Environnements

| Environnement | URL | Déploiement | Données |
|---------------|-----|-------------|---------|
| Dev local | `localhost:{PORT}` | Manuel (`{COMMANDE_DEV}`) | Données mock / locales |
| Staging | `staging.{DOMAIN}` | Automatique sur push `{BRANCHE}` | Données de staging |
| Production | `{DOMAIN}` | {AUTOMATIQUE_OU_MANUEL} | Données réelles |

## Process de revue

### Critères d'acceptation d'une PR

- [ ] Code conforme au lint + format
- [ ] Type checking passe
- [ ] Tests unitaires + intégration verts
- [ ] Tests a11y verts (cf. [[a11y-rules]])
- [ ] CHANGELOG mis à jour si feature ou fix user-visible
- [ ] Documentation mise à jour si API publique modifiée
- [ ] {AUTRE_CRITERE}

### Template de PR

Le fichier `.github/PULL_REQUEST_TEMPLATE.md` doit contenir :

```markdown
## Contexte

Pourquoi ce changement ? (lien issue, contexte produit)

## Changements

- ...

## Comment tester

1. ...

## Checklist

- [ ] Tests ajoutés / mis à jour
- [ ] Documentation mise à jour
- [ ] A11y vérifiée si UI modifiée
```

### CODEOWNERS

Le fichier `.github/CODEOWNERS` (ou équivalent) définit qui review quoi :

```
{DIR_OU_FICHIER}    @{USER_OU_TEAM}
```

## Conventions par langage / framework

### {LANGAGE_1}

- {CONVENTION_1}

### {FRAMEWORK_1}

- {CONVENTION_1}

## Versioning et releases

- **Stratégie** : {SEMVER / CALVER / AUTRE}
- **Outil** : {CHANGESETS / SEMANTIC_RELEASE / MANUEL}
- **Changelog** : {OUI_NON_FORMAT}
- **Tag Git** : {FORMAT}

## Références

- [Conventional Commits](https://www.conventionalcommits.org)
- {AUTRE_LIEN}
