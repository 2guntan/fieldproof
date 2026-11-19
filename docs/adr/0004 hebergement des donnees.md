# ADR-0004 — Hébergement des données : Supabase Europe pour le pilote, portable vers un hébergement local

Statut : Accepté — 19/11/2026

## Contexte
Fieldproof stocke des pièces d'identité et des données de clients d'une institution réglementée (BCEAO). Un transfert de données hors du Sénégal peut nécessiter une autorisation de la CDP. PAMECAS peut avoir une exigence interne de localisation.

## Décision
- Pilote sur un projet Supabase dédié « fieldproof », région Europe.
- Logique métier en Postgres standard (SQL, PostGIS, RLS) ; aucune dépendance propre à Supabase dans la logique métier, pour pouvoir migrer vers un hébergement au Sénégal / UEMOA.
- Avant la première collecte : demander à PAMECAS son exigence de localisation ; déclaration CDP et, si requise, demande d'autorisation de transfert (à valider par un juriste).

## Alternatives écartées
- Hébergement local dès le pilote : coût et délai d'exploitation d'un Postgres auto-géré, sans exigence confirmée.
