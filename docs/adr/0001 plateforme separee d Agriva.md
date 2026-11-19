# ADR-0001 — Fieldproof est une plateforme séparée d'Agriva, construite par copie sélective

Statut : Accepté — 19/11/2026

## Contexte

Après la réunion PAMECAS, le besoin exprimé (collecte terrain + envoi de paquets à un prêteur qui ne travaille pas dans la plateforme, et suivi satellite) diffère du modèle Agriva, où le prêteur traite le dossier de crédit dans l'application office. Agriva continue d'être développé tel quel comme produit complet.

## Décision

- Fieldproof a son propre dépôt GitHub privé, son propre dossier « 6. Fieldproof » et son propre projet Supabase. Aucune base partagée avec Agriva.
- Le code utile d'Agriva est copié module par module, uniquement quand le glossaire le demande. Chaque copie est tracée dans `PROVENANCE.md` (chemin source, commit Agriva, date, modifications). Le code copié appartient à Fieldproof ; aucune synchronisation automatique dans un sens ou dans l'autre.
- Les migrations repartent de 0000.
- Candidats à copier : socle core (organisations, rôles, RLS, bac à sable, événements), identity (client/producteur, exploitation, parcelle PostGIS), harnais de tests, générateur de contrats, app terrain Flutter (hors ligne, GPS, photos), adaptateurs satellite (ADR-009 Agriva). Ne pas copier : credit, commerce, assets, registry.
- Quand un concept est identique, le terme Agriva est conservé, pour qu'une fusion future soit un rapprochement et non une réinterprétation.

## Alternatives écartées

- Bâtir dans Agriva : couple un client bancaire (données sensibles, cadence PAMECAS) à un produit plus large encore en construction.
- Forker le dépôt Agriva : hérite de 33 migrations et de schémas inutiles.
- Monorepo à paquets partagés : couplage de versions entre deux produits aux rythmes différents.

## Conséquences

Une amélioration d'un module copié doit être reportée manuellement dans l'autre produit, si on le juge utile.
