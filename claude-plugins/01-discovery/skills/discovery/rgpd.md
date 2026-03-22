---
name: rgpd
description: Template du livrable de conformité RGPD
required_sections:
  - Inventaire des traitements de données
  - Solution de consentement cookies
  - Audit des formulaires
  - Droits des utilisateurs
  - Mentions légales (template)
  - Politique de confidentialité (structure)
  - Hébergement et transferts
  - Actions à mener
---

# Conformité RGPD — {NOM_DU_PROJET}

> Date : {DATE}
> DPO : {NOM_COMPLET} — {EMAIL_OU_CONTACT}

## Inventaire des traitements de données

| Traitement | Données collectées | Base légale | Durée de conservation | Destinataires |
|------------|-------------------|-------------|----------------------|---------------|
| {TRAITEMENT} | {DONNEES_PRECISES} | Consentement / Contrat / Intérêt légitime / Obligation légale | {DUREE_PRECISE} | {DESTINATAIRES} |

## Solution de consentement cookies

- **Outil choisi** : {NOM_OUTIL} — {JUSTIFICATION_DU_CHOIX}
- **Catégories de cookies** :
  - Strictement nécessaires (pas de consentement requis) : {LISTE}
  - Analytics / mesure d'audience : {LISTE}
  - Marketing / publicité : {LISTE_OU_NA}
  - Réseaux sociaux : {LISTE_OU_NA}

## Audit des formulaires

> Doit correspondre aux formulaires décrits dans specs-fonctionnelles.md.

| Formulaire | Champs | Champs obligatoires | Consentement explicite | Lien politique confidentialité |
|-----------|--------|--------------------|-----------------------|-------------------------------|
| {FORMULAIRE} | {LISTE_CHAMPS} | {LISTE_OBLIGATOIRES} | ✅ / ❌ | ✅ / ❌ |

## Droits des utilisateurs

| Droit | Implémentation prévue |
|-------|----------------------|
| Accès | {COMMENT_CONCRETEMENT} |
| Rectification | {COMMENT} |
| Suppression | {COMMENT} |
| Portabilité | {COMMENT} |
| Opposition | {COMMENT} |

## Mentions légales (template)

```
Éditeur du site : {RAISON_SOCIALE}
Adresse : {ADRESSE_COMPLETE}
SIRET : {NUMERO_SIRET}
Directeur de la publication : {NOM_COMPLET}
Contact : {EMAIL}

Hébergeur : {NOM_HEBERGEUR}
Adresse : {ADRESSE_HEBERGEUR}
Téléphone : {TEL_HEBERGEUR}
```

## Politique de confidentialité (structure)

> Les 10 points obligatoires à couvrir dans la politique de confidentialité :

1. **Identité du responsable de traitement** : {QUI}
2. **Données collectées et finalités** : {RESUME}
3. **Base légale des traitements** : {RESUME}
4. **Durées de conservation** : {RESUME}
5. **Destinataires des données** : {RESUME}
6. **Transferts hors UE** : {OUI_DETAILS / NON}
7. **Droits des personnes** : {COMMENT_EXERCER}
8. **Cookies et traceurs** : {RENVOI_VERS_SOLUTION_CONSENTEMENT}
9. **Contact DPO** : {EMAIL_DPO}
10. **Droit de réclamation** : auprès de la CNIL — https://www.cnil.fr

## Hébergement et transferts

- **Hébergement UE** : {OUI/NON} — {NOM_HEBERGEUR}, {PAYS}
- **Sous-traitants hors UE** :

| Sous-traitant | Pays | Service | Garanties |
|---------------|------|---------|-----------|
| {NOM} | {PAYS} | {SERVICE} | Clauses contractuelles types / Décision d'adéquation / Autre |

## Actions à mener

- [ ] Rédiger les mentions légales définitives
- [ ] Rédiger la politique de confidentialité complète
- [ ] Configurer {OUTIL_CONSENTEMENT}
- [ ] Ajouter les liens de politique de confidentialité sur tous les formulaires
- [ ] Implémenter les mécanismes de droits utilisateurs
- [ ] Vérifier la conformité de {OUTIL_ANALYTICS}
- [ ] Documenter les clauses contractuelles avec les sous-traitants hors UE
