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
- 2026-09-07 — Coding agent swarms — Hold
- 2026-09-07 — Ignoring durability in agent workflows — Hold
- 2026-09-07 — Role-based contextual isolation in RAG — Assess
- 2026-09-11 — Context engineering — Adopt
- 2026-09-11 — Zero trust architecture — Adopt
- 2026-09-11 — Coding throughput as a measure of productivity — Hold
- 2026-09-15 — Sandboxed execution for coding agents — Trial
- 2026-09-15 — Feedback sensors for coding agents — Trial
- 2026-09-15 — AI-accelerated shadow IT — Caution
- 2026-09-18 — Codebase cognitive debt — Caution
- 2026-09-18 — Feedback flywheel — Assess
- 2026-09-18 — Team of coding agents — Assess
- 2026-09-21 — Structured output from LLMs — Adopt
- 2026-09-21 — Code intelligence as agentic tooling — Assess
- 2026-09-21 — Measuring collaboration quality with coding agents — Assess

Statut : en cours

## CNCF Technology Landscape Radar — Q3 2025 (paru le 2025-11-11)

- 2026-08-31 — Model Context Protocol (MCP) — Adopt
- 2026-08-31 — Llama Stack — Adopt
- 2026-08-31 — kagent — Assess
- 2026-09-04 — NVIDIA Triton — Adopt
- 2026-09-04 — Airflow — Adopt
- 2026-09-04 — BentoML — Adopt (inférence) / Trial (orchestration)
- 2026-09-08 — Metaflow — Adopt
- 2026-09-08 — DeepSpeed — Adopt
- 2026-09-08 — Argo Workflows — Trial
- 2026-09-12 — Kubeflow — Trial
- 2026-09-12 — Seldon Core — Assess
- 2026-09-12 — Flyte — Assess
- 2026-09-16 — agentgateway — Trial
- 2026-09-16 — TensorFlow Serving — Adopt
- 2026-09-19 — Agent2Agent (A2A) — Trial
- 2026-09-19 — Adlik — Trial
- 2026-09-22 — LangChain — Hold
- 2026-09-22 — crewAI — Hold
- 2026-09-22 — Haystack — Trial

Statut : en cours

## InfoQ AI, ML and Data Engineering Trends Report — édition 2025 (paru le 2025-09-24)

- 2026-09-01 — AI Agents — Innovators
- 2026-09-01 — Retrieval Augmented Generation (RAG) — Early Adopters
- 2026-09-01 — Model Context Protocol (MCP) — Innovators
- 2026-09-05 — AI DevOps — Innovators
- 2026-09-05 — Reasoning Models — Innovators
- 2026-09-05 — Vector Databases — Early Majority
- 2026-09-09 — Physical AI — Innovators
- 2026-09-09 — Language Model Innovations — Early Adopters
- 2026-09-09 — Human Computer Interaction (HCI) — Innovators
- 2026-09-13 — Multi-modal Language Models — Innovators
- 2026-09-13 — Synthetic Data — Early Majority
- 2026-09-13 — AutoML — Early Adopters
- 2026-09-17 — MLOps — Early Majority
- 2026-09-17 — Distributed computation (Storm) — Late Majority
- 2026-09-20 — Lakehouses — Late Majority
- 2026-09-20 — Stream Processing — Late Majority

Statut : épuisé le 2026-09-20 — les 16 technologies listées par l'article source (7 Innovators,
3 Early Adopters, 3 Early Majority, 3 Late Majority) sont désormais toutes traitées. Rotation
resserrée sur les deux radars restants (ThoughtWorks, CNCF).

## Gartner Hype Cycle for Agentic AI — édition inaugurale (paru le 2026-04-02)

- 2026-09-02 — AI Agent Development Platforms — Peak of Inflated Expectations
- 2026-09-02 — Model Context Protocol (MCP) — Peak of Inflated Expectations
- 2026-09-06 — AI SOC Agents — Peak of Inflated Expectations
- 2026-09-10 — Multi-agent orchestration — Peak of Inflated Expectations
- 2026-09-10 — Autonomous coding agents — Peak of Inflated Expectations
- 2026-09-10 — Swarm intelligence — Innovation Trigger
- 2026-09-14 — AI-to-AI negotiation — Innovation Trigger
- 2026-09-14 — Neural symbolic AI agents — Innovation Trigger

Statut : épuisé le 2026-09-18 — les sources publiques accessibles (institutepm.com, xpander.ai ;
le rapport complet Gartner reste payant) ne couvrent que 13 des 27 innovations du rapport, avec
position par ring vérifiable. Les 8 ci-dessus les épuisent entièrement (Innovation Trigger et
Peak of Inflated Expectations au complet) ; les 5 restantes (First-generation AI copilots, Basic
task automation agents, Process-specific AI assistants, AI-augmented decision support, Document
AI / AI-powered search / Predictive analytics) avaient déjà été écartées les 2026-09-10 et
2026-09-14 pour position contradictoire selon les sources ou absence de lien avec agents/harness,
non re-vérifiées différemment le 2026-09-18. Rotation resserrée sur les trois radars restants.
