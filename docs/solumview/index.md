---
layout: default
title: SolumView
parent: Documentation
nav_order: 6
description: Canonical visual layer of Zipvilization. SolumView renders SolumWorld into a deterministic, auditable and reproducible visual representation without modifying state or meaning.
---

# 👁️ SolumView — Technical Canon

**SolumView is Zipvilization's final visual layer.**  
It renders **[SolumWorld](../solumworld/)** state into a deterministic, auditable view — without inventing rules, data or meaning.

> 🌍 **Zipvilization** = the whole  
> 🧩 **[SolumWorld](../solumworld/)** = state + rules  
> 👁️ **SolumView** = canonical renderer

---

## ✅ What SolumView Is

SolumView is a **state-to-visual projection system**.

It takes inputs that already exist (or are already computed) in the stack:

- **[Solum](../solum/)** (on-chain) → immutable signals (supply, transfers, pool primitives)
- **[SolumTools](../solumtools/)** (off-chain interpreter) → normalized metrics + derived signals (no invention)
- **[SolumWorld](../solumworld/)** (world layer) → canonical world-state, zoom rules, evolution mode, state model
- **SolumView** (this folder) → the **visual expression** of that state

SolumView does **not**:

- simulate a world
- decide what reality is
- add narrative meaning
- change economics
- "make it pretty" at the cost of truth

It only makes the world **visible**.

---

## 🎯 Core Requirement: Visual Determinism

SolumView must be **reproducible**.

**Same inputs ⇒ same outputs (pixel-perfect / rule-perfect).**

That means:

- no hidden randomness
- no device-specific layout drift
- no subjective rendering choices
- no "best effort" visualization

When something changes visually, it must be explainable by a change in:

- on-chain [Solum](../solum/) state
- [SolumTools](../solumtools/)-derived signals
- [SolumWorld](../solumworld/) rules or state
- or the explicit SolumView contract documents in this folder

---

## 🧭 Canonical Document Map

This folder defines the minimum canonical surface for SolumView.

### 1) 🧱 Canonical Pipeline (how we render)

- **[PIPELINE_CANON.md](PIPELINE_CANON.md)** — the end-to-end rendering pipeline:
  input acquisition → normalization → state binding → view output.

---

### 2) 🔎 Zoom Mapping (how SolumWorld zoom becomes visible)

- **[ZOOM_MAPPING.md](ZOOM_MAPPING.md)** — mapping between SolumWorld zoom levels and SolumView visual zooms.

Zoom in SolumView is not a camera trick — it is a **semantic resolution selector**.

---

### 3) 🧩 UI Contract (what the UI must expose)

- **[UI_CONTRACT.md](UI_CONTRACT.md)** — canonical UI structure, panels, disclosure rules and non-negotiable visibility.

UI is state-first, not presentation-first.

---

### 4) 🧿 Icons Contract (visual semantics)

- **[ICONS_CONTRACT.md](ICONS_CONTRACT.md)** — every icon is a **semantic state encoder**.

No decorative icons.  
No ambiguous symbols.

---

### 5) ✅ Visual Determinism (auditability)

- **[VISUAL_DETERMINISM.md](VISUAL_DETERMINISM.md)** — reproducibility rules, hashing strategy and validation expectations.

---

### 6) 👛 Wallet Mode (viewer perspective)

- **[WALLET_MODE.md](WALLET_MODE.md)** — view any wallet (lookup) or your own (connect), as a **visual filter** over [SolumWorld](../solumworld/).

Wallet Mode does not change state.

It changes **perspective**.

---

### 7) 🤖 AI Onboarding (how an AI must read this folder)

- **[AI_ONBOARDING.md](AI_ONBOARDING.md)** — operating rules for an AI agent implementing SolumView.

It defines how to read hierarchy, avoid invention and preserve determinism.

---

## 🧩 Relationship to SolumWorld

[SolumWorld](../solumworld/) is the **source of truth** for:

- world-state model
- zoom rules
- evolution mode
- state transitions and invariants
- any rule that defines "what exists"

SolumView is the **source of truth** for:

- how that state becomes visible
- which UI elements are allowed or required
- icon semantics
- determinism guarantees
- validation procedures

**If [SolumWorld](../solumworld/) doesn't define it, SolumView must not render it.**

**If SolumView renders it, it must be traceable to [SolumWorld](../solumworld/).**

---

## 🧱 Minimal Implementation Targets

A SolumView implementation is considered **green** when it can:

- Render a given [SolumWorld](../solumworld/) snapshot deterministically
- Render the same snapshot identically across machines
- Produce a validation hash (or manifest) for verification
- Support semantic zoom switching via [ZOOM_MAPPING.md](ZOOM_MAPPING.md)
- Support Wallet Mode perspective filtering via [WALLET_MODE.md](WALLET_MODE.md)
- Use icons strictly according to [ICONS_CONTRACT.md](ICONS_CONTRACT.md)
- Respect UI disclosure rules defined in [UI_CONTRACT.md](UI_CONTRACT.md)

---

## 📌 Canon Rule

If a behavior is not explicitly defined in:

- the **[SolumWorld](../solumworld/)** canon, or
- the **SolumView canon** (this folder)

...then that behavior does not exist as canon.

No hidden rules.  
No silent assumptions.
