---
name: a11y-rules
description: Template de règles d'accessibilité pour le projet (WCAG, outils, processus, points de vigilance)
---

# Règles d'accessibilité — {NOM_DU_PROJET}

> Date : {DATE}
> Niveau WCAG cible : {A / AA / AAA}
> Référentiel applicable : {WCAG_2.X / RGAA / ADA / EAA / AUTRE}

## Engagement & cadre légal

{DESCRIPTION_DE_L_ENGAGEMENT_ET_DES_OBLIGATIONS_APPLICABLES}

| Cadre | Applicable | Échéance |
|-------|------------|----------|
| WCAG 2.1 / 2.2 niveau {X} | {OUI_NON} | {DATE} |
| RGAA (France) | {OUI_NON} | {DATE} |
| European Accessibility Act (EAA) | {OUI_NON} | 2025-06-28 |
| ADA Title III (US) | {OUI_NON} | continue |
| Autre | {OUI_NON} | {DATE} |

## Périmètre

### In scope

- {ECRAN_OU_COMPOSANT_1}
- {ECRAN_OU_COMPOSANT_2}

### Out of scope

- {ECRAN_OU_COMPOSANT_OUT_1}

## Règles transverses

### Sémantique HTML

- {REGLE_HTML_1}
- Utiliser les balises sémantiques natives avant de recourir à ARIA
- `<button>` pour les actions, `<a>` pour la navigation — jamais `<div onClick>`
- Titres `<h1>`-`<h6>` hiérarchiques sans saut de niveau
- Listes `<ul>`/`<ol>` pour toute énumération

### Contrastes & couleur

- Contraste texte normal : ≥ 4.5:1 (AA) / ≥ 7:1 (AAA)
- Contraste texte large (≥ 18pt ou 14pt gras) : ≥ 3:1 (AA) / ≥ 4.5:1 (AAA)
- Contraste UI / icônes informatives : ≥ 3:1
- **L'information ne doit jamais reposer sur la couleur seule** (ajouter icône, texte, motif)

### Navigation clavier

- Tous les contrôles interactifs accessibles au clavier (`Tab`, `Shift+Tab`, `Enter`, `Esc`, flèches selon le composant)
- Ordre de tabulation logique (suit le flux visuel)
- Focus visible (outline minimum 2px, contraste ≥ 3:1)
- `Skip to main content` en début de page sur les sites web
- Pas de "piège à clavier" (focus bloqué dans un composant)

### Lecteurs d'écran

- Toutes les images informatives ont un `alt` significatif
- Images décoratives : `alt=""` ou `aria-hidden="true"`
- Labels de formulaire associés explicitement (`<label for>` ou `aria-label`)
- Messages d'erreur annoncés via `aria-live` ou `role="alert"`
- États dynamiques annoncés (loading, success, error, expanded/collapsed)

### Animations & médias

- Animations désactivables (`prefers-reduced-motion`)
- Pas d'auto-play vidéo/audio
- Vidéos : sous-titres (AA) + transcription (AA) + audio-description (AAA si applicable)
- Pas de flash > 3 fois/seconde (risque épilepsie)

### Formulaires

- Champs obligatoires identifiés (texte + `aria-required` + visuel)
- Erreurs de validation : message clair, suggestion de correction, focus déplacé
- Regroupement logique (`<fieldset>` + `<legend>` pour les groupes thématiques)
- Saisie tolérante (autocomplete, formats multiples, pas de casse forcée sur les emails)

## Règles spécifiques par composant à risque

### Modales / dialogues

- Focus piégé dans la modale tant qu'elle est ouverte (`focus trap`)
- `Esc` ferme la modale
- Focus restauré sur l'élément déclencheur après fermeture
- Rôle `dialog` ou `alertdialog`, `aria-modal="true"`
- Titre via `aria-labelledby`

### Menus déroulants / navigation

- Navigation flèches haut/bas dans le menu
- `aria-expanded` sur le déclencheur
- Fermeture sur `Esc` ou clic extérieur
- Sous-menus annoncés explicitement

### Datepickers, autocomplete

- Saisie manuelle toujours possible (jamais imposer le widget)
- Combobox pattern WAI-ARIA respecté
- Tests manuels NVDA + VoiceOver indispensables

### Contenu dynamique

- Mise à jour annoncée via `aria-live` (politeness adaptée : `polite`/`assertive`)
- Loading states annoncés
- Notifications non bloquantes lisibles avant disparition

### Tableaux

- En-têtes (`<th>`) avec `scope="col"` / `scope="row"`
- Caption descriptive (`<caption>`)
- Pour les tableaux complexes : `headers` + `id` ou structure imbriquée évitée

## Outils d'audit

### Automatisés (CI/CD)

| Outil | Quand | Couverture |
|-------|-------|------------|
| **axe-core** (Playwright/Cypress integration) | À chaque PR | ~30-40 % des règles WCAG (issues claires) |
| **Lighthouse a11y** | Avant merge sur main | Score global a11y page par page |
| **eslint-plugin-jsx-a11y** | Commit/push hook | Patterns JSX en local dev |
| **pa11y-ci** (optionnel) | Nightly sur prod/staging | Tests parcours complets |

### Manuels (récurrence à acter)

| Outil / méthode | Fréquence | Responsable |
|----------------|-----------|-------------|
| **NVDA** sur Windows + Firefox/Chrome | Avant chaque release | {NOM} |
| **VoiceOver** sur macOS + Safari | Avant chaque release | {NOM} |
| **TalkBack** sur Android | Avant release mobile | {NOM} |
| **Navigation clavier seule** (sans souris) | Sur chaque nouvelle feature | Dev |
| **Audit RGAA / WCAG manuel complet** | Annuel ou avant lancement majeur | {AUDITEUR_INTERNE_OU_EXTERNE} |

## Processus & intégration équipe

### Workflow de dev

1. **Design** : maquettes validées sur les contrastes et les zones de focus
2. **Spécification** : Définition of Done inclut "tests a11y passants + audit manuel sur le composant"
3. **Dev** : usage des composants accessibles de la lib (Radix, React Aria, Reach UI…) avant de coder maison
4. **Review** : checklist a11y dans le template PR
5. **QA** : tests manuels NVDA/VoiceOver + clavier sur les parcours impactés
6. **Release** : suivi des bugs a11y comme des bugs prio 1

### Formation

- Onboarding équipe : {FORMATION_INITIALE}
- Veille : {RESSOURCES_RECOMMANDEES}
- Tests utilisateurs : {PROCESSUS_AVEC_UTILISATEURS_REELS}

## Tests utilisateurs réels

| Profil | Fréquence souhaitée | Mode |
|--------|---------------------|------|
| {PROFIL_1} | {FREQUENCE} | {REMOTE / EN_PERSONNE} |

## Plan de remédiation

Pour les non-conformités identifiées en cours de projet :

| Niveau | Délai max de correction |
|--------|------------------------|
| Bloquant (impossible d'utiliser) | 48 h |
| Majeur (UX dégradée) | 1 sprint |
| Mineur | Prochaine release |

## Déclaration d'accessibilité

Une déclaration d'accessibilité publique sera publiée :

- URL : `{URL_DECLARATION}`
- Mise à jour : {FREQUENCE}
- Contenu : état de conformité, dérogations, contact, voies de recours

## Références

- [WCAG 2.1 Quick Reference](https://www.w3.org/WAI/WCAG21/quickref/)
- [RGAA — référentiel](https://accessibilite.numerique.gouv.fr/)
- [WAI-ARIA Authoring Practices](https://www.w3.org/WAI/ARIA/apg/)
- [Inclusive Components — Heydon Pickering](https://inclusive-components.design/)
