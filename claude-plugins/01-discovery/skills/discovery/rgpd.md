---
name: rgpd
description: Template du livrable de conformité RGPD
---

# Conformité RGPD — {NOM_DU_PROJET}

> Date : {DATE}
> DPO : {NOM_DPO} — {CONTACT_DPO}

## Inventaire des traitements de données

| Traitement | Données collectées | Base légale | Durée de conservation | Destinataires |
|------------|-------------------|-------------|----------------------|---------------|
| Formulaire de contact | Nom, email, message | Consentement | 3 ans | Équipe interne |
| Création de compte | Nom, email, mot de passe | Exécution du contrat | Durée du compte + 3 ans | Équipe interne |
| Newsletter | Email | Consentement | Jusqu'au désabonnement | {OUTIL_NEWSLETTER} |
| Analytics | IP (anonymisée), navigation | Intérêt légitime | {DUREE} | {OUTIL_ANALYTICS} |
| {TRAITEMENT_N} | {DONNEES} | {BASE_LEGALE} | {DUREE} | {DESTINATAIRES} |

## Solution de consentement cookies

- **Outil choisi** : {TARTEAUCITRON/AXEPTIO/AUTRE}
- **Catégories de cookies** :
  - Strictement nécessaires (pas de consentement requis)
  - Analytics / mesure d'audience
  - Marketing / publicité (si applicable)
  - Réseaux sociaux (si applicable)

## Audit des formulaires

| Formulaire | Champs | Champs obligatoires | Consentement explicite | Lien politique de confidentialité |
|-----------|--------|--------------------|-----------------------|----------------------------------|
| Contact | {CHAMPS} | {OBLIGATOIRES} | ✅/❌ | ✅/❌ |
| Inscription | {CHAMPS} | {OBLIGATOIRES} | ✅/❌ | ✅/❌ |
| Newsletter | {CHAMPS} | {OBLIGATOIRES} | ✅/❌ | ✅/❌ |

## Droits des utilisateurs

| Droit | Implémentation prévue |
|-------|----------------------|
| Accès | {COMMENT} |
| Rectification | {COMMENT} |
| Suppression | {COMMENT} |
| Portabilité | {COMMENT} |
| Opposition | {COMMENT} |

## Mentions légales (template)

```
Éditeur du site : {RAISON_SOCIALE}
{ADRESSE}
{SIRET}
Directeur de la publication : {NOM}
Hébergeur : {NOM_HEBERGEUR} — {ADRESSE_HEBERGEUR}
```

## Politique de confidentialité (structure)

1. Identité du responsable de traitement
2. Données collectées et finalités
3. Base légale des traitements
4. Durées de conservation
5. Destinataires des données
6. Transferts hors UE (si applicable)
7. Droits des personnes
8. Cookies et traceurs
9. Contact DPO
10. Droit de réclamation auprès de la CNIL

## Hébergement et transferts

- **Hébergement UE** : {OUI/NON}
- **Sous-traitants hors UE** : {LISTE_SI_APPLICABLE}
- **Garanties** : {CLAUSES_CONTRACTUELLES_TYPES / AUTRE}

## Actions à mener

- [ ] Rédiger les mentions légales définitives
- [ ] Rédiger la politique de confidentialité complète
- [ ] Configurer la solution de consentement
- [ ] Ajouter les liens de politique de confidentialité sur tous les formulaires
- [ ] Implémenter les mécanismes de droits utilisateurs
- [ ] Vérifier la conformité de l'outil analytics
