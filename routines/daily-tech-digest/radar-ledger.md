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
- 2026-09-03 — Agent Skills — Trial
- 2026-09-03 — OpenSpec — Assess
- 2026-09-03 — Ralph loop — Assess

Statut : en cours

## CNCF Technology Landscape Radar — Q3 2025 (paru le 2025-11-11)

- 2026-08-31 — Model Context Protocol (MCP) — Adopt
- 2026-08-31 — Llama Stack — Adopt
- 2026-08-31 — kagent — Assess
- 2026-09-04 — NVIDIA Triton — Adopt
- 2026-09-04 — Airflow — Adopt
- 2026-09-04 — BentoML — Adopt (inférence) / Trial (orchestration)

Statut : en cours

## InfoQ AI, ML and Data Engineering Trends Report — édition 2025 (paru le 2025-09-24)

- 2026-09-01 — AI Agents — Innovators
- 2026-09-01 — Retrieval Augmented Generation (RAG) — Early Adopters
- 2026-09-01 — Model Context Protocol (MCP) — Innovators
- 2026-09-05 — AI DevOps — Innovators
- 2026-09-05 — Reasoning Models — Innovators
- 2026-09-05 — Vector Databases — Early Majority

Statut : en cours

## Gartner Hype Cycle for Agentic AI — édition inaugurale (paru le 2026-04-02)

- 2026-09-02 — AI Agent Development Platforms — Peak of Inflated Expectations
- 2026-09-02 — Model Context Protocol (MCP) — Peak of Inflated Expectations

Statut : en cours
