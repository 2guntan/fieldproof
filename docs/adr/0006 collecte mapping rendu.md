# ADR-0006 — Documents : collecte canonique, mapping par prêteur, rendu par adaptateur

Statut : Accepté — 19/11/2026

## Décision
Trois couches séparées :
1. Collecte : un seul modèle de données (le dossier client) = socle fixe codé (identité, adresse, exploitation, parcelle, besoin, consentement) + champs complémentaires déclarés dans la configuration prêteur, affichés automatiquement par l'app.
2. Mapping : dans la configuration prêteur, chaque champ du formulaire du prêteur est relié à une donnée du dossier, avec ses transformations (format de date, majuscules, case cochée selon une valeur…). La complétude se déduit du mapping : un champ obligatoire relié à une donnée vide bloque la soumission.
3. Rendu : adaptateur déclaré par modèle — Carbone pour les modèles Word et la fiche Fieldproof, pdf-lib pour les PDF à champs. L'annexe structurée et la future API sont un autre rendu du même mapping.

## Réserves
- Vérifier la licence Carbone pour un usage commercial auto-hébergé ; sinon docxtemplater + LibreOffice derrière la même interface.
- Demander les formulaires du prêteur en Word ou PDF remplissable, pas en scan.

## Alternatives écartées
- Formulaires de collecte entièrement codés en dur : chaque prêteur exige une mise à jour de l'app.
- Générateur de formulaires générique : projet en soi, données inexploitables.
- Redessiner les formulaires du prêteur en HTML : le prêteur doit valider une copie au lieu de son original.
