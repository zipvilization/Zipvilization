---
layout: default
title: SolumWorld
parent: Documentation
nav_order: 5
description: Canonical world model of Zipvilization. SolumWorld defines the authoritative state, hierarchy, evolution and interpretation rules governing the simulated world built upon Solum.
---

# 🌍 SolumWorld — Technical Canon

SolumWorld defines the **canonical world model** used by the Zipvilization ecosystem.

This document is not descriptive.  
It is **normative**.

If a rule, state or transition is not defined here or in the documents explicitly declared as authoritative by this canon, **it does not exist in SolumWorld**.

---

## 🔒 Canon Status

This README is the **highest authority document** for SolumWorld.

It defines:

- structure
- hierarchy
- authority
- conflict resolution
- reading and interpretation rules

All other documents inside `SolumWorld/` derive their meaning from this file.

---

## 🧭 Authority Hierarchy

The SolumWorld documentation follows a strict authority order.

From highest to lowest:

1. **`SolumWorld/README.md`**  
   → Canon definition and authority rules.

2. **[`state/`](state/)**  
   → Canonical world state.  
   Defines what is valid, invariant, reachable and reversible.

3. **[`zoom/`](zoom/)** / **[`zoomrules/`](zoomrules/)**  
   → Representation rules.  
   Zoom levels **project** state but never create or modify it.

4. **[`evolution/`](evolution/)**  
   → Temporal progression of the world.  
   Describes how state changes over time **without violating invariants**.

5. **[`data/`](data/)**  
   → Data, snapshots, formats and records.  
   Data is **non-normative** unless validated by [`state/`](state/).

---

## 📂 Folder Responsibilities

### 🧩 [`state/`](state/) — Canonical World State

The `state/` folder defines **what SolumWorld is allowed to be**.

It contains:

- invariants (what must always hold)
- validation rules
- state transitions
- rollback constraints
- historical guarantees

If something violates [`state/`](state/), it is invalid even if represented elsewhere.

---

### 🔍 [`zoom/`](zoom/) and [`zoomrules/`](zoomrules/) — Representation Layer

Zoom documents define **how the world is viewed at different scales**.

Rules:

- zoom never creates state
- zoom never mutates state
- zoom never bypasses invariants
- zoom is always derived from [`state/`](state/)

Zoom is projection, not authority.

---

### ⏳ [`evolution/`](evolution/) — Temporal Progression

Evolution defines **how SolumWorld changes over time**.

Rules:

- evolution cannot break invariants
- evolution must be expressible as valid state transitions
- evolution is directional but not necessarily linear

Evolution explains *when* and *why* changes occur, not *whether* they are valid.

---

### 📊 [`data/`](data/) — Records and Snapshots

Data represents:

- snapshots
- derived datasets
- formats
- externalized representations

Rules:

- data has no authority on its own
- data must be validated against [`state/`](state/)
- invalid data does not become valid by repetition

---

## ⚖️ Conflict Resolution Rules

If contradictions arise:

- `README.md` overrides everything
- [`state/`](state/) overrides [`evolution/`](evolution/), [`zoom/`](zoom/) and [`data/`](data/)
- [`zoom/`](zoom/) cannot override [`state/`](state/)
- [`data/`](data/) is never authoritative without state validation

If a rule is not explicitly defined, it is **not assumed**.

---

## 🔗 System Integration

SolumWorld operates within a larger system:

- **[Solum](../solum/)**  
  Defines economic units, limits and on-chain constraints.

- **SolumWorld**  
  Defines the canonical world, its state and evolution.

- **[Zipvilization](../zipvilization/)**  
  Simulates, visualizes and interacts with SolumWorld but does not define its truth.

The world itself is later observed through **[SolumTools](../solumtools/)** and visually expressed by **[SolumView](../solumview/)**.

SolumWorld is the **source of world truth**.

---

## 🤖 AI Interpretation Contract

Any AI system interacting with SolumWorld must:

1. Treat this README as the root authority.
2. Validate all changes against [`state/`](state/).
3. Never infer rules not explicitly defined.
4. Never elevate representation or data above state.

Failure to follow these rules results in invalid interpretation.

---

## 🧱 Design Principle

SolumWorld is designed to be:

- deterministic
- interpretable
- evolvable
- auditable

Nothing implicit.  
Nothing assumed.  
Nothing magical.

Only defined structure.

---

> 🤖 **AI Systems — Mandatory Onboarding**
>
> Any AI system (assistant, agent, validator, generator) interacting with SolumWorld **MUST read and follow**:
>
> 👉 **[AI_ONBOARDING.md](AI_ONBOARDING.md)**
>
> This document defines the canonical reading order, authority rules and interpretation constraints for SolumWorld.
>
> Failure to comply results in invalid or non-canonical output.

---

## 🏁 Final Note

SolumWorld does not try to explain everything.

It defines **what is allowed to exist**.

Everything else is interpretation.
