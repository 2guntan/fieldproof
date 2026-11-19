# ADR-0003 — Un prêteur est une configuration, pas du code

Statut : Accepté — 19/11/2026

## Contexte

Fieldproof doit servir PAMECAS puis d'autres prêteurs (IMF, banques). Coder en dur les formulaires et règles PAMECAS obligerait à dupliquer au deuxième client.

## Décision

Chaque prêteur est décrit par une configuration :
- modèles de formulaires (Word/PDF balisés, remplis par la plateforme) ;
- liste des pièces obligatoires (alimente la complétude) ;
- caisses et leur zone géographique (routage automatique, corrigeable) ;
- adresses de réception (caisse + adresse centrale) ;
- format de l'annexe structurée.

PAMECAS est le premier prêteur configuré. Au pilote, la configuration est saisie par IBRIZ, sans écran d'administration ; l'écran viendra quand au moins deux prêteurs montreront ce qui varie vraiment.

## Alternatives écartées

- Spécifique PAMECAS puis généralisation : coût de refonte élevé, alors que le moteur de remplissage de formulaires est nécessaire de toute façon.
