---
layout: default
title: SolumWorld
parent: The World
nav_order: 8
has_children: true
description: >
  SolumWorld is the canonical world-state layer of Zipvilization. It translates
  blockchain state and canonical rules into a deterministic model of what
  exists in the world, without adding narrative, visual, or AI invention.
permalink: /world/solumworld/
---

# SolumWorld

Blockchain tells us what happened.

Zipvilization also needs to determine what those events mean for the world.

That is the role of **SolumWorld**.

SolumWorld is the canonical world-state layer of Zipvilization.

It connects technical state with the rules of the world and determines what canonically exists:

- Colonists,
- Territories,
- Zips,
- maturity,
- Dormant Land,
- Permanent Nature,
- developmental state,
- and other world structures defined by canonical rules.

It does not create blockchain state.

It does not move Solum.

It does not invent civilization.

It does not decide what would make the world more interesting.

It determines what the existing state means inside Zipvilization.

> **Blockchain records what happened.**
>
> **SolumWorld determines what that means for the world.**

→ **[Explore The World](/world/)**  
→ **[Explore the Smart Contract](/smart-contract/)**

---

# Two languages, one world

Zipvilization deliberately maintains two connected languages.

**Blockchain describes the mechanism.**

**Zipvilization describes the meaning.**

For example:

| Blockchain | Zipvilization |
|:-----------|:--------------|
| Holder | Colonist |
| Solum balance | Controlled land |
| Supply | Finite territorial substrate |
| Pool | Dormant Land |
| Burn | Permanent Nature |
| Block progression | Biological time |
| Threshold state | Territory |
| Binary information | Zip population |

These are not independent systems.

They describe the same underlying reality from different layers.

SolumWorld is the bridge that keeps those relationships deterministic.

It prevents every interface, tool, or AI from creating its own interpretation of Zipvilization.

---

# Deterministic interpretation

SolumWorld interprets state.

But **interpretation does not mean imagination**.

Given the same canonical inputs and the same canonical rules, the resulting world state should be the same.

A Farm cannot be mature for one interface and immature for another.

Burned Solum cannot be Permanent Nature in one application and available territory in another.

A City cannot exist because an AI believes that it should.

A Kingdom cannot appear because a map designer wants the world to look more interesting.

The rule is simple:

> **State → Canonical Rules → World**

Never:

> **Desired World → Invented State**

---

# The authority chain

Each layer of Zipvilization has a different responsibility.

**Smart Contract**

executes blockchain mechanics.

↓

**Blockchain**

records state and progression.

↓

**Canonical Rules**

define how relevant state maps into Zipvilization.

↓

**SolumWorld**

determines canonical world state.

↓

**SolumTools**

observes and exposes that state.

↓

**SolumView**

renders that state visually.

This hierarchy is fundamental.

> **The Smart Contract executes.**
>
> **The blockchain records.**
>
> **SolumWorld determines.**
>
> **SolumTools observes.**
>
> **SolumView reveals.**

No higher layer should silently redefine a lower one.

---

# What SolumWorld can determine

Where explicit canonical rules exist, SolumWorld can determine states such as:

### Colonist

A blockchain Holder interpreted as a participant inside Zipvilization.

→ **[Discover Colonists](/world/colonists/)**

### Territory

The territorial structure supported by canonical Solum conditions.

Farm.

City.

State.

Kingdom.

→ **[Explore Territories](/world/territories/)**

### Biological state

Zip population, development, and maturity according to the canonical biological model.

→ **[Discover Zips](/world/zips/)**

### Developmental state

Progress derived from canonical block-based time.

→ **[Understand Time](/world/time/)**

### Dormant Land

Solum that remains outside active civilization in its dormant state.

→ **[Discover Solum](/world/solum/)**

### Permanent Nature

Solum permanently removed from circulation through Burn and therefore unavailable to future colonization.

→ **[Understand Burn](/smart-contract/burn/)**

These are examples of canonical world state.

Future Chapters may introduce additional states.

---

# What SolumWorld does not determine

SolumWorld defines the world beneath civilization.

It does not predetermine civilization itself.

It should not decide:

- which Colonists will cooperate,
- which territories will become economically important,
- which political structures will succeed,
- which alliances will form,
- which conflicts will occur,
- who will become powerful,
- or what culture may emerge.

Those outcomes belong to participation and future civilizational mechanics.

> **SolumWorld determines conditions.**
>
> **Colonists create consequences.**

→ **[Explore Civilization](/world/civilization/)**

---

# Territory is not maturity

SolumWorld must preserve distinctions.

A Colonist may satisfy the Solum threshold for a City while that City is still biologically developing.

Therefore both statements can be true:

> **Territory: City**

and

> **Maturity: Developing**

Territorial scale and biological maturity are different state dimensions.

The same applies elsewhere:

**Territory is not population.**

**Population is not power.**

**Maturity is not civilization.**

Keeping these concepts separate prevents false conclusions.

→ **[Explore Territories](/world/territories/)**  
→ **[Discover Zips](/world/zips/)**

---

# The world has memory

Zipvilization is not only a snapshot.

Things happen.

Colonists arrive.

Territorial thresholds are crossed.

Zips emerge.

Territories mature.

Solum becomes Permanent Nature.

New structures become possible.

That creates a difference between:

**current state**

and

**history.**

A new City and a mature City may contain similar amounts of Solum while representing very different histories.

A piece of Dormant Land and a piece of Permanent Nature may both sit outside Colonist control while having completely different futures.

SolumWorld must preserve meaningful distinctions created by state and time.

→ **[Understand Time](/world/time/)**

---

# The world must be reconstructable

Zipvilization should not depend entirely on one website, one database, one AI, or one visualization.

Wherever possible, canonical world state should be reproducible from:

**canonical inputs**

+

**canonical rules**

=

**canonical world state**

An independent implementation following the same rules should be capable of reaching the same answer.

That makes the world more resilient.

And more verifiable.

> **If an interface disappears, the world should remain derivable.**

The deeper technical specification for that reconstruction belongs in the Repository.

→ **[Open the Repository](/repository/)**

---

# SolumWorld is not SolumTools

The distinction is simple.

**SolumWorld determines.**

**SolumTools observes.**

SolumWorld answers:

> What canonically exists?

SolumTools answers:

> How can we expose and inspect that state?

A SolumTools error does not change the world.

It means the tool is wrong.

→ **[Explore SolumTools](/world/solumtools/)**

---

# SolumWorld is not SolumView

SolumView is the visual layer.

Its responsibility is representation.

SolumWorld may determine:

> **City — Developing**

SolumView may represent that City as visually incomplete.

But SolumView cannot promote it to maturity because a finished City looks better.

Likewise, Permanent Nature can appear visually because the corresponding canonical state exists.

The direction must always remain:

**World State**

↓

**Visual Representation**

> **The map follows the world.**
>
> **The world does not follow the map.**

→ **[Explore SolumView](/world/solumview/)**

---

# SolumWorld and Artificial Intelligence

Artificial Intelligence needs a world it can reason about without inventing missing state.

The correct path is:

**Canonical concept**

↓

**Canonical rule**

↓

**Implementation status**

↓

**Current state**

↓

**Valid derivation**

↓

**Explanation**

If information is missing, the correct answer may be:

> **Unknown.**

That is acceptable.

Inventing canonical state is not.

AI can help understand Zipvilization.

It cannot create Zipvilization simply by describing something as true.

→ **[Explore Artificial Intelligence](/trinomial/artificial-intelligence/)**

---

# Explore SolumWorld

SolumWorld contains several deeper problems that deserve their own documentation.

## Authority

What is authoritative, and which layer is allowed to determine what?

→ **Authority**

## State Mapping

How does blockchain state map deterministically into Zipvilization concepts?

→ **State Mapping**

## State Transitions

How do upgrades, downgrades, maturation, Burn, and other events change world state?

→ **State Transitions**

## History

How do current state, previous state, and irreversible events create a world with memory?

→ **History**

## AI Integrity

How can Artificial Intelligence reason about Zipvilization without inventing canonical state?

→ **AI Integrity**

## Versioning

How can canonical rules evolve without silently rewriting the world that already existed?

→ **Versioning**

These pages will develop the deeper architecture.

This index defines their common foundation.

---

# SolumWorld in the architecture

The complete relationship is:

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

determines.

↓

**SolumTools**

observes.

↓

**SolumView**

reveals.

↓

**Humans and Artificial Intelligence**

understand.

↓

**Colonists**

act.

↓

**Civilization**

may emerge.

The final outcome can remain open because the foundation beneath it is explicit.

---

# Continue exploring

### Observe the world

→ **[SolumTools](/world/solumtools/)**

### See the world

→ **[SolumView](/world/solumview/)**

### Understand the world substrate

→ **[Solum](/world/solum/)**

### Understand territorial structure

→ **[Territories](/world/territories/)**

### Understand biological state

→ **[Zips](/world/zips/)**

### Understand development

→ **[Time](/world/time/)**

### Understand what remains emergent

→ **[Civilization](/world/civilization/)**

### Inspect the blockchain mechanics

→ **[Smart Contract](/smart-contract/)**

### Reach the technical source

→ **[Repository](/repository/)**

---

**The blockchain gives Zipvilization facts.**

**Canonical rules give those facts relationships.**

**SolumWorld turns those relationships into a world.**

And only then should anyone — human, interface, or Artificial Intelligence — decide how to look at it.

---

→ **[Return to The World](/world/)**  
→ **[Continue to SolumView](/world/solumview/)**
