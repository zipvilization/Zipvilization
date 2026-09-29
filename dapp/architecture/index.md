---
layout: default
title: Architecture
parent: The dApp
nav_order: 2
description: >
  The dApp Architecture explains how blockchain evidence, History and Canonical
  Rules can become deterministic Zipvilization state and how that state can
  support data, world and experience layers without exposing the internal
  implementation required to reproduce the system.
permalink: /dapp/architecture/
---

# dApp Architecture

The visible dApp is only the surface.

Below it is a system responsible for a more difficult task:

> **preserving the relationship between blockchain evidence, canonical meaning, History and the world that Humans and AI can observe.**

That requires more than reading balances.

The architecture must distinguish:

- evidence from meaning,
- current state from History,
- capacity from maturity,
- generation from capacity,
- canonical state from representation,
- representation from simulation,
- and observation from valid interaction.

These distinctions are part of the foundation of Zipvilization.

The exact machinery used to implement them is not.

---

# Architecture Before Interface

Zipvilization does not begin with a graphical interface.

It begins with relationships.

Blockchain state exists.

History accumulates.

Canonical Rules determine meaning.

Deterministic relationships allow meaningful Zipvilization state to be derived.

Only then does that state become data, world representation and experience.

The public architectural direction is:

**EVIDENCE**  
↓  
**CANONICAL MEANING**  
↓  
**DERIVED WORLD STATE**  
↓  
**ACCESS**  
↓  
**REPRESENTATION / EXPERIENCE**

History matters throughout this process.

> **The interface consumes the architecture.**
>
> **It does not define the world beneath it.**

This allows the first interfaces to remain relatively simple while the system beneath them preserves considerably deeper relationships.

---

# Logical Architecture

For public documentation, the dApp can be understood through five logical boundaries:

**EVIDENCE**  
Blockchain state and History  
↓  
**SEMANTICS**  
Canonical Rules, definitions and invariants  
↓  
**DERIVED STATE**  
Deterministic Zipvilization state  
↓  
**ACCESS**  
State made usable by different consumers  
↓  
**REPRESENTATION & EXPERIENCE**  
Data, world and territorial experience

These are **logical responsibilities**.

They are not a public description of deployment topology, internal services, storage architecture or implementation boundaries.

That distinction is intentional.

The Atlas explains what the system must preserve.

It does not publish how every internal component achieves it.

---

# Evidence

At the base is technical evidence.

Relevant evidence can include blockchain state and History such as:

- SOLUM balances,
- transfers,
- Burn,
- Pool state,
- blocks,
- contract events,
- addresses,
- and state changes through Time.

These facts can establish what happened technically.

But raw blockchain evidence does not independently explain the full meaning of Zipvilization.

A balance does not by itself explain Colonist status.

A transfer does not by itself explain territorial maturity.

A Burn does not explain Permanent Nature without the canonical relationship that gives Burn that meaning.

Therefore:

> **Evidence establishes facts.**
>
> **Canonical Rules establish Zipvilization meaning.**

---

# Canonical Meaning

Canonical Rules connect technical evidence to the world.

They define relationships such as:

**1 SOLUM = 1 m² of Solum**

**8,000,000 SOLUM = 8 Tiles = 1 complete Farm**

**complete Farm threshold → Colonist**

**valid Colonist → Active Territory**

**1 Farm → 1 Bloch**

**Burn → Permanent Nature**

and the defined relationships governing:

- territorial capacity,
- territorial composition,
- Time,
- population,
- maturity,
- land state,
- and historical validity.

This boundary prevents interfaces and applications from independently deciding what blockchain activity means.

> **Canonical Rules define the meaning.**
>
> **The dApp applies and exposes that meaning.**

---

# Canonical Meaning Must Be Public

A Human or AI should be able to understand why a canonical claim is valid.

For example:

- why an address is a Holder rather than a Colonist,
- why a complete Farm exists,
- why Territory is Active,
- why land became Permanent Nature,
- why population can exist,
- or why a maturity state is historically supported.

Those relationships cannot depend on hidden world rules.

They belong to the public model.

But public canonical meaning does not require public internal implementation.

This creates an important boundary:

**PUBLIC**

Definitions  
Rules  
Relationships  
Dependencies  
Invariants  
Canonical consequences

**INTERNAL**

Implementation methods  
Operational structures  
Performance mechanisms  
Private infrastructure  
Proprietary engineering

> **The meaning must be auditable.**
>
> **The machinery does not need to be reproducible from the Atlas.**

---

# Deterministic Derived State

Blockchain evidence and Canonical Rules can together produce meaningful Zipvilization state.

Conceptually:

**BLOCKCHAIN STATE + HISTORY**  
+  
**CANONICAL RULES**  
↓  
**DETERMINISTIC ZIPVILIZATION STATE**

That state can include defined concepts such as:

- Holders,
- Colonists,
- Territory,
- Tiles,
- Farms,
- Cities,
- States,
- Kingdoms,
- Bloch,
- land states,
- population,
- maturity,
- and historically valid development.

This is a central architectural responsibility.

The blockchain does not need to store every Human-readable world concept directly.

And the visual interface does not need to invent them.

Defined relationships allow them to be derived.

---

# Derived Does Not Mean Inferred

In Zipvilization, a canonical derived state is not a guess.

It is not an AI interpretation.

It is not an estimate produced because the interface needs an answer.

And it is not a conclusion drawn from visual appearance.

Canonical derivation requires:

**VALID EVIDENCE**  
+  
**DEFINED RULES**

If a canonical relationship is not defined, the architecture must not silently invent one.

If evidence is insufficient, the system must not convert uncertainty into canonical fact.

> **Deterministic derivation applies defined meaning.**
>
> **It does not create missing meaning.**

This distinction is especially important for AI.

---

# History Is Part of State

Zipvilization cannot always be understood from a current snapshot.

Current state can tell us what exists now.

History can determine how that state became valid.

For example:

a later acquisition can increase future territorial capacity.

It does not create retroactive development.

A later transfer can change future conditions.

It does not erase valid development that occurred before it.

Therefore:

**CURRENT BALANCE ≠ HISTORICAL MATURITY**

and:

**CURRENT CAPACITY ≠ HISTORICAL POPULATION**

The architectural requirement is consequently larger than:

**READ CURRENT STATE**

It must be capable of respecting:

**STATE THROUGH TIME**

because History can affect the canonical interpretation of the present.

> **A snapshot explains now.**
>
> **History explains how the world became now.**

---

# Historical Validity

The public architecture does not need to expose the internal process used to handle historical state.

But it must make one requirement explicit:

> **historical claims must remain supported by valid evidence and canonical rules.**

This applies to concepts such as:

- when active territorial development became possible,
- which Farms were valid through Time,
- how much valid biological progression could occur,
- which population could emerge,
- and when maturity could become valid.

The requirement is public.

The implementation is internal.

That distinction protects both auditability and know-how.

---

# Truth and Operational State Are Different Things

A system can maintain operational representations of canonical information in order to make the dApp usable.

Those representations are useful.

They are not the origin of canonical truth.

Conceptually:

**AUTHORITATIVE EVIDENCE**  
↓  
**CANONICAL MEANING**  
↓  
**DERIVED STATE**  
↓  
**OPERATIONAL ACCESS**  
↓  
**REPRESENTATION**

This distinction matters because an operational error must remain an operational error.

If exposed information becomes stale, canonical reality has not changed to match it.

If a graphical representation is incorrect, Territory has not changed to match the graphic.

If an interface fails to display an existing state, that absence does not erase the underlying state.

> **Convenience is not authority.**
>
> **Representation is not truth.**

---

# Reconstructibility as an Architectural Requirement

Canonical state should not conceptually depend on an interface or representation remaining permanently available.

The authoritative basis remains:

**BLOCKCHAIN STATE + HISTORY**  
+  
**CANONICAL RULES**

From an architectural perspective, this establishes an important requirement:

> **deterministic world state should remain derivable from authoritative evidence and canonical meaning.**

This does not describe or disclose the internal reconstruction process.

Nor does it claim that every possible derived representation is stored on-chain.

It defines the direction of authority.

Operational systems may make access faster.

They may prepare information for different consumers.

They may maintain derived representations.

But they must remain downstream from the evidence and rules that give the state its validity.

---

# Replaceable Surfaces

One consequence of this architecture is that the visible surfaces can evolve.

SolumTools can change its interface.

SolumWorld can change its graphical representation.

SolumView can become substantially more sophisticated.

Those changes do not require redefining:

- what a Holder is,
- what a Colonist is,
- what a Farm is,
- what Territory means,
- how Bloch relates to Farms,
- what Time means,
- or what historical maturity requires.

This gives the dApp an important property:

> **The experience can evolve without rewriting the world underneath it.**

---

# Authority Flows Downstream

The architecture has a clear direction of authority:

**BLOCKCHAIN STATE + HISTORY**  
↓  
**CANONICAL RULES**  
↓  
**DERIVED STATE**  
↓  
**REPRESENTATION**

Never the reverse.

A downstream system can misrepresent upstream truth.

It cannot acquire authority over it.

If SolumTools displays an incorrect value, the display is wrong.

If SolumWorld renders unsupported Territory, the representation is wrong.

If SolumView shows unsupported canonical population, the experience is wrong.

The error does not become canonical merely because it is visible.

> **Representation can interpret truth.**
>
> **It cannot replace it.**

---

# Invariants Before Features

Interfaces and features can evolve rapidly.

Canonical invariants should not.

Among the architectural invariants already defined:

### One canonical reality

Different dApp surfaces cannot create different truths.

### Evidence precedes canonical claims

Canonical state must remain grounded in valid evidence and defined rules.

### Holder is not automatically Colonist

A complete Farm threshold remains required.

### Territory defines capacity

Graphical representation cannot redefine territorial mathematics.

### Farms generate population

Population origin remains associated with Farms and Bloch.

### Higher Territory provides capacity

Higher territorial structures do not introduce independent population generators.

### Time acts on valid state

Elapsed blocks alone do not invent population.

### History determines what validly occurred

Current state cannot retroactively manufacture development.

### Capacity does not equal maturity

Historical development remains relevant.

### Dormant, Active and Permanent remain distinct

Representation cannot collapse their meanings.

### Simulation does not create canonical History

Visual life can be dynamic without fabricating world truth.

### Testnet is not canonical History

Testing can validate development without becoming the official world.

### Horizonte remains unresolved

Undefined future systems cannot be inferred merely because the architecture could support them.

> **Features can expand the experience.**
>
> **Invariants preserve the world.**

---

# Access Without Semantic Duplication

Different parts of the dApp require different views of the same underlying state.

SolumTools needs readable information.

SolumWorld needs world-scale state.

SolumView needs increasingly detailed territorial state.

The architecture should not require each of them to independently redefine canonical meaning.

The public model is therefore:

**ONE CANONICAL REALITY**  
↓  
**MULTIPLE DEPTHS OF ACCESS**

not:

**MULTIPLE INTERFACES**  
↓  
**MULTIPLE DEFINITIONS OF REALITY**

This is one of the reasons the architecture is modular while the experience can remain unified.

---

# SolumTools Is the Data Foundation

SolumTools is the principal data and observation layer of the dApp.

Its role is to apply canonical meaning to blockchain state and History and expose readable Zipvilization data.

Conceptually:

**BLOCKCHAIN STATE + HISTORY**  
↓  
**CANONICAL RULES**  
↓  
**SOLUMTOOLS**  
↓  
**READABLE ZIPVILIZATION DATA**

SolumTools can expose deterministic information about:

- Colonists,
- Territory,
- Farms,
- Cities,
- States,
- Kingdoms,
- Dormant Land,
- Permanent Nature,
- population,
- maturity,
- History,
- and activity.

But SolumTools does not invent the meaning of those concepts.

Canonical Rules do.

> **SolumTools makes the state of Solum readable.**

→ **[Explore SolumTools](/world/solumtools/)**

---

# SolumWorld Represents the Planet

SolumWorld gives grounded world state planetary form.

It can represent:

- Dormant Land,
- Active Territory,
- Permanent Nature,
- territorial structures,
- population,
- maturity,
- and History

at appropriate levels of abstraction.

Its architecture is data-bound but visually interpretative.

That means visual representation can evolve.

Canonical facts cannot.

> **Canonical state determines what is true on Solum.**
>
> **SolumWorld determines how that truth is represented at planetary scale.**

SolumWorld does not determine canonical world state.

It represents it.

→ **[Explore SolumWorld](/world/solumworld/)**

---

# SolumView Makes Territory Experienceable

SolumView moves from planetary observation into individual Territory.

Its possible experiential depth includes:

- Farms,
- Zips,
- development,
- maturity,
- construction,
- movement,
- local activity,
- and History.

But SolumView introduces an important distinction:

**CANONICAL STATE**  
↓  
**EXPERIENTIAL REPRESENTATION**

The experience can be dynamic.

It does not need to represent every canonical unit literally.

It can interpret, animate and simulate visual life.

But:

> **Visual life may be simulated.**
>
> **Canonical truth may not.**

A visual Zip walking does not automatically create canonical History.

A rendered building does not independently establish maturity.

A visual interaction does not become a canonical event merely because it occurred on screen.

→ **[Explore SolumView](/world/solumview/)**

---

# Modular Architecture, Unified Experience

SolumTools, SolumWorld and SolumView are deeply related.

But their relationship should not be misunderstood as a requirement that each technical implementation must literally depend on the previous interface.

The conceptual progression is:

**DATA → PLANET → LIFE**

and:

**READ → SEE → ENTER**

At the same time, they remain different ways of accessing the same underlying reality.

Conceptually:

**CANONICAL ZIPVILIZATION STATE**  
↙ ↓ ↘  
**DATA — WORLD — LIFE**

This preserves both properties:

> **The architecture is modular.**
>
> **The experience is unified.**

---

# Different Consumers, Same Facts

The layers may represent different levels of detail.

They cannot disagree on canonical facts.

If eight valid Farms exist, one layer cannot canonically claim twelve.

If a Territory is historically immature, another layer cannot declare it canonically mature.

If land is Permanent Nature, a visual layer cannot treat it as Active Territory.

The representations can differ.

The facts cannot.

> **Different depth.**
>
> **Same canonical reality.**

---

# Technical Events and World Meaning

Not every blockchain event is automatically a world event.

A transfer is technical evidence.

Its canonical consequences depend on what actually changes.

It may affect:

- a balance,
- territorial capacity,
- Farm validity,
- Colonist status,
- future biological development,
- or another defined state.

Or it may have no higher-level world consequence beyond the transfer itself.

Therefore the public architectural direction is:

**TECHNICAL EVENT**  
↓  
**CANONICAL INTERPRETATION**  
↓  
**VALID STATE CHANGE**  
↓  
**WORLD MEANING**

Only supported meaning should reach the user as a canonical world claim.

This prevents an activity interface from inventing narrative merely because technical activity occurred.

> **The UX can translate.**
>
> **The data cannot be fiction.**

---

# Activity Must Remain Grounded

Visible activity should correspond to:

**something that actually happened**

or:

**a deterministic consequence of something that actually happened.**

The dApp must not transform a threshold or transfer into an unsupported Human action.

For example, reaching a numerical condition does not automatically mean:

**A Colonist founded a City**

unless canonical rules actually define that event.

This is a small example of a much larger architectural principle:

> **Meaning must travel from evidence to experience without acquiring fiction on the way.**

---

# Read and Interaction Are Different Directions

Much of the early dApp is observational.

Canonical state moves toward the user:

**CANONICAL STATE**  
↓  
**DATA / WORLD / EXPERIENCE**

That is fundamentally different from an interaction intended to change canonical state.

A visual action cannot acquire canonical authority merely because the interface allows it.

Any future interaction that changes canonical reality must have an explicitly defined canonical meaning and valid supporting evidence.

Therefore:

**CANONICAL → EXPERIENCE**

is a broad representational direction.

But:

**EXPERIENCE → CANONICAL**

requires a valid canonical path.

> **Observation can be broad.**
>
> **Canonical mutation must be explicit.**

The Architecture does not predefine future interaction systems that have not yet been canonically established.

---

# Observation First

The first meaningful layers of Zipvilization are naturally observation-heavy.

SolumTools observes and explains data.

SolumWorld observes and represents the planet.

Early SolumView can observe and experience individual Territory.

This allows the system to develop around:

- correctness,
- History,
- territorial state,
- population,
- maturity,
- representation,
- and observability

before deeper interaction needs to be defined.

This is consistent with the Chapters:

**EXIST → OBSERVE → WORLD → ACT → REMEMBER → EMERGE → ?**

The sequence expresses the DNA of Zipvilization.

It is not a rigid software release schedule.

---

# Human Access

Humans should not need to reconstruct Zipvilization manually from raw blockchain activity.

The architecture allows technical evidence to become world meaning.

A Human can move from:

**address**

to:

**Holder or Colonist**

from:

**balance**

to:

**territorial capacity**

from:

**blocks**

to:

**Time and valid development**

from:

**Burn**

to:

**Permanent Nature**

and from:

**historical state changes**

to:

**the History of a Territory**

The underlying evidence remains available as the foundation.

The dApp makes its meaning understandable.

---

# AI Access

AI requires the same world to be structured explicitly.

It needs to distinguish:

**EVIDENCE**

**CANONICAL**

**DERIVED**

**REPRESENTATIONAL**

**EXPERIMENTAL**

**UNRESOLVED**

Those distinctions prevent AI from treating every documented statement as the same kind of truth.

The authority direction remains:

**BLOCKCHAIN STATE + HISTORY**  
↓  
**CANONICAL RULES**  
↓  
**DETERMINISTIC STATE**  
↓  
**AI INTERPRETATION**

AI can:

- explain,
- relate,
- compare,
- navigate,
- and audit.

It cannot become the source of missing canonical meaning.

> **Humans follow the experience.**
>
> **AI follows the relationships.**

---

# AI Must Stop at the Boundary

A machine-readable architecture creates a specific responsibility.

When information is missing, AI must not fill the gap merely because a plausible answer exists.

When documentation conflicts, AI should identify the conflict.

When a relationship is not canonically defined, AI should not manufacture it.

When a possibility belongs to Horizonte, AI should leave it open.

This protects the architecture from one of the largest risks of highly structured documentation:

**plausible inference becoming false canon.**

> **Structured information improves reasoning.**
>
> **It does not authorize invention.**

---

# Testnet and Canonical State

Test environments can exercise substantial parts of the architecture before Genesis.

They can help explore:

- state interpretation,
- deterministic relationships,
- data presentation,
- world representation,
- Territory entry,
- visual models,
- and possible interaction approaches.

This is real development.

But:

**TESTNET STATE ≠ CANONICAL ZIPVILIZATION STATE**

and:

**TESTNET HISTORY ≠ CANONICAL HISTORY**

Testnet can validate approaches.

It cannot manufacture the real History that begins with the official world.

---

# Progressive Architecture

The world does not need maximum infrastructure before it has maximum complexity.

Pre-Genesis and early Genesis conditions are different from those of a mature Zipvilization.

As the world grows:

- History becomes deeper,
- Colonists can increase,
- Territory can expand,
- population can grow,
- maturity can diversify,
- world representation can gain resolution,
- and local experience can become more demanding.

The architecture must allow the system to grow with that reality.

But increasing scale should not require redefining canonical meaning.

> **Infrastructure grows around the world model.**
>
> **The world model should not change merely to accommodate an interface.**

---

# SolumView Has Different Requirements

SolumTools can become useful with real data and a relatively simple interface.

SolumWorld can become useful with a simple representation of a real planet state.

SolumView is different.

Its intended role is to make individual Territory increasingly experienceable.

That means its deepest UX depends on sufficient real:

- Colonists,
- Territory,
- Farms,
- Zips,
- population,
- maturity,
- activity,
- and History.

Its architecture can be explored before the world reaches that scale.

Testnet models can help.

But its final experiential requirements should not be invented from an empty world.

> **SolumTools can begin with data.**
>
> **SolumWorld can begin with a planet.**
>
> **SolumView needs a living world.**

---

# Observability Without Exposure

A system can be auditable without publishing its internal implementation.

For important canonical claims, the public system should make it possible to understand the relevant semantic path.

For example:

**Why is this address a Colonist?**

**Why does this Territory have this capacity?**

**Why is this land Permanent Nature?**

**Why is this maturity valid?**

**Which defined relationship gives this state its meaning?**

Those are questions about canonical validity.

They should be answerable.

They do not require publishing:

- internal algorithms,
- private infrastructure,
- proprietary engineering methods,
- or operational implementation.

This gives the architecture a useful principle:

> **Explain the validity of the result.**
>
> **Protect the machinery used to produce it efficiently.**

---

# Audit Boundaries

The most important public audit points are semantic boundaries.

### Evidence → Canonical Meaning

Does the claim begin from valid evidence?

### Canonical Meaning → Derived State

Does the derived conclusion follow a defined deterministic relationship?

### Derived State → Representation

Does the interface preserve the meaning of the state it represents?

### Experience → Canonical Interaction

If an interaction can affect canonical state, is that authority explicitly defined?

These questions expose what matters for trust without exposing how the internal system is engineered.

---

# What the Public Architecture Shows

The public Architecture documents:

- authority,
- logical responsibilities,
- canonical dependencies,
- deterministic relationships,
- historical requirements,
- representation boundaries,
- consumer relationships,
- audit boundaries,
- observability principles,
- development maturity,
- and the distinction between canonical state and experience.

This is enough to understand that the dApp rests on a structured system rather than on an interface concept.

---

# What Remains Internal

The Atlas deliberately stops before implementation becomes reproducible.

Internal development includes engineering decisions and methods that are not required to understand or audit canonical meaning.

Those details can remain private.

The public boundary is therefore not:

**real architecture vs hidden architecture**

It is:

**public architecture vs internal implementation**

> **Show the architecture.**
>
> **Protect the implementation.**

This allows Zipvilization to remain transparent about what the system means and how its major responsibilities relate without publishing the engineering knowledge required to reproduce the machine.

---

# Security Is Not Canonical Secrecy

Protecting implementation must never become an excuse for hiding the rules that determine world truth.

Canonical integrity should come from:

- valid evidence,
- explicit rules,
- deterministic relationships,
- and preserved invariants.

Not from asking users to trust an unexplained private process.

The implementation can remain private because it is implementation.

The canonical meaning remains public because it is the world.

> **Know-how can be protected.**
>
> **Canonical meaning must remain understandable.**

---

# Extensible Does Not Mean Predetermined

A modular architecture can support future systems that have not yet been defined.

That does not mean those systems already exist.

Possible future layers may involve:

- deeper interaction,
- relationships,
- specialization,
- cooperation,
- competition,
- institutions,
- politics,
- markets,
- alliances,
- conflict,
- culture,
- or forms not yet anticipated.

These remain possibilities unless and until they are canonically defined.

The architecture can leave room for them without turning them into promises.

> **We define the conditions.**
>
> **We do not define the outcome.**

That unresolved boundary is:

**Horizonte.**

---

# Architecture at a Glance

The dApp Architecture is:

**EVIDENCE-BOUND**

Canonical claims begin from valid technical evidence.

**RULE-BOUND**

Canonical meaning comes from defined rules, not interfaces.

**DETERMINISTIC**

Derived canonical state cannot depend on arbitrary interpretation.

**HISTORICAL**

The present cannot always be understood without the past.

**MODULAR**

Different systems solve different access and representation problems.

**UNIFIED**

Those systems refer to one canonical world.

**REPRESENTATION-AWARE**

Visual interpretation remains downstream from truth.

**OBSERVABLE**

Canonical conclusions can be explained through meaningful relationships.

**AUDITABLE**

The validity of important world claims can be followed without exposing internal implementation.

**PROGRESSIVE**

The technical system can grow with the world.

**AI-READABLE**

Authority and semantic boundaries are explicit enough for machines to follow.

**OPEN**

Undefined future systems remain unresolved.

**PROTECTED**

Public documentation demonstrates the architecture without becoming a reproduction manual.

Its central engineering principle is:

> **Preserve the relationship between what happened, what it means and what the world is allowed to claim.**

---

# From Architecture to Experience

Architecture answers:

> **How can one coherent Zipvilization reality support different depths of access without allowing those surfaces to redefine it?**

The next layer asks:

> **How should Humans and AI experience that architecture?**

That is where:

**DATA**

becomes:

**WORLD**

and eventually:

**LIFE**.

→ **[Continue to dApp Experience](/dapp/experience/)**

---

# Follow the Architecture

### Understand the conceptual model

→ **[dApp Model](/dapp/model/)**

### Follow the Human and AI experience

→ **[dApp Experience](/dapp/experience/)**

### Read the state

→ **[SolumTools](/world/solumtools/)**

### See the planet

→ **[SolumWorld](/world/solumworld/)**

### Enter Territory

→ **[SolumView](/world/solumview/)**

---

# One World, Multiple Depths

The architecture begins with evidence.

Evidence receives canonical meaning.

Canonical meaning allows deterministic state.

State becomes accessible.

Access becomes representation.

Representation becomes experience.

**EVIDENCE**  
↓  
**MEANING**  
↓  
**STATE**  
↓  
**DATA**  
↓  
**WORLD**  
↓  
**LIFE**  
↓  
**?**

The deeper the experience becomes, the more important the authority boundary becomes.

Interfaces can change.

Visual systems can change.

Infrastructure can change.

The experience can become dramatically richer.

But none of those changes should reverse the fundamental direction:

> **Canonical state determines what the dApp is allowed to represent.**
>
> **The dApp does not determine canonical state.**

Beyond the defined architecture:

**Horizonte remains open.**
