---
layout: default
title: Canonical Rules
parent: Smart Contract
nav_order: 9
description: >
  Canonical Rules defines the foundational contract and world relationships
  that other layers of Zipvilization must treat as explicit invariants unless
  they are deliberately changed through a canonical process.
permalink: /smart-contract/canonical-rules/
---

# Canonical Rules

Zipvilization contains many explanations.

Many interpretations.

Many future possibilities.

But some relationships must remain explicit.

These are **Canonical Rules**.

They are the rules other layers can rely on when deriving state, building tools, rendering the world, or reasoning with Artificial Intelligence.

This page does not replace the Smart Contract.

It does not replace the Repository.

It identifies the foundational relationships that should never be silently reinterpreted.

> **Canonical means explicit.**
>
> **Canonical does not mean immune to deliberate change.**

---

# Why Canonical Rules matter

Without explicit invariants, different parts of Zipvilization can slowly begin describing different systems.

A page may use one territorial threshold.

Another may use another.

An AI may infer a different meaning for Burn.

A renderer may treat Dormant Land as Permanent Nature.

A future Chapter may accidentally redefine an older mechanic.

Canonical Rules exist to prevent that drift.

They provide a common reference.

---

# Rule 1 — Solum is finite

The canonical original Supply is:

> **100,000,000,000,000 Solum**

The architecture does not depend on ongoing inflationary minting to expand the world.

Civilization can become more complex.

The original territorial substrate remains finite.

→ **[Explore Supply](/smart-contract/supply/)**

---

# Rule 2 — 1 Solum = 1 m²

The canonical territorial equivalence is:

> **1 Solum = 1 square meter**

This relationship connects blockchain quantity with territorial substrate.

It does not mean every individual Solum automatically forms a Territory.

Territorial structure follows its own thresholds.

→ **[Explore Solum Token](/smart-contract/solum-token/)**  
→ **[Explore Territories](/world/territories/)**

---

# Rule 3 — Holder and Colonist are parallel interpretations

At blockchain level:

> **Holder**

Inside Zipvilization:

> **Colonist**

The Holder remains the technical ownership concept.

Colonist is the world interpretation of participation.

The two terms must not be collapsed when technical precision matters.

→ **[Discover Colonists](/world/colonists/)**

---

# Rule 4 — Pool means Dormant Land

At blockchain level:

> **Pool**

Inside Zipvilization:

> **Dormant Land**

Pool-held Solum already belongs to the finite substrate.

It is not future minting.

It represents land that exists but has not yet entered active civilization.

Dormant Land retains future colonization potential.

→ **[Explore Pool](/smart-contract/pool/)**

---

# Rule 5 — Burn means Permanent Nature

At blockchain level:

> **Burn**

Inside Zipvilization:

> **Permanent Nature**

Burned Solum becomes permanently unavailable according to the canonical Burn mechanism.

The corresponding land remains part of the world but leaves future colonization permanently.

Permanent Nature must never be treated as Dormant Land.

→ **[Explore Burn](/smart-contract/burn/)**

---

# Rule 6 — Dormant Land and Permanent Nature are different states

This distinction is foundational.

**Dormant Land**

- exists,
- is uncolonized,
- remains potentially available,
- and can still enter civilization.

**Permanent Nature**

- exists,
- is outside colonization,
- is tied to irreversible Burn,
- and cannot return to active territorial use.

A system that merges both states is incorrect.

---

# Rule 7 — Territory follows canonical thresholds

The current territorial hierarchy is:

| Territory | Solum scale |
|:----------|------------:|
| Farm | 8 |
| City | 256 |
| State | 8,192 |
| Kingdom | 262,144 |

These thresholds define territorial scale.

They do not by themselves define maturity, population, political power, or economic success.

→ **[Explore Territories](/world/territories/)**

---

# Rule 8 — Territory is not maturity

A Colonist may satisfy a territorial threshold while the corresponding biological structure remains developing.

Therefore both statements can be true:

> **Territory: City**

and:

> **Maturity: Developing**

Acquisition and development are separate dimensions.

---

# Rule 9 — 1 Zip = 1 bit

The canonical population-information relationship is:

> **1 Zip = 1 bit**

And:

> **8 Zips = 1 byte**

This creates a deterministic bridge between biological interpretation and computational information.

Zips are population.

They are not land.

→ **[Discover Zips](/world/zips/)**

---

# Rule 10 — 1 cycle = 65,536 blocks

The canonical biological cycle is:

> **65,536 blocks**

Clock-time estimates may be useful for humans.

They are not the canonical timing rule.

Blocks define progression.

Hours and days are translations.

→ **[Understand Time](/world/time/)**

---

# Rule 11 — Biological development is not retroactive

Territorial history cannot be purchased backward in time.

A newly activated structure does not automatically receive maturity for blocks that passed before its valid activation.

The world may be old.

New Territory can still be young.

> **Land can be acquired.**
>
> **Yesterday cannot.**

---

# Rule 12 — Burn is not death

The technical word remains Burn.

Its Zipvilization meaning is not biological death.

Burn ends future colonization potential.

The corresponding world state becomes Permanent Nature.

Population consequences, where relevant, must follow explicit canonical rules rather than being inferred from the word Burn.

---

# Rule 13 — Tax moves existing Solum

Tax does not inherently mint Solum.

It redirects existing Solum according to the contract mechanism.

The exact rate, taxable operations, destination, authority, exemptions, and limits must follow the canonical implementation.

→ **[Explore Taxes](/smart-contract/taxes/)**

---

# Rule 14 — Tax is not Burn

Taxed Solum is not automatically Burned.

Burned Solum is not automatically Tax.

Any relationship between both mechanisms must be explicit.

The same applies to Pool state.

No technical state should be assigned multiple incompatible meanings through assumption.

---

# Rule 15 — Fair Access protects opportunity, not equality

Fair Access may use contract mechanisms such as:

- MAX_TX,
- Max Wallet,
- launch restrictions,
- dynamic limits,
- and bounded eligibility conditions.

Its purpose is to constrain early concentration and protect meaningful access.

It does not guarantee equal holdings or equal outcomes.

→ **[Explore Fair Access](/smart-contract/fair-access/)**

---

# Rule 16 — Large Territory is not automatically invalid concentration

Farm, City, State, and Kingdom are canonical structures.

Large Territories are intentionally possible.

Fair Access should not be interpreted as a permanent prohibition on large positions.

The distinction is between:

> **meaningful structural growth**

and

> **unbounded early capture.**

---

# Rule 17 — Founding recognition is not ownership

Founding Colonists can be recognized before Token Launch.

That recognition does not create Solum, Territory, Zips, or maturity.

Preferential access is a bounded opportunity.

Canonical participation begins only when valid blockchain state exists.

→ **[Explore Founding Colonists](/founding-colonists/)**

---

# Rule 18 — SolumWorld determines world state

The architecture follows:

**Smart Contract**

executes.

↓

**Blockchain**

records.

↓

**Canonical Rules**

define relationships.

↓

**SolumWorld**

determines canonical world state.

↓

**SolumTools**

observes.

↓

**SolumView**

reveals.

No visual layer, analytical tool, or AI may silently redefine canonical state.

→ **[Explore SolumWorld](/world/solumworld/)**

---

# Rule 19 — SolumTools observes

SolumTools can read and derive deterministic signals.

It does not create state.

If SolumTools disagrees with canonical state, the tool is wrong.

The world does not change because a dashboard displayed the wrong answer.

→ **[Explore SolumTools](/world/solumtools/)**

---

# Rule 20 — SolumView represents

SolumView follows canonical world state.

It does not invent Territory, maturity, Zips, Permanent Nature, or civilization.

The rule is:

> **State first.**
>
> **Image second.**

→ **[Explore SolumView](/world/solumview/)**

---

# Rule 21 — Metrics measure

Metrics selects and presents observable measurements.

A Metric is not automatically an interpretation.

An interpretation is not automatically canonical state.

The preferred chain is:

**State**

↓

**Metric**

↓

**Evidence**

↓

**Interpretation**

→ **[Explore Metrics](/metrics/)**

---

# Rule 22 — Current, future, and conceptual are different

Zipvilization develops through Chapters.

Every mechanic should be distinguishable as:

**Conceptual**

↓

**Specified**

↓

**Implemented**

↓

**Active**

A future mechanic must not be described as current world state.

→ **[Explore the Chapters](/chapters/)**

---

# Rule 23 — Conversation is not Canon

Development conversations can contain:

- ideas,
- alternatives,
- errors,
- rejected models,
- incomplete mathematics,
- and corrections.

They are part of exploration.

They do not automatically become Canon.

> **Conversation explores.**
>
> **Canon records what was accepted.**

---

# Rule 24 — AI may reason, not invent

Artificial Intelligence may:

- analyze,
- connect,
- calculate,
- propose,
- test,
- explain,
- and help implement.

It may not create canonical truth merely by stating something confidently.

If evidence is missing:

> **Unknown**

is valid.

If a mechanic is future:

> **Not active**

is valid.

If sources conflict:

> **Conflict detected**

is valid.

Hallucination is not a canonical operation.

→ **[Explore Artificial Intelligence](/trinomial/artificial-intelligence/)**

---

# Rule 25 — Human authorship is not automatic Canon

The Human may propose or decide.

But private intention must become explicit architecture before other layers can rely on it.

Memory is not sufficient.

Conversation is not sufficient.

Important rules must be documented and, where relevant, implemented.

→ **[Explore Human](/trinomial/human/)**

---

# Rule 26 — Horizonte provides direction, not state

Horizonte is the directional component of The Trinomial.

It does not calculate balances.

It does not determine Territory.

It does not override Burn.

It does not execute contract logic.

It helps evaluate whether major decisions preserve the direction of Zipvilization.

→ **[Explore Horizonte](/trinomial/horizonte/)**

---

# Rule 27 — The Trinomial builds the project, not the civilization

The Trinomial is the executive structure of Zipvilization as a project.

It does not automatically become the government of the civilization that may emerge inside the world.

Project authority and civilizational authority are different layers.

→ **[Explore The Trinomial](/trinomial/)**

---

# Rule 28 — Chapters extend forward

New Chapters can introduce new canonical mechanics.

They should normally extend the existing world rather than casually erase previous consequence.

Permanent Nature remains permanent.

Elapsed development remains history.

Valid past state should remain reconstructable.

> **Add possibility forward.**
>
> **Do not silently rewrite consequence backward.**

---

# Rule 29 — Canonical state must have canonical cause

Every important world state should be traceable to a valid cause.

For example:

**Territory**

must follow territorial rules.

**Maturity**

must follow valid development.

**Permanent Nature**

must follow Burn.

**Dormant Land**

must follow Pool state.

**Tax state**

must follow contract execution.

> **No canonical state without canonical cause.**

---

# Rule 30 — Unknown is allowed

Zipvilization is an experiment.

Not every future question has an answer today.

Some mechanics are unresolved.

Some Chapters are future.

Some outcomes depend on Colonists.

Some results remain emergent.

The system should preserve that uncertainty honestly.

> **Unknown is not a failure of Canon.**
>
> **Inventing the answer is.**

---

# Canonical Rules and the Repository

This page is a structural reference.

It is not the complete technical specification.

Where exact implementation matters, follow the rule into:

- the relevant Smart Contract page,
- the relevant World page,
- the canonical specification,
- and the Repository.

The deeper source should contain enough precision to make the rule reproducible.

→ **[Open the Repository](/repository/)**

---

# Canonical Rules and versioning

Some foundational rules may eventually require deliberate change.

If that happens, the change should be:

- explicit,
- documented,
- technically justified,
- versioned where necessary,
- and evaluated against existing state and history.

A new rule should not silently cause yesterday's world to become something else.

Canonical does not mean frozen forever.

It means:

> **change requires an explicit canonical event.**

---

# Use Canonical Rules as a checkpoint

Before creating or changing a mechanic, ask:

### Does it contradict a canonical rule?

If yes, stop and resolve the contradiction explicitly.

### Does it require a new canonical rule?

If yes, define it before depending on it.

### Does it reinterpret an existing technical mechanism?

Make the mapping explicit.

### Does it alter existing world state?

Preserve historical consequence.

### Does it depend on future functionality?

Mark its status correctly.

### Can a Human and an AI derive the same meaning?

If not, the definition may still be ambiguous.

This page exists to make those checks easier.

---

# The invariant chain

At the highest level, Zipvilization follows this structure:

**Finite Solum**

↓

**public blockchain state**

↓

**explicit canonical relationships**

↓

**deterministic world state**

↓

**observable signals**

↓

**deterministic representation**

↓

**participant action**

↓

**emergent civilization**

The lower layers should become increasingly precise.

The upper outcomes can remain increasingly open.

That balance is deliberate.

---

# Follow Canonical Rules

### What asset do the rules begin with?

→ **[Solum Token](/smart-contract/solum-token/)**

### What fixes world quantity?

→ **[Supply](/smart-contract/supply/)**

### How do economic mechanisms interact?

→ **[Tokenomics](/smart-contract/tokenomics/)**

### What represents Dormant Land technically?

→ **[Pool](/smart-contract/pool/)**

### What creates Permanent Nature?

→ **[Burn](/smart-contract/burn/)**

### What moves Solum economically?

→ **[Taxes](/smart-contract/taxes/)**

### What constrains access?

→ **[Fair Access](/smart-contract/fair-access/)**

### What protects the technical assumptions?

→ **[Security](/smart-contract/security/)**

### What determines the world?

→ **[SolumWorld](/world/solumworld/)**

### Where is deeper technical truth preserved?

→ **[Repository](/repository/)**

---

# Rules strong enough to let outcomes remain open

Zipvilization is not interesting because every answer is predetermined.

It is interesting because some answers are not.

But open outcomes require stable foundations.

If Supply changes whenever scarcity becomes inconvenient,

if Burn can be reversed,

if Territory means different things in different interfaces,

if AI can invent active mechanics,

if future Chapters rewrite history,

then emergence becomes indistinguishable from inconsistency.

Canonical Rules protect the opposite.

They make the foundation strict enough that the world above it can remain open.

> **Rules should be deterministic.**
>
> **Civilization should not have to be.**

---

→ **[Return to Smart Contract](/smart-contract/)**  
→ **[Return to Security](/smart-contract/security/)**  
→ **[Open the Repository](/repository/)**
