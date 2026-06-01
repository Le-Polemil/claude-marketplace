---
name: specs-seo
description: Template de spécifications SEO (mots-clés, structure URL, technique, contenu)
---

# Spécifications SEO — {NOM_DU_PROJET}

> Date : {DATE}
> Statut : ⏳ Proposé / ✅ Validé
> Périmètre : {URL_OU_SECTION_DU_PROJET_VISEE_PAR_LE_SEO}

## Objectifs SEO

| KPI | Cible | Échéance |
|-----|-------|----------|
| Trafic organique mensuel | {N_VISITES} | {DATE} |
| Position moyenne mots-clés cibles | {POSITION} | {DATE} |
| Conversions depuis l'organique | {N_CONVERSIONS} | {DATE} |
| Core Web Vitals (LCP / INP / CLS) | {SEUILS} | {DATE} |
| Couverture indexation | 100 % des pages utiles indexées | continu |

## Recherche de mots-clés

### Mots-clés principaux (head)

| Mot-clé | Volume mensuel | Difficulté | Intention | Priorité |
|---------|----------------|------------|-----------|----------|
| {MC_1} | {VOL} | {DIFF} | {INFO/COM/NAV/TRANS} | Haute |

### Mots-clés longue traîne

| Mot-clé | Volume | Intention | Page cible |
|---------|--------|-----------|-----------|
| {MC_LONG_1} | {VOL} | {INTENTION} | {URL_OU_TYPE_PAGE} |

### Concurrents organiques observés

| Concurrent | Pages fortes | Mots-clés communs | Stratégie observée |
|------------|--------------|-------------------|--------------------|
| {CONC_1} | {PAGES} | {MC} | {STRATEGIE} |

## Structure d'URL & arborescence

### Règles d'URL

- Format : `{domaine}/{section}/{slug}`
- Slugs : minuscules, séparés par tirets, sans accents, sans stop-words
- Pas d'extension `.html` ni de paramètres
- Pas de profondeur > 3 niveaux

### Arborescence cible

```
{domaine}/
├── /                        # Home
├── /produit/                # Pages produit
├── /tarifs/                 # Pricing
├── /blog/                   # Blog
│   └── /blog/{slug}/        # Article
├── /a-propos/               # About
└── /contact/                # Contact
```

### Maillage interne

- Chaque page importante reçoit au moins {N} liens internes
- Texte d'ancre descriptif (pas "cliquez ici")
- Breadcrumb sur toutes les pages > niveau 1

## Technique SEO

### Rendu

- **Stratégie** : SSR / SSG / SPA / hybride — choix : {CHOIX}
- Raison : {JUSTIFICATION}
- Compatibilité bots : crawlable sans JS

### Performance (Core Web Vitals)

| Métrique | Seuil "Good" Google | Cible projet |
|----------|--------------------|--------------|
| LCP | < 2.5 s | {CIBLE} |
| INP | < 200 ms | {CIBLE} |
| CLS | < 0.1 | {CIBLE} |
| TTFB | < 800 ms | {CIBLE} |

### Balises techniques obligatoires

- `<title>` unique par page, 50-60 caractères
- `<meta name="description">` 150-160 caractères
- `<link rel="canonical">` sur chaque page
- Open Graph (`og:title`, `og:description`, `og:image`, `og:type`)
- Twitter Card
- Schema.org structured data (`Organization`, `Product`, `Article`, `FAQ`, `BreadcrumbList` selon page)
- `<link rel="alternate" hreflang>` si i18n
- `<html lang>` correctement set
- Robots meta selon visibilité souhaitée

### Fichiers techniques

- `robots.txt` : règles de crawl, lien sitemap
- `sitemap.xml` : auto-généré, soumis à Google Search Console + Bing Webmaster
- `humans.txt` (optionnel)

### HTTPS & sécurité

- HTTPS obligatoire (redirect 301 HTTP → HTTPS)
- HSTS activé
- Pas de mixed content

### International / i18n

- Stratégie : sous-domaine / sous-répertoire / domaine ccTLD : **{CHOIX}**
- `hreflang` rigoureusement configuré entre versions linguistiques

## Contenu

### Stratégie éditoriale

- Types de contenus : {LISTE}
- Cadence de publication : {CADENCE}
- Voix : voir [[charte-editoriale]]

### Templates de contenu

#### Page d'accueil

- H1 unique, contenant le mot-clé principal
- Pitch en < 25 mots dans les 100 premiers caractères
- 3-5 sections claires (proposition de valeur, preuve, CTA)

#### Page produit / feature

- H1 = nom de la feature
- Description (problème résolu, mode d'emploi, bénéfices)
- Visuel / démo
- CTA clair

#### Article de blog

- H1 = titre orienté lecteur + mot-clé
- Sommaire pour les articles > 1500 mots
- Mise à jour datée
- Schema `Article`

#### Page FAQ

- Schema `FAQPage` pour rich results
- Questions formulées comme l'utilisateur les pose
- Réponses concises < 300 mots

## Indexation & exclusions

| Page / section | À indexer | À crawler | Raison |
|----------------|-----------|-----------|--------|
| Pages produit | ✅ | ✅ | Cible SEO |
| Pages légales | ✅ | ✅ | Confiance |
| Page connexion | ❌ (`noindex`) | ✅ | Pas de valeur SEO |
| Espace utilisateur connecté | ❌ (`noindex`) | ❌ (`Disallow` robots.txt) | Données perso |

## Plan d'action SEO

### Phase de lancement

- [ ] Soumettre `sitemap.xml` à Google Search Console + Bing Webmaster
- [ ] Configurer le suivi (GA/GSC/Plausible+Search Console)
- [ ] Vérifier que toutes les pages produit ont title/description optimisés
- [ ] Audit Lighthouse + PageSpeed Insights ≥ 90 partout

### Phase de croissance (3-6 mois)

- [ ] Création de contenu blog ciblé sur longue traîne
- [ ] Backlinks via partenariats / mentions presse
- [ ] Optimisation continue selon données GSC

### Suivi

| Outil | Usage |
|-------|-------|
| Google Search Console | Indexation, requêtes, performance |
| Plausible / Matomo / Fathom | Analytics respectueux RGPD |
| Lighthouse CI | Performance + SEO automatique |
| Ahrefs / Semrush (optionnel) | Recherche mots-clés, suivi positions, audit techniques |

## Références

- [Google Search Central — SEO Starter Guide](https://developers.google.com/search/docs/fundamentals/seo-starter-guide)
- [Schema.org](https://schema.org/)
- [Core Web Vitals](https://web.dev/vitals/)
