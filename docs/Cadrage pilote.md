# Fieldproof — Cadrage du pilote PAMECAS

Validé le 19/11/2026.

## Périmètre

- Originateur : IBRIZ — 4 agents terrain, 2 par zone.
- Prêteur : PAMECAS — caisses des zones Niayes et Ziguinchor (caisses exactes à confirmer avec PAMECAS).
- Volume visé : 50 à 100 clients personnes physiques.
- Démarrage : immédiat.

## Tranche 1 — pilote

- Module Dossier complet : collecte hors ligne, consentement, complétude, vérification superviseur, paquets ouverture de compte + demande de crédit, envoi par lien sécurisé, retours du prêteur.
- Module Watch : analyse rétroactive des parcelles, intégrée à la fiche Fieldproof.
- Surfaces : app mobile Flutter (agent), web (superviseur), pages du lien sécurisé (prêteur). Supabase dédié.

## Tranche 2 — après les premiers décaissements

- Suivi continu, alertes vérifiées, rapport de portefeuille mensuel.

## Plus tard

- Groupements, écran d'administration des prêteurs, API / import vers le système du prêteur, portail lecture seule prêteur.

## Prérequis avant la première collecte

- Formulaires officiels PAMECAS (adhésion, demande de crédit).
- Identification du système bancaire central de PAMECAS (pour l'annexe structurée).
- Liste des caisses pilotes, leurs zones et leurs adresses mail, plus l'adresse centrale.
- Déclaration à la CDP et texte de consentement validé par un juriste.
- Nom : vérification du domaine et de la marque (OAPI) « Fieldproof ».

## Point d'attention

Ziguinchor (Casamance) est très nuageux en saison des pluies : l'optique Sentinel-2 y sera souvent aveugle de juin à octobre. Prévoir un adaptateur radar Sentinel-1, qui voit à travers les nuages, pour le suivi en hivernage.
