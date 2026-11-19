# ADR-0008 — Consentement sans SMS par défaut ; mails transactionnels sur domaine propre

Statut : Accepté — 19/11/2026

## Contexte
Le SMS a un coût par envoi ; il est le dernier recours. Les mails vers le prêteur ne doivent pas finir en spam.

## Décision
- Consentement par défaut, à coût nul : signature manuscrite à l'écran (ou trait/empreinte dessinée pour un client qui ne signe pas), horodatage, position GPS, photo du client au moment du recueil, finalités cochées séparément. Le texte est lu au client dans sa langue.
- OTP par SMS : désactivé par défaut ; activable dans la configuration d'un prêteur qui l'exige. Adaptateur remplaçable ; si activé, agrégateur local couvrant Orange, Free et Expresso.
- Mails : service d'envoi transactionnel, domaine propre, SPF/DKIM/DMARC dès le premier jour ; test réel vers une adresse PAMECAS avant le pilote.
- Chaque envoi (mail, SMS) est journalisé avec son statut de livraison, visible par le superviseur.

## Alternatives écartées
- OTP SMS systématique : coût récurrent par dossier sans exigence du prêteur.
