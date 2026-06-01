---
name: ia-docs-structure
description: Template structure de documentation pour les agents IA (CLAUDE.md, AGENTS.md, ADRs, READMEs)
---

# Documentation pour agents IA — {NOM_DU_PROJET}

> Date : {DATE}
> Statut : ⏳ Proposé / ✅ Validé

## Pourquoi documenter spécifiquement pour les agents IA

Les agents IA (Claude Code, Cursor, GitHub Copilot, codex CLI, etc.) sont devenus des contributeurs réguliers au code. Une documentation ad hoc leur permet de :

1. **Comprendre le contexte produit** sans relire tout le code
2. **Respecter les conventions** (style, patterns, sécurité, a11y, RGPD)
3. **Éviter les anti-patterns** connus du projet
4. **Accéder aux décisions architecturales** sans les redécouvrir

Cette documentation est **vivante** : elle évolue à chaque décision structurante.

## Agents IA utilisés sur le projet

| Agent | Usage principal | Configuration |
|-------|-----------------|---------------|
| {AGENT_1} | {USAGE} | {FICHIER_CONFIG} |
| {AGENT_2} | {USAGE} | {FICHIER_CONFIG} |

## Structure de documentation

```
{NOM_REPO}/
├── CLAUDE.md                       # Contexte global pour Claude Code
├── AGENTS.md                       # Contexte universel pour agents IA (alternative ou complément)
├── README.md                       # Pour humains et IA, vue d'ensemble du projet
├── CONTRIBUTING.md                 # Lien vers [[contributing]]
├── docs/
│   ├── adr/                        # Architecture Decision Records
│   │   ├── 0001-{topic}.md
│   │   └── 0002-{topic}.md
│   ├── patterns/                   # Patterns réutilisables documentés
│   └── runbooks/                   # Procédures opérationnelles
├── packages/{pkg}/
│   ├── README.md                   # Spécifique au package
│   └── CLAUDE.md                   # Contexte IA si conventions spécifiques
└── .cursorrules                    # Si Cursor utilisé
```

## CLAUDE.md à la racine — structure recommandée

Le fichier `CLAUDE.md` à la racine est lu par Claude Code à chaque session. Il doit contenir :

### 1. Pitch produit (3-5 phrases)

> Que fait le projet ? Pour qui ? Pourquoi c'est utile ?

### 2. Stack technique (lien vers [[adr-stack]])

Synthèse de la stack en quelques lignes + lien vers le détail.

### 3. Conventions critiques que l'IA NE DOIT PAS violer

- Style code (ex. pas de variable `any` en TypeScript)
- Patterns sécurité (ex. jamais logger un mot de passe)
- Patterns a11y (ex. utiliser Radix UI plutôt qu'écrire ses propres modales)
- Patterns RGPD (ex. jamais stocker de payload utilisateur en log)
- Architecture (ex. couches d'optim à respecter, voir [[schema-archi]])

### 4. Workflow Git attendu

Synthèse de [[contributing]] : branches, commits, PRs.

### 5. Commandes utiles

```bash
# Démarrer en dev
{CMD}

# Tests
{CMD}

# Lint
{CMD}
```

### 6. Pointeurs vers la doc détaillée

- `docs/adr/` — décisions architecturales
- `work/` — livrables projet par phase
- `{AUTRE_DOSSIER}` — {DESCRIPTION}

### 7. Choses à NE PAS faire

- {ANTI_PATTERN_1}
- {ANTI_PATTERN_2}

## AGENTS.md (alternative universelle)

Si on veut une doc agnostique du modèle (Claude, GPT, Gemini, etc.), créer `AGENTS.md` à la racine avec le même contenu que `CLAUDE.md` mais sans markers spécifiques Claude. Certains agents lisent les deux ; certains uniquement leur fichier dédié.

## ADR (Architecture Decision Records)

### Format adopté

**{MICHAEL_NYGARD / MADR / AUTRE}**

### Structure d'un ADR

```markdown
# ADR-{NUM} — {Titre court}

> Date : {DATE}
> Statut : Proposé / Accepté / Rejeté / Remplacé par ADR-{X}
> Décideurs : {NOMS}

## Contexte

{Quel problème on résout ? Quelles contraintes ?}

## Décision

{Ce qu'on décide}

## Alternatives considérées

{Ce qu'on a écarté et pourquoi}

## Conséquences

{Bonnes et mauvaises, à court et long terme}
```

### Numérotation

- Format : `0001-`, `0002-`, etc. (4 chiffres, padding zéro)
- Slug : kebab-case explicite ({ex. `0001-choose-typescript-for-backend.md`})

### Cycle de vie

| Statut | Signification |
|--------|---------------|
| Proposé | En discussion, pas encore validé |
| Accepté | Validé, en vigueur |
| Rejeté | Discuté mais non retenu |
| Remplacé | Une nouvelle ADR a pris le relais |

### Quand créer un ADR

- Choix de stack majeur
- Choix d'archi structurant (monolithe vs micro-services, REST vs GraphQL…)
- Adoption d'un standard (auth, RGPD, sécurité)
- Décision contre-intuitive qu'il faudra justifier dans 6 mois

## README par package (monorepo)

Chaque package contient un `README.md` avec :

```markdown
# {Nom du package}

{1-2 phrases sur le rôle du package}

## Installation

{Si applicable}

## Usage

```{LANG}
{Exemple minimal}
```

## API publique

{Liste des exports principaux}

## Dépendances clés

{Liste avec versions et justification}

## Tests

{Commande, coverage cible}
```

## .cursorrules (si Cursor utilisé)

À la racine, `.cursorrules` contient les règles que Cursor injecte dans chaque prompt. Format Markdown ou texte.

Doit reprendre les conventions critiques de `CLAUDE.md` (anti-patterns, style code, sécurité).

## Artefacts vivants vs morts

| Document | Type | Mise à jour |
|----------|------|-------------|
| `CLAUDE.md` / `AGENTS.md` | Vivant | À chaque décision structurante |
| `README.md` racine | Vivant | À chaque changement significatif |
| `CONTRIBUTING.md` | Vivant | Quand les conventions changent |
| ADRs | **Mort une fois acceptés** | Nouveau ADR si la décision change |
| Runbooks ops | Vivant | Après chaque incident traité |
| Patterns | Vivant | Quand un nouveau pattern émerge |
| `work/` (livrables phases) | Mort une fois validé | Nouvelle version explicite |

## Maintenance

- **Audit trimestriel** : tous les 3 mois, relire `CLAUDE.md` et `AGENTS.md` pour s'assurer qu'ils reflètent la réalité du projet
- **Pull request "doc IA"** : pour toute évolution structurante, créer une PR dédiée à la mise à jour de la doc IA (la mention dans le code seul ne suffit pas)
- **Test d'efficacité** : périodiquement, demander à un agent IA "explique-moi le projet en utilisant CLAUDE.md" et vérifier la précision

## Références

- [Anthropic — Claude Code best practices](https://docs.claude.com/en/docs/claude-code)
- [Michael Nygard — Documenting Architecture Decisions](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions)
- [MADR template](https://adr.github.io/madr/)
- [Conventional Commits](https://www.conventionalcommits.org)
- {AUTRE_REFERENCE}
