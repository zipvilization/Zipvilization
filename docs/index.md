---
layout: default
title: Documentation
nav_order: 2
has_children: true
permalink: /docs/
description: Canonical documentation for Zipvilization, including its vision, project foundations, Solum contract, interpretation tools, world model, visual layer, chapters and technical translations.
---

# Documentation

This is the canonical documentation of Zipvilization.

The repository is the project's public truth layer. It defines the rules, constraints, interpretations and technical relationships that make Zipvilization auditable by both humans and AI systems.

The documentation is organized by responsibility. Each section describes a distinct layer of the system and links directly to the files that define it.

---

## Vision

The conceptual foundation of Zipvilization: an experiment in whether immutable rules, real economic activity and time can produce a readable world and an emergent civilization.

- [Vision](vision.md)

---

## Project

The foundational posture of the project: its origin, launch conditions, assumptions, communication principles, security model and long-term guarantees.

- [Project overview](project/)
- [Assumptions](project/ASSUMPTIONS.md)
- [Communication](project/COMMUNICATION.md)
- [Early Access](project/EARLY_ACCESS.md)
- [Lore: Genesis](project/LORE_GENESIS.md)
- [Post-launch guarantees](project/POST_LAUNCH_GUARANTEES.md)
- [Security](project/SECURITY.md)
- [Token launch](project/TOKEN_LAUNCH.md)
- [Treasury](project/TREASURY.md)

---

## Solum

The immutable on-chain substrate of Zipvilization.

Solum defines fixed supply, contract constraints, transaction rules and the mechanical reality from which the rest of the system is derived.

- [Solum overview](solum/)
- [Canonical contract specification](solum/CONTRACT_SPEC.md)

---

## Solumtools

The interpretation layer between raw blockchain data and readable system signals.

Solumtools defines how public on-chain inputs are collected, normalized and transformed into deterministic outputs for SolumWorld and SolumView.

- [Solumtools overview](solumtools/)
- [Canonical rules](solumtools/CANON.md)
- [Input contracts](solumtools/INPUT_CONTRACTS.md)
- [Output schemas](solumtools/OUTPUT_SCHEMAS.md)
- [Processing pipeline](solumtools/PROCESSING_PIPELINE.md)
- [Tools specification](solumtools/TOOLS_SPEC.md)
- [AI onboarding](solumtools/AI_ONBOARDING.md)

---

## SolumWorld

The canonical world-coherence layer.

SolumWorld defines how on-chain signals become territory, state, history, evolution and a consistent world model without modifying the underlying blockchain reality.

- [SolumWorld overview](solumworld/)
- [World specification](solumworld/WORLD_SPEC.md)
- [Data model](solumworld/DATA_MODEL.md)
- [State model](solumworld/STATE_MODEL.md)
- [Evolution mode](solumworld/EVOLUTION_MODE.md)
- [Implementation pipeline](solumworld/IMPLEMENTATION_PIPELINE.md)
- [Zoom rules](solumworld/ZOOM_RULES.md)
- [AI onboarding](solumworld/AI_ONBOARDING.md)

### State

The state documents define what SolumWorld is allowed to be, how valid states are reached and how consistency is preserved over time.

- [State overview](solumworld/state/)
- [State history](solumworld/state/STATE_HISTORY.md)
- [State invariants](solumworld/state/STATE_INVARIANTS.md)
- [State transitions](solumworld/state/STATE_TRANSITIONS.md)
- [State validation](solumworld/state/STATE_VALIDATION.md)
- [State rollback](solumworld/state/STATE_ROLLBACK.md)

---

## SolumView

The deterministic visual layer of Zipvilization.

SolumView converts canonical SolumWorld state into an auditable interface. It defines rendering, zoom behavior, visual semantics, wallet perspectives and UI requirements.

- [SolumView overview](solumview/)
- [Canonical rendering pipeline](solumview/PIPELINE_CANON.md)
- [Zoom mapping](solumview/ZOOM_MAPPING.md)
- [UI contract](solumview/UI_CONTRACT.md)
- [Icons contract](solumview/ICONS_CONTRACT.md)
- [Visual determinism](solumview/VISUAL_DETERMINISM.md)
- [Wallet mode](solumview/WALLET_MODE.md)
- [AI onboarding](solumview/AI_ONBOARDING.md)

---

## Zipvilization

The user-facing translation layer.

These documents explain how Solum, Solumtools, SolumWorld and SolumView appear in the frontend as territory, colonists, history, population and readable civilization.

- [Zipvilization overview](zipvilization/)
- [Solum translation](zipvilization/SOLUM_TRANSLATION.md)
- [Solumtools translation](zipvilization/SOLUMTOOLS_TRANSLATION.md)
- [SolumWorld translation](zipvilization/SOLUMWORLD_TRANSLATION.md)
- [SolumView translation](zipvilization/SOLUMVIEW_TRANSLATION.md)

### Territories

Rules describing how territory is formed, consolidated and interpreted.

- [Territory consolidation rules](zipvilization/territories/TERRITORY_CONSOLIDATION_RULES.md)
- [ZIP territories and colonist roles](zipvilization/territories/ZIP_TERRITORIES_AND_COLONIST_ROLES.md)

### ZIPs

The biological and population interpretation of ZIP entities inside the readable world.

- [ZIP biology](zipvilization/zips/ZIP_BIOLOGY.md)
- [ZIP biology timing](zipvilization/zips/ZIP_BIOLOGY_TIMING.md)
- [ZIP territory and population](zipvilization/zips/ZIP_TERRITORY_AND_POPULATION.md)

---

## Chapters

Zipvilization evolves through sequential chapters.

Each chapter represents a coherent system state and a publicly readable stage of technical, conceptual and social maturity.

- [Chapters overview](chapters/)
- [Chapter 0 — Genesis](chapters/CHAPTER_0_GENESIS.md)
- [Chapter 1 — Observability](chapters/CHAPTER_1_OBSERVABILITY.md)
- [Chapter 2 — Territory](chapters/CHAPTER_2_TERRITORY.md)
- [Chapter 3 — Colonists and Roles](chapters/CHAPTER_3_COLONISTS_AND_ROLES.md)
- [Chapter 4 — Time, History and Evolution](chapters/CHAPTER_4_TIME_HISTORY_EVOLUTION.md)
- [Chapter 5 — Emergence, Community and Horizon](chapters/CHAPTER_5_EMERGENCE_COMMUNITY_HORIZON.md)

---

## Team

Zipvilization is sustained by a structural trinomio: the human factor, the cognitive engine and the Horizon.

These documents define the role and limits of each element.

- [Team overview](team/)
- [Human factor](team/HUMAN.md)
- [Cognitive engine](team/COGNITIVE.md)
- [Horizon](team/HORIZON.md)

---

## Canonical reading order

A first reading of the project can follow this sequence:

1. [Vision](vision.md)
2. [Project](project/)
3. [Solum](solum/)
4. [Solumtools](solumtools/)
5. [SolumWorld](solumworld/)
6. [SolumView](solumview/)
7. [Zipvilization](zipvilization/)
8. [Chapters](chapters/)
9. [Team](team/)

The documentation should be read as one connected system:

**Solum defines reality. Solumtools reads it. SolumWorld structures it. SolumView renders it. Zipvilization makes it understandable.**
