---
name: env-example
description: Template de gestion des secrets et variables d'environnement (.env.example, rotation, environnements)
---

# Gestion des secrets & variables d'environnement — {NOM_DU_PROJET}

> Date : {DATE}
> Statut : ⏳ Proposé / ✅ Validé

> ⚠️ **Aucun secret en clair dans ce document.** Uniquement les noms de variables, leur format attendu, leur usage, et la procédure pour les récupérer / les rotater.

## Principes de gestion des secrets

1. **Jamais commiter de secret** — `.env` et tous les fichiers contenant des valeurs réelles sont gitignored
2. **`.env.example` toujours à jour** — chaque nouvelle variable doit y être ajoutée dans la même PR que son usage
3. **Différenciation par environnement** — chaque environnement (dev/staging/prod) a ses propres valeurs
4. **Rotation périodique** — voir section "Rotation"
5. **Procédure de compromission** — voir section "En cas de compromission"
6. **Aucune lecture inutile** — un service ne lit que les variables dont il a besoin (principe du moindre privilège)

## Outils

| Contexte | Outil retenu | Justification |
|----------|--------------|---------------|
| Local dev | `.env` + `.env.example` (gitignored) | Standard simple |
| Stockage centralisé secrets | {DOTENV_VAULT / 1PASSWORD / VAULT / SOPS / DOPPLER / INFISICAL} | {RAISON} |
| Secrets CI | {GITHUB_ACTIONS_SECRETS / GITLAB_CI_VARIABLES} | Natif plateforme CI |
| Secrets production | {COOLIFY_ENV / KUBERNETES_SECRETS / AWS_SECRETS_MANAGER / VAULT} | Aligné avec [[adr-hebergement]] |
| Chiffrement at-rest | {ACTIVÉ_NATIVEMENT_PAR_FOURNISSEUR / SOPS_AGE / AUTRE} | — |

## Liste exhaustive des variables d'environnement

### Variables backend

| Variable | Format | Usage | Sensible | Requise par env |
|----------|--------|-------|----------|-----------------|
| `NODE_ENV` | `development` / `staging` / `production` | Détection env | ❌ | tous |
| `PORT` | nombre | Port d'écoute | ❌ | tous |
| `DATABASE_URL` | `postgresql://...` | Connexion DB | 🔴 | tous |
| `JWT_SECRET` | string 256 bits | Signature JWT | 🔴 | tous |
| `{API_KEY_1}` | string | Accès {SERVICE_1} | 🔴 | tous |

### Variables front / extension

| Variable | Format | Usage | Sensible | Requise par env |
|----------|--------|-------|----------|-----------------|
| `VITE_API_URL` | URL | Endpoint backend | ❌ | tous |
| `VITE_PLAUSIBLE_DOMAIN` | string | Domaine analytics | ❌ | prod uniquement |

> ⚠️ **Variables exposées au client** (`VITE_*`, `NEXT_PUBLIC_*`, `REACT_APP_*`) sont **visibles publiquement** dans le bundle compilé — n'y mettre **jamais** de secret.

### Variables CI/CD uniquement

| Variable | Usage | Lieu |
|----------|-------|------|
| `{CI_SECRET_1}` | {USAGE} | {LIEU_CI} |

## Différenciation par environnement

| Variable | Dev local | Staging | Production |
|----------|-----------|---------|-----------|
| `DATABASE_URL` | `postgresql://localhost:5432/{DB}_dev` | DB managed staging | DB managed prod |
| `{API_KEY_1}` | Compte sandbox | Compte sandbox | Compte production |
| `LOG_LEVEL` | `debug` | `info` | `warn` |

## Procédure d'ajout d'une nouvelle variable

1. Ajouter dans `.env.example` avec valeur factice et commentaire explicatif
2. Ajouter dans ce document (`env-example.md`) avec format, usage, sensibilité
3. Configurer la valeur réelle dans **{LIEU_CENTRAL_SECRETS}** pour chaque environnement
4. Ajouter dans secrets CI si nécessaire ({LIEU_CI})
5. Communiquer aux contributeurs dans le canal {CANAL}

## Procédure de rotation

| Type de secret | Fréquence rotation | Procédure |
|----------------|--------------------|-----------|
| `JWT_SECRET` | Annuel ou sur incident | Rolling restart avec ancien + nouveau acceptés pendant 24h |
| API keys tierces | Selon politique fournisseur | Régénérer côté fournisseur, mettre à jour dans {LIEU} |
| Database passwords | 6-12 mois ou sur incident | Outil natif fournisseur, downtime min |

## En cas de compromission d'un secret

**Procédure d'urgence à exécuter dans l'ordre :**

1. **Révoquer immédiatement** le secret compromis côté fournisseur
2. **Générer un nouveau secret**
3. **Mettre à jour** dans {LIEU_CENTRAL_SECRETS} (toutes les valeurs concernées)
4. **Redéployer** les services concernés
5. **Auditer les logs** pour vérifier si le secret a été utilisé entre la compromission et la révocation
6. **Notifier** {DESTINATAIRES} (équipe, DPO si données perso impliquées, utilisateurs si requis par la loi)
7. **Documenter** l'incident dans `docs/security-incidents/`

## Audit

- **Audit régulier** : tous les {FREQUENCE}, vérifier que :
  - `.env.example` est à jour
  - Aucun secret n'a fuité dans le code (outil : `gitleaks`, `trufflehog`)
  - Les rotations dues sont faites
- **Outil d'audit automatique** : {OUTIL} configuré sur {EVENEMENT}

## Format `.env.example` recommandé

Le fichier `.env.example` à la racine doit ressembler à :

```bash
# ============================================
# {NOM_DU_PROJET} — Variables d'environnement
# ============================================
# Copier ce fichier en .env et remplir les valeurs.
# .env est gitignored — NE JAMAIS le commiter.

# --- Environnement ---
NODE_ENV=development
PORT=3000

# --- Base de données ---
DATABASE_URL=postgresql://user:password@localhost:5432/{DB_NAME}_dev

# --- Auth ---
JWT_SECRET=  # 256 bits aléatoires (générer avec `openssl rand -hex 32`)

# --- Services tiers ---
# {SERVICE_1} — récupérer la clé sur {URL_DASHBOARD}
{API_KEY_1}=

# --- Frontend (exposé bundle) ---
# Ces variables sont visibles publiquement, ne pas y mettre de secret
VITE_API_URL=http://localhost:3000

# ... (autres variables)
```

## Références

- [12-factor app — Config](https://12factor.net/config)
- [OWASP — Secrets Management Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Secrets_Management_Cheat_Sheet.html)
- {AUTRE_REFERENCE}
