---
layout: default
title: Docs
parent: Repository
nav_order: 1
has_children: true
permalink: /repository/docs/
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

1) **Technical correctness** (immutable rules, derivations, constraints)
2) **Readable meaning** (what users will actually see in the interface)

For that reason, docs are split into:
- **technical layers** (how the system works)
- **translation layers** (how the system becomes a world in the frontend)

---

## 🧱 The Technical Layers (Truth Layer)

These folders describe *what exists* and *how it is derived*.

### 🔒 `solum/`
The on-chain substrate.
The immutable token contract layer, constraints, and mechanical reality.

→ Read if you want the rules.

### 🛠️ `solumtools/`
The interpretation tool layer.
Defines **how to read on-chain data**, compute signals, and produce consistent outputs.

→ Read if you want verifiable metrics and schemas.

### 🌍 `solumworld/`
The world coherence layer.
Defines zoom structure, evolution rules, state model, invariants, and transitions.

→ Read if you want the “world logic” that sits above raw metrics.

### 👁️ `solumview/`
The visual/UX expression layer.
Defines how the world becomes a deterministic, consistent interface: zoom behavior, wallet mode, UI determinism.

→ Read if you want what the user will actually experience.

---

## 🪞 The Translation Layer (User-Facing Meaning)

### 🎛️ `zipvilization/`
This folder is the “mirror”.
It translates the technical layers into **what the user sees and understands** in the frontend.

It answers:
- What does a user see?
- What options exist?
- What does each code / metric represent in the interface?
- How do Solum/Solumtools/Solumworld/Solumview map into UX?

This is not lore or narrative.
It is **technical translation**.

---

## 🧩 Roadmap as Chapters

### 📖 `chapters/`
Zipvilization is built in chapters, not as a single launch of everything at once.

This folder defines:
- what is included in each chapter
- what is intentionally see-through / incomplete early
- what becomes possible only once previous chapters are stable

Chapter 5 is the horizon expansion: once Zipvilization is real, the system becomes open-ended without losing essence.

---

## 🧑‍🚀 Project Canon (Non-technical but still canonical)

### 🗂️ `project/`
Project-level canonical docs that must stay stable and auditable:

- **Lore / Genesis** (how the world is framed)
- **Token Launch** (where and how it happens)
- **Early Access** (why it exists; whitelist mechanism may be defined later)
- **Communication** (why no Discord/Telegram; how official channels work)

These documents are still “truth layer”:
they define constraints and intent, not hype.

---

## 🧬 The Team (Trinomio)

### 🧠 `team/`
Zipvilization is not built like a conventional crypto project.
The team is the trinomio:

- **Human Factor** (anonymous, non-protagonist)
- **Cognitive Engine (AI)** (aligned execution + development capacity)
- **Horizon** (inmutable direction, open-ended after Chapter 5)

No ego. No face. No personality cult.
The protagonist is Zipvilization.

---

## 🌱 Vision (High-level framing)

### `vision.md`
One-page orientation: what Zipvilization is, why it exists, what it tries to observe.

---

# ✅ Recommended Reading Paths

## Path A — Technical Audit (most strict)
1. `solum/`
2. `solumtools/`
3. `solumworld/`
4. `solumview/`

## Path B — “What will users see?”
1. `zipvilization/`
2. `solumview/`
3. `solumworld/`

## Path C — Project understanding (canonical intent)
1. `project/`
2. `chapters/`
3. `team/`

---

## ⚠️ Canon Rule

If a rule is not written in the repo,
and not enforceable by the deployed contract(s),
it does not exist.

This folder is where Zipvilization stays coherent.
