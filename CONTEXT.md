# Fieldproof — Glossaire (CONTEXT.md)

Version 0.1 — 19/11/2026 — issue de la séance de cadrage post-réunion PAMECAS.

Fieldproof est une plateforme qui collecte sur le terrain les données d'un client, génère les documents d'ouverture de compte et de demande de crédit au format d'un prêteur, les lui envoie, et apporte la preuve par satellite que l'exploitation existe et est cultivée — avant et pendant le crédit.

Quand un concept existe aussi dans Agriva, Fieldproof garde le même terme (voir ADR-0001).

---

## Acteurs

**Originateur** : organisation dont les agents collectent les dossiers sur le terrain et les envoient au prêteur. Au pilote : IBRIZ.
_Éviter_ : partenaire, apporteur.

**Prêteur** : organisation qui reçoit les paquets, ouvre le compte et décide du crédit. Il n'a pas de compte utilisateur sur Fieldproof au départ ; il interagit par le lien sécurisé. Au pilote : PAMECAS.
_Éviter_ : banque (seul), IMF partenaire, client (le client est le producteur).

**Caisse** : unité locale du prêteur, destinataire principale d'un envoi. Déduite de la localité du client, corrigeable par le superviseur.
_Éviter_ : agence.

**Adresse centrale** : adresse du siège du prêteur, toujours en copie des envois.

**Agent terrain** : agent de l'originateur qui collecte le dossier client sur l'application mobile hors ligne.

**Superviseur** : agent de l'originateur qui vérifie un dossier soumis, l'envoie ou le renvoie avec un motif, et trie les alertes satellite.

## Module Dossier

**Client** : personne physique ou groupement (GIE, coopérative, association) qui demande une ouverture de compte et/ou un crédit. Un groupement a des membres (eux-mêmes clients personnes physiques) et un représentant. Pilote : personnes physiques uniquement.
_Éviter_ : producteur pour désigner le titulaire du dossier (un client n'est pas forcément producteur), bénéficiaire.

**Dossier client** : ensemble des données et pièces d'un client (identité, justificatifs, exploitation, parcelles, besoin), saisi une seule fois, à partir duquel les paquets sont générés.
_Éviter_ : dossier (seul), fiche client.

**Paquet** : ensemble de documents généré depuis un dossier client pour un prêteur, et envoyé en une fois. Contient : les formulaires officiels du prêteur pré-remplis, la fiche Fieldproof, l'annexe structurée, les pièces scannées.

**Paquet d'ouverture de compte** : paquet destiné à rendre le client titulaire d'un compte (sociétaire) chez le prêteur.

**Paquet de demande de crédit** : paquet destiné à la demande de crédit. Il ne peut être envoyé que si le client a un numéro de compte chez le prêteur, ou si le paquet d'ouverture de compte part dans le même envoi.

**Fiche Fieldproof** : document d'une à deux pages propre à Fieldproof : carte de la parcelle, photos géolocalisées, exploitation, analyse satellite rétroactive.

**Annexe structurée** : fichier de données (Excel ou JSON) reprenant champ par champ les données attendues par le système du prêteur. Son contenu est celui de la future API.

**Complétude** : contrôle automatique (pièces obligatoires, lisibilité, géométrie, champs des formulaires, consentement) qui bloque la soumission tant qu'il échoue.
_Éviter_ : readiness (terme Agriva, même idée — à aligner si fusion).

**Soumission** : action de l'agent terrain qui passe un dossier complet au superviseur.

**Vérification** : examen du superviseur, qui aboutit à un envoi ou à un renvoi motivé à l'agent.

**Envoi** : action du superviseur qui expédie un ou deux paquets à la caisse (adresse centrale en copie) par un lien sécurisé.
_Éviter_ : transmission (terme Agriva réservé à la création d'un dossier de crédit chez un prêteur qui travaille dans la plateforme).

**Lien sécurisé** : lien à durée limitée, journalisé et révocable, sans compte à créer, par lequel le prêteur télécharge un paquet et déclare son statut.

**Retour du prêteur** : statut déclaré par le prêteur sur un paquet : Reçu → Intégré (avec sa référence : numéro de compte ou de dossier) | Rejeté (avec motif). Le numéro de compte reçu débloque le paquet de demande de crédit.

**Consentement** : accord électronique (OTP par SMS ou signature à l'écran), horodaté, donné par finalité : (1) constitution et envoi au prêteur choisi, (2) suivi satellite pendant le crédit, (3) facultatif, usage anonymisé. Les finalités 1 et 2 sont des pièces bloquantes de la complétude. Un retrait arrête le suivi et est notifié au prêteur.

## Module Watch (suivi satellite)

**Parcelle** : surface cultivée tracée au GPS par l'agent terrain, rattachée à une exploitation du client.

**Analyse rétroactive** : analyse des 2 à 3 dernières saisons d'une parcelle à partir des archives satellite, réalisée dès la collecte et intégrée à la fiche Fieldproof (cultivée ou non, cycle de végétation, surface confirmée).

**Suivi** : surveillance continue d'une parcelle pendant la durée du crédit.

**Alerte** : signal satellite sur une parcelle suivie (pas de semis à date, chute de végétation, inondation…). Elle va d'abord au superviseur.

**Alerte confirmée** : alerte vérifiée par l'originateur (appel ou visite), envoyée au prêteur par lien sécurisé avec le constat terrain.
_Éviter_ : envoyer une alerte brute au prêteur.

**Rapport de portefeuille** : rapport mensuel envoyé à la caisse et au siège : état (vert / orange / rouge) et évolution de chaque ferme financée.

## Configuration

**Configuration prêteur** : ensemble des paramètres propres à un prêteur : modèles de formulaires, pièces obligatoires, caisses et zones, adresses de réception, format de l'annexe. Un nouveau prêteur se branche par configuration, sans code. Au pilote, la configuration est faite par IBRIZ, sans écran d'administration.
