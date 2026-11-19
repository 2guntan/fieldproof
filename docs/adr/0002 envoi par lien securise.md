# ADR-0002 — Les paquets sont envoyés par lien sécurisé, avec boucle de retour du prêteur

Statut : Accepté — 19/11/2026

## Contexte

Le prêteur (PAMECAS) n'a pas de compte sur Fieldproof et intègre les dossiers dans son propre système. Le paquet de demande de crédit dépend du numéro de compte que seul le prêteur attribue.

## Décision

- L'envoi est un mail à la caisse du client, adresse centrale du siège en copie, contenant un lien sécurisé (durée limitée, journalisé, révocable, sans compte).
- Par ce lien, le prêteur télécharge le paquet et déclare : Reçu → Intégré (référence prêteur) | Rejeté (motif).
- Le numéro de compte déclaré débloque le paquet de demande de crédit.
- Chaque paquet contient : formulaires officiels du prêteur pré-remplis, fiche Fieldproof, annexe structurée, pièces scannées. L'annexe structurée est le contenu de la future API ; seul le canal changera.
- Repli possible : pièces jointes en plus du lien, si l'informatique du prêteur bloque les liens externes.

## Alternatives écartées

- Pièces jointes seules : pièces d'identité non contrôlées en circulation, aucune trace d'accès, aucun retour automatique.
- Comptes utilisateurs pour le prêteur dès le pilote : friction d'adoption ; reporté (portail en lecture seule plus tard).
