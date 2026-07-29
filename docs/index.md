---
layout: default
title: Documentation
nav_order: 2
has_children: true
permalink: /docs/
description: Canonical documentation of Zipvilization. Explore the technical layers, translation layer, project canon, chapters, vision and team through the project's auditable source of truth.
---

# 📚 Docs — Canonical Documentation (Zipvilization)

GitHub is the **technical, canonical truth layer** of Zipvilization.

- Everything here is written to be **auditable** (by humans and by AI).
- Nothing here is “marketing”.
- If something is not described in the repo (or not deployed on-chain), it **does not exist operationally**.

Other channels (web / Medium / X) may explain the same ideas with a more accessible tone,
but **this folder is the source of truth**.

---

## 🧭 How to Read These Docs

Zipvilization has two simultaneous needs:

1. **Technical correctness** (immutable rules, derivations, constraints)
2. **Readable meaning** (what users will actually see in the interface)

For that reason, docs are split into:

- **technical layers** (how the system works)
- **translation layers** (how the system becomes a world in the frontend)

---

## 🧱 The Technical Layers (Truth Layer)

These folders describe *what exists* and *how it is derived*.

### 🔒 [`solum/`](solum/)

The on-chain substrate.
The immutable token contract layer, constraints, and mechanical reality.

→ Read if you want the rules.

**Documents**

- [Overview](solum/)
- [Canonical Contract Specification](solum/CONTRACT_SPEC.md)

---

### 🛠️ [`solumtools/`](solumtools/)

The interpretation tool layer.

Defines **how to read on-chain data**, compute signals, and produce consistent outputs.

→ Read if you want verifiable metrics and schemas.

**Documents**

- [Overview](solumtools/)
- [Canon](solumtools/CANON.md)
- [Input Contracts](solumtools/INPUT_CONTRACTS.md)
- [Output Schemas](solumtools/OUTPUT_SCHEMAS.md)
- [Processing Pipeline](solumtools/PROCESSING_PIPELINE.md)
- [Tools Specification](solumtools/TOOLS_SPEC.md)
- [AI Onboarding](solumtools/AI_ONBOARDING.md)

---

### 🌍 [`solumworld/`](solumworld/)

The world coherence layer.

Defines zoom structure, evolution rules, state model, invariants, and transitions.

→ Read if you want the “world logic” that sits above raw metrics.

**Documents**

- [Overview](solumworld/)
- [World Specification](solumworld/WORLD_SPEC.md)
- [Data Model](solumworld/DATA_MODEL.md)
- [State Model](solumworld/STATE_MODEL.md)
- [Evolution Mode](solumworld/EVOLUTION_MODE.md)
- [Implementation Pipeline](solumworld/IMPLEMENTATION_PIPELINE.md)
- [Zoom Rules](solumworld/ZOOM_RULES.md)
- [AI Onboarding](solumworld/AI_ONBOARDING.md)

**State**

- [Overview](solumworld/state/)
- [State History](solumworld/state/STATE_HISTORY.md)
- [State Invariants](solumworld/state/STATE_INVARIANTS.md)
- [State Transitions](solumworld/state/STATE_TRANSITIONS.md)
- [State Validation](solumworld/state/STATE_VALIDATION.md)
- [State Rollback](solumworld/state/STATE_ROLLBACK.md)

---

### 👁️ [`solumview/`](solumview/)

The visual/UX expression layer.

Defines how the world becomes a deterministic, consistent interface: zoom behavior, wallet mode, UI determinism.

→ Read if you want what the user will actually experience.

**Documents**

- [Overview](solumview/)
- [Pipeline Canon](solumview/PIPELINE_CANON.md)
- [Zoom Mapping](solumview/ZOOM_MAPPING.md)
- [UI Contract](solumview/UI_CONTRACT.md)
- [Icons Contract](solumview/ICONS_CONTRACT.md)
- [Visual Determinism](solumview/VISUAL_DETERMINISM.md)
- [Wallet Mode](solumview/WALLET_MODE.md)
- [AI Onboarding](solumview/AI_ONBOARDING.md)

---

## 🪞 The Translation Layer (User-Facing Meaning)

### 🎛️ [`zipvilization/`](zipvilization/)

This folder is the “mirror”.

It translates the technical layers into **what the user sees and understands** in the frontend.

It answers:

- What does a user see?
- What options exist?
- What does each code / metric represent in the interface?
- How do Solum/Solumtools/Solumworld/Solumview map into UX?

This is not lore or narrative.

It is **technical translation**.

**Documents**

- [Overview](zipvilization/)
- [Solum Translation](zipvilization/SOLUM_TRANSLATION.md)
- [SolumTools Translation](zipvilization/SOLUMTOOLS_TRANSLATION.md)
- [SolumWorld Translation](zipvilization/SOLUMWORLD_TRANSLATION.md)
- [SolumView Translation](zipvilization/SOLUMVIEW_TRANSLATION.md)

**Territories**

- [Territory Consolidation Rules](zipvilization/territories/TERRITORY_CONSOLIDATION_RULES.md)
- [ZIP Territories and Colonist Roles](zipvilization/territories/ZIP_TERRITORIES_AND_COLONIST_ROLES.md)

**ZIPs**

- [ZIP Biology](zipvilization/zips/ZIP_BIOLOGY.md)
- [ZIP Biology Timing](zipvilization/zips/ZIP_BIOLOGY_TIMING.md)
- [ZIP Territory and Population](zipvilization/zips/ZIP_TERRITORY_AND_POPULATION.md)

---

## 🧩 Roadmap as Chapters

### 📖 [`chapters/`](chapters/)

Zipvilization is built in chapters, not as a single launch of everything at once.

This folder defines:

- what is included in each chapter
- what is intentionally see-through / incomplete early
- what becomes possible only once previous chapters are stable

Chapter 5 is the horizon expansion: once Zipvilization is real, the system becomes open-ended without losing essence.

**Documents**

- [Overview](chapters/)
- [Chapter 0 — Genesis](chapters/CHAPTER_0_GENESIS.md)
- [Chapter 1 — Observability](chapters/CHAPTER_1_OBSERVABILITY.md)
- [Chapter 2 — Territory](chapters/CHAPTER_2_TERRITORY.md)
- [Chapter 3 — Colonists and Roles](chapters/CHAPTER_3_COLONISTS_AND_ROLES.md)
- [Chapter 4 — Time, History and Evolution](chapters/CHAPTER_4_TIME_HISTORY_EVOLUTION.md)
- [Chapter 5 — Emergence, Community and Horizon](chapters/CHAPTER_5_EMERGENCE_COMMUNITY_HORIZON.md)

---

## 🧑‍🚀 Project Canon (Non-technical but still canonical)

### 🗂️ [`project/`](project/)

Project-level canonical docs that must stay stable and auditable.

**Documents**

- [Overview](project/)
- [Assumptions](project/ASSUMPTIONS.md)
- [Communication](project/COMMUNICATION.md)
- [Early Access](project/EARLY_ACCESS.md)
- [Lore / Genesis](project/LORE_GENESIS.md)
- [Post-launch Guarantees](project/POST_LAUNCH_GUARANTEES.md)
- [Security](project/SECURITY.md)
- [Token Launch](project/TOKEN_LAUNCH.md)
- [Treasury](project/TREASURY.md)

These documents are still the **truth layer**:
they define constraints and intent, not hype.

---

## 🧬 The Team (Trinomio)

### 🧠 [`team/`](team/)

Zipvilization is not built like a conventional crypto project.

The team is the trinomio:

- **Human Factor** (anonymous, non-protagonist)
- **Cognitive Engine (AI)** (aligned execution + development capacity)
- **Horizon** (immutable direction, open-ended after Chapter 5)

No ego. No face. No personality cult.

The protagonist is Zipvilization.

**Documents**

- [Overview](team/)
- [Human Factor](team/HUMAN.md)
- [Cognitive Engine](team/COGNITIVE.md)
- [Horizon](team/HORIZON.md)

---

## 🌱 Vision (High-level Framing)

### [`vision.md`](vision.md)

One-page orientation: what Zipvilization is, why it exists, what it tries to observe.

---

# ✅ Recommended Reading Paths

## Path A — Technical Audit (most strict)

1. [`solum/`](solum/)
2. [`solumtools/`](solumtools/)
3. [`solumworld/`](solumworld/)
4. [`solumview/`](solumview/)

---

## Path B — What Will Users See?

1. [`zipvilization/`](zipvilization/)
2. [`solumview/`](solumview/)
3. [`solumworld/`](solumworld/)

---

## Path C — Project Understanding (Canonical Intent)

1. [`project/`](project/)
2. [`chapters/`](chapters/)
3. [`team/`](team/)

---

## ⚠️ Canon Rule

If a rule is not written in the repository,
and not enforceable by the deployed contract(s),
it does not exist.

This folder is where Zipvilization stays coherent.
