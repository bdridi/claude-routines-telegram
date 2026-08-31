# Registre d'exploitation des radars

Mémoire longue de la routine. La déduplication ordinaire ne regarde que les 7 derniers digests ;
ce fichier couvre l'exploitation d'un radar sur plusieurs mois.

**Tenu par l'agent**, chaque lundi, dans le même commit que le digest du jour. Le protocole est
défini dans `sources.md` (branche `main`), section *Radars & rapports de tendances*.

Une ligne par entrée traitée : la date du digest où elle est parue, le nom de l'entrée, et sa
position dans le radar.

---

## Format d'une section

```
## <Nom du radar> — <édition> (paru le AAAA-MM-JJ)

- 2026-09-07 — Nom de l'entrée — Adopt
- 2026-09-07 — Autre entrée — Hold
- 2026-09-14 — Encore une — Trial

Statut : en cours | épuisé le AAAA-MM-JJ
```

---

## Éditions

## ThoughtWorks Technology Radar — Vol 34 (paru en avril 2026)

- 2026-08-30 — MCP par défaut — Hold
- 2026-08-30 — Instructions partagées et versionnées pour les équipes — Adopt
- 2026-08-30 — Instructions d'agent qui s'accumulent — Hold

Statut : en cours

## CNCF Technology Landscape Radar — Q3 2025 (paru le 2025-11-11)

- 2026-08-31 — Model Context Protocol (MCP) — Adopt
- 2026-08-31 — Llama Stack — Adopt
- 2026-08-31 — kagent — Assess

Statut : en cours
