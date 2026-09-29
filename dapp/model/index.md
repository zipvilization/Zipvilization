---
layout: default
title: Model
parent: The dApp
nav_order: 1
description: >
  The dApp Model defines how canonical Zipvilization reality becomes readable,
  visible and eventually experienceable through one system without allowing
  representation, interface or simulation to become sources of truth.
permalink: /dapp/model/
---

# The dApp Model

Before asking how the dApp is implemented, we need to define what the dApp actually is.

Zipvilization is not a conventional application with a fictional world behind its interface.

The world has state.

It has rules.

It has Time.

It can accumulate History.

Territory can become active.

Population can emerge.

Maturity can develop.

Permanent changes can occur.

The dApp exists to make that reality increasingly accessible.

> **The dApp is not the world.**
>
> **It is how Humans and AI access the world.**

This distinction is the foundation of the model.

---

# One Canonical Reality

Everything begins with one underlying Zipvilization reality.

There is not:

- one version for SolumTools,
- another for SolumWorld,
- another for SolumView,
- another for Humans,
- and another for AI.

There is one canonical reality that can be accessed at different depths and represented in different ways.

At the highest level:

**BLOCKCHAIN STATE + HISTORY**  
↓  
**CANONICAL RULES**  
↓  
**DETERMINISTIC ZIPVILIZATION STATE**  
↓  
**ACCESS / REPRESENTATION / EXPERIENCE**

This direction is fundamental.

The interface is downstream from truth.

> **One world.**
>
> **Multiple ways to understand it.**

---

# Evidence, Meaning and Experience

The model separates three things that must never be confused.

## Evidence

The blockchain provides technical evidence.

Balances.

Transfers.

Burns.

Blocks.

Addresses.

Contract events.

State changes.

Historical transactions.

These facts exist at the blockchain level.

## Meaning

Canonical Rules determine what valid evidence means inside Zipvilization.

A quantity of SOLUM can correspond to territorial capacity.

A complete Farm threshold can establish Colonist status.

Burned SOLUM can correspond to Permanent Nature.

Valid Farms, Bloch, Time and History can determine biological development.

This is where technical state acquires world meaning.

## Experience

The dApp can then make that meaning:

- readable,
- searchable,
- visible,
- navigable,
- and eventually experienceable.

The direction remains:

**EVIDENCE**  
↓  
**MEANING**  
↓  
**EXPERIENCE**

Never:

**EXPERIENCE**  
↓  
**MEANING**

A representation can communicate truth.

It cannot create truth.

---

# The dApp Does Not Determine Canonical State

This is one of the most important boundaries in the entire architecture.

SolumTools does not decide what a Farm is.

SolumWorld does not decide which Territory exists.

SolumView does not decide which Zips exist.

The interface does not decide whether a Territory is mature.

Those meanings originate upstream.

If an interface displays incorrect information, the interface is wrong.

If a graphical layer shows unsupported Territory, the representation is wrong.

If a local experience contains unsupported canonical population, the experience is wrong.

The canonical world does not change to match the interface.

> **Truth constrains representation.**
>
> **Representation does not constrain truth.**

---

# From Blockchain to Zipvilization

The blockchain does not directly store every Human-readable concept used by Zipvilization.

The model therefore requires translation.

For example:

**ON-CHAIN SOLUM**  
↓  
**TERRITORIAL CAPACITY**

**VALID FARM THRESHOLD**  
↓  
**COLONIST**

**VALID FARM**  
↓  
**BLOCH**

**BLOCK PROGRESSION + VALID STATE + HISTORY**  
↓  
**BIOLOGICAL DEVELOPMENT**

**BURNED SOLUM**  
↓  
**PERMANENT NATURE**

The important point is not that the interface invents these relationships.

It is that the relationships are defined before the interface represents them.

This allows raw technical state to become a coherent world without turning interpretation into arbitrary fiction.

---

# Holder Is Not Colonist

The dApp model must preserve distinctions even when simplifying them would make an interface easier to build.

One of the clearest examples is Colonist status.

The path is:

**ADDRESS**  
↓  
**SOLUM HOLDER**  
↓  
**8,000,000 SOLUM**  
↓  
**8 TILES**  
↓  
**1 COMPLETE FARM**  
↓  
**COLONIST**  
↓  
**ACTIVE TERRITORY**

An address below the complete Farm threshold may hold SOLUM.

It is a Holder.

It is not yet a Colonist.

It does not yet have a complete active Colonist Territory.

That distinction must remain true whether the user is reading a metric, looking at the planet or entering Territory.

> **UX can simplify presentation.**
>
> **UX cannot simplify away canonical meaning.**

→ **[Understand Colonists](/world/colonists/)**

---

# Territory Is a State Relationship

Territory is not merely a colored area on a map.

Its meaning comes from canonical relationships.

At the base:

> **1 SOLUM = 1 m² of Solum**

Territorial capacity can then be expressed through Tiles and higher structures.

But the dApp model must distinguish between:

**balance**

**capacity**

**structure**

**population**

**maturity**

**History**

These concepts are related.

They are not interchangeable.

A wallet can gain capacity without gaining retroactive History.

A territorial structure can exist without being biologically mature.

A mature Territory can have a History that cannot be reconstructed from its current balance alone.

The model therefore treats Territory as more than a current numerical quantity.

→ **[Explore Territories](/world/territories/)**

---

# Current State Is Not Complete History

A blockchain can tell us what exists now.

Its History can tell us how that state came to exist.

Zipvilization needs both.

Consider a Colonist who acquires additional Territory after biological Time has already passed.

The new capacity exists from that point forward.

It does not automatically receive development that would have occurred if that capacity had existed earlier.

Likewise, a later transfer can change future territorial conditions without deleting valid development that occurred before the transfer.

Therefore:

**CURRENT BALANCE**  
≠  
**HISTORICAL TERRITORIAL STATE**

and:

**CURRENT CAPACITY**  
≠  
**HISTORICAL MATURITY**

This is not merely a historical display feature.

It changes what the dApp can validly derive.

> **A snapshot explains the present.**
>
> **History explains how the present became possible.**

---

# The World Has Memory

History is therefore part of the dApp model itself.

It can affect:

- Colonist development,
- territorial development,
- biological progression,
- population,
- maturity,
- previous state,
- and the interpretation of current state.

This means the dApp cannot always answer a question by reading one current balance.

Some questions require temporal reconstruction.

The public model needs to establish that requirement.

The exact internal methods used to reconstruct, index and serve that History belong to implementation.

> **The requirement is public.**
>
> **The implementation can remain internal.**

---

# Territory Provides Capacity

Territorial structure defines capacity.

Canonical scales include:

| Territory | Tiles | SOLUM | Area | Maximum Zip Capacity |
|:----------|------:|------:|-----:|---------------------:|
| Farm | 8 | 8,000,000 | 8 km² | 8 |
| City | 256 | 256,000,000 | 256 km² | 256 |
| State | 8,192 | 8,192,000,000 | 8,192 km² | 8,192 |
| Kingdom | 262,144 | 262,144,000,000 | 262,144 km² | 262,144 |

These scales define total territorial capacity.

They do not mean that each higher structure is composed of 32 complete structures of the previous level.

The actual hierarchy preserves its own Territory:

**CITY**

16 complete Farms  
+  
128 Tiles of City Territory

**STATE**

16 complete Cities  
+  
4,096 Tiles of State Territory

**KINGDOM**

16 complete States  
+  
131,072 Tiles of Kingdom Territory

This distinction matters to the dApp because graphical simplification must not replace structural truth.

> **Scale is not composition.**

---

# Farms Provide Population Origin

Territory provides capacity.

Population needs an origin.

The model connects that origin to Farms.

**1 FARM**  
↓  
**1 BLOCH**  
↓  
**TIME**  
↓  
**ZIP DEVELOPMENT**

The Farm is therefore both:

- the minimum active territorial structure,
- and the primary population-generating territorial structure.

Higher Territories provide additional capacity.

They do not introduce independent population generators.

This creates one scalable biological model instead of separate arbitrary mechanisms for Farms, Cities, States and Kingdoms.

> **Generation comes from Farms.**
>
> **Capacity comes from Territory.**

→ **[Discover Zips](/world/zips/)**

---

# Time Provides Progression

Blockchain blocks provide a measurable progression.

Zipvilization gives part of that progression biological meaning.

A biological cycle corresponds to:

> **65,536 blockchain blocks**

But elapsed blocks alone are not sufficient to invent population.

Biological development depends on valid relationships between:

**TERRITORY**  
+  
**FARMS**  
+  
**BLOCH**  
+  
**AVAILABLE CAPACITY**  
+  
**TIME**  
+  
**HISTORY**

The dApp model therefore does not treat Time as a universal counter that independently generates world state.

Time operates on valid state.

> **Time provides progression.**
>
> **State determines what can progress.**
>
> **History determines what validly occurred.**

→ **[Understand Time](/world/time/)**

---

# Population and Maturity Are Different

Population is not simply another name for territorial capacity.

And capacity is not maturity.

A Territory can have room for more Zips than currently exist.

A City-scale Territory can exist before that City becomes biologically mature.

A State-scale capacity can exist before the historical conditions required for State maturity have occurred.

The dApp must therefore preserve separate concepts for:

**capacity**

**population**

**development**

**maturity**

**History**

This separation allows the same world to change through Time without redefining its territorial mathematics.

---

# Land Has Different States

Not all Solum has the same relationship with Civilization.

The model distinguishes three fundamental land states:

## Dormant Land

Land outside active Colonist Territory that remains potentially available.

Its principal on-chain reserve corresponds to Pool-held SOLUM.

## Active Territory

Territory associated with valid Colonist development beginning from the complete Farm threshold.

It can participate in biological development and History.

## Permanent Nature

Land represented by SOLUM removed through Burn.

It remains part of Solum.

But it is permanently unavailable to Civilization.

These states must remain distinguishable across the entire dApp.

**DORMANT**  
≠  
**ACTIVE**  
≠  
**PERMANENT**

SolumTools can expose them as data.

SolumWorld can represent them spatially.

SolumView can eventually encounter their local consequences.

The underlying meaning remains the same.

---

# Deterministic Where Truth Requires It

The dApp does not need every aspect of the world to be deterministic.

It needs canonical claims to be deterministic where Canon defines them.

For example:

- whether a complete Farm exists,
- whether an address has crossed the Colonist threshold,
- how much territorial capacity exists,
- how many valid Farms exist,
- whether SOLUM was burned,
- how much valid biological Time has elapsed,
- and whether historical conditions support a maturity state

cannot depend on visual interpretation.

But other aspects can remain interpretative.

Terrain style.

Lighting.

Camera.

Animation.

Atmosphere.

Graphical abstraction.

Interface layout.

These can evolve.

The distinction is:

> **Canonical meaning must be reproducible from valid evidence and rules.**
>
> **Representation can remain creative.**

---

# Three Access Layers

The dApp model currently organizes access to the world through three principal layers.

They are not three different worlds.

They are three depths of the same one.

---

## SolumTools — Read

SolumTools is the data and interpretation layer.

It makes blockchain state and History readable as Zipvilization.

Its responsibility is to answer questions such as:

- How many Colonists exist?
- How much Territory is active?
- How much remains Dormant?
- How much has become Permanent Nature?
- How many Farms exist?
- What population is valid?
- What maturity is historically supported?
- What happened?

Its fundamental direction is:

**STATE + HISTORY**  
↓  
**CANONICAL MEANING**  
↓  
**READABLE DATA**

> **SolumTools makes the world understandable.**

→ **[Explore SolumTools](/world/solumtools/)**

---

## SolumWorld — See

SolumWorld is the graphical world representation.

It takes valid world state and gives it spatial form.

At broad scale it can begin with:

- Dormant Land,
- Active Territory,
- Permanent Nature.

As the world grows, increasing depth can reveal:

- Colonists,
- territorial structures,
- population,
- maturity,
- History,
- and individual Territory.

Its fundamental direction is:

**VALID WORLD STATE**  
↓  
**SPATIAL REPRESENTATION**

> **SolumWorld makes Solum visible.**

→ **[Explore SolumWorld](/world/solumworld/)**

---

## SolumView — Enter

SolumView begins when observation becomes territorial experience.

It can move inside individual Colonist Territory and eventually make increasingly local consequences of state and History experienceable.

Its possible depth includes:

- Farms,
- Zips,
- population,
- movement,
- construction,
- development,
- maturity,
- and local History.

Its fundamental direction is:

**VALID TERRITORIAL STATE + HISTORY**  
↓  
**LOCAL EXPERIENCE**

> **SolumView makes Territory experienceable.**

→ **[Explore SolumView](/world/solumview/)**

---

# Read → See → Enter

Together:

**SOLUMTOOLS**  
↓  
**READ**

**SOLUMWORLD**  
↓  
**SEE**

**SOLUMVIEW**  
↓  
**ENTER**

This can continue conceptually:

**READ**  
↓  
**SEE**  
↓  
**ENTER**  
↓  
**EXPERIENCE**  
↓  
**INTERACT**  
↓  
**?**

This is an experiential progression.

It should not be interpreted as a mandatory release sequence.

SolumTools and SolumWorld can develop in parallel.

SolumView can also be prototyped and tested while the live world is still young.

What differs is the amount of real state required for each layer to fulfill its purpose.

> **Architecture can develop in parallel.**
>
> **Experience depends on what the world actually contains.**

---

# Data → World → Life

The same model can be expressed another way:

**DATA**  
↓  
**WORLD**  
↓  
**LIFE**

This does not mean that life is generated by a graphical layer.

It describes increasing Human experiential depth.

At DATA level, the user understands state.

At WORLD level, the user sees that state as part of Solum.

At LIFE level, the user enters the local consequences of that state.

One reality.

Increasing resolution.

Increasing context.

Increasing experience.

---

# The Interface Can Be Simple

The complexity of the underlying model does not require the first interface to expose everything simultaneously.

SolumTools can begin with a relatively simple information interface.

SolumWorld can begin with a relatively simple planetary representation.

That simplicity is compatible with a much deeper architecture underneath.

The interface can become richer without redefining:

- Holder,
- Colonist,
- Farm,
- Territory,
- Bloch,
- Time,
- population,
- maturity,
- History,
- or land state.

> **Surface complexity can grow.**
>
> **Canonical meaning should remain stable.**

---

# SolumView Has a Different Dependency

SolumView cannot be treated exactly like the first two layers.

A simple data table can already make SolumTools useful.

A simple planet can already make SolumWorld useful.

But SolumView exists to make a Territory feel inhabited and increasingly alive.

That requires enough real world beneath it.

Its conceptual architecture can exist before Genesis.

Its technical models can be tested before Genesis.

Its possible interfaces can be prototyped before Genesis.

But its deeper UX needs evidence from a sufficiently meaningful base of real:

- Colonists,
- Territory,
- Farms,
- population,
- Zips,
- maturity,
- activity,
- and History.

> **SolumTools can begin with data.**
>
> **SolumWorld can begin with a planet.**
>
> **SolumView needs a living world.**

---

# Testnet and Canonical Reality

The model distinguishes test environments from canonical Zipvilization.

Testnet can help validate:

- relationships,
- data flows,
- technical assumptions,
- graphical models,
- navigation,
- Territory entry,
- simulations,
- and possible interactions.

That work is real development.

But testnet activity is not canonical Zipvilization History.

Therefore:

**TESTNET MODEL**  
≠  
**CANONICAL WORLD**

A prototype can demonstrate that an architectural approach works.

It cannot manufacture the real historical evidence that only a live world can produce.

---

# Defined Does Not Mean Live

The dApp model distinguishes several kinds of project maturity.

## Defined

The relationship is known and documented.

## Implemented

A technical realization of that relationship exists.

## Tested

The implementation or model has been exercised under test conditions.

## Live

The official system is producing canonical state and History.

## Data-dependent

Further development requires enough real state or History to learn from actual behavior.

## Open

The outcome has intentionally not been predetermined.

These categories should not be collapsed.

A system can be deeply defined without being live.

A test can be meaningful without becoming canonical History.

A future possibility can remain open without being an architectural omission.

---

# Observation Does Not Mean Control

The dApp gives Humans and AI increasing access to Zipvilization.

That does not mean the observer controls the world simply by observing it.

Reading Territory does not change Territory.

Opening SolumWorld does not create land state.

Entering SolumView does not create Zips.

AI interpreting History does not rewrite History.

The dApp can eventually support interactions where explicit actions do change valid state.

Those interactions must be distinguished from observation.

> **Observation reveals.**
>
> **Valid interaction can act.**
>
> **Neither should be confused with invention.**

---

# Human Access

Humans should not need to reconstruct Zipvilization manually from raw blockchain state.

The dApp translates technical evidence into concepts that belong to the world.

Instead of only:

**0x...**

a Human can understand:

**Colonist**

Instead of only:

**token balance**

a Human can understand:

**territorial capacity**

Instead of only:

**block difference**

a Human can understand:

**biological progression**

Instead of only:

**burn transaction**

a Human can understand:

**Permanent Nature**

Instead of only:

**historical events**

a Human can understand:

**how a Territory developed**

The technical evidence remains underneath.

The Human experience becomes increasingly natural.

---

# Machine Access

AI needs the same world expressed differently.

It needs explicit relationships.

Authority.

Dependencies.

State distinctions.

Historical boundaries.

Deterministic rules.

Unresolved concepts.

It must be able to distinguish:

**CANONICAL**

**DERIVED**

**EXPERIMENTAL**

**REPRESENTATIONAL**

**UNRESOLVED**

This allows AI to help explain the world without silently extending it.

> **Humans follow the experience.**
>
> **AI follows the relationships.**

The dApp model supports both.

---

# AI Is Not an Authority Layer

AI can help:

- interpret,
- explain,
- connect,
- navigate,
- compare,
- audit,
- and make complex state understandable.

It cannot independently decide what canonical state means.

The authority chain does not become:

**STATE → AI → WORLD**

It remains:

**STATE + HISTORY**  
↓  
**CANONICAL RULES**  
↓  
**DETERMINISTIC STATE**

AI operates over that structure.

If information is missing, AI should identify the gap.

If two sources conflict, AI should report the conflict.

If a concept is unresolved, AI should not resolve it by inference.

If something belongs to Horizonte, AI should leave it open.

---

# Representation Can Be Rich

The model deliberately leaves substantial creative freedom at the representational layer.

A world does not need to look like a database.

Territory can have visual identity.

Zips can move.

Cities can feel inhabited.

History can leave visible consequences.

SolumView can eventually become deeply experiential.

The restriction is not against creativity.

It is against turning creativity into unsupported canonical claims.

> **Representation may be richer than raw data.**
>
> **Its factual claims cannot be.**

---

# Civilization Is Not a Database Field

The dApp can understand many deterministic relationships.

Civilization itself should not be reduced to one metric or switch.

It can emerge from relationships between:

**TERRITORY**  
+  
**ZIPS**  
+  
**TIME**  
+  
**HISTORY**  
+  
**HUMAN PARTICIPATION**  
+  
**INTERACTION**

Possible future consequences may include:

- specialization,
- cooperation,
- competition,
- social structures,
- institutions,
- culture,
- politics,
- markets,
- alliances,
- conflict,
- and forms not yet defined.

These are possibilities.

They are not automatically current systems.

The dApp model must be capable of growing without pretending those outcomes already exist.

→ **[Explore Civilization](/world/civilization/)**

---

# The Model Has a Boundary

A strong model does not need to define everything.

It needs to define what must remain stable and identify where certainty ends.

Zipvilization already defines substantial foundations.

But not every future interaction.

Not every future institution.

Not every future behavior.

Not every possible consequence of a mature Civilization.

The model therefore ends with:

**?**

That question mark is not a missing module.

It is a boundary.

**Horizonte.**

> **The foundation is defined.**
>
> **The possibilities are not.**

→ **[Explore Horizonte](/trinomial/horizonte/)**

---

# Public Model, Protected Implementation

The dApp Model can be documented openly because understanding it does not require publishing the internal machinery used to execute it.

Public documentation can explain:

- concepts,
- authority,
- inputs,
- outputs,
- relationships,
- invariants,
- dependencies,
- state transitions,
- and canonical boundaries.

That is necessary for Humans and AI to understand the system.

It also makes major claims auditable.

But the Model does not need to disclose:

- exact algorithms,
- internal data structures,
- complete indexing strategies,
- reconstruction implementations,
- infrastructure topology,
- optimization techniques,
- private tooling,
- or implementation-specific operational logic.

Those belong to Architecture and implementation at different levels of disclosure.

The distinction is:

> **The rules of the world should be understandable.**
>
> **The internal machinery used to operate them does not need to be reproducible from the Atlas.**

---

# Model Invariants

Any implementation of the dApp must preserve a number of fundamental invariants.

### One canonical reality

Different interfaces cannot create different truths.

### Authority flows downward

Representation cannot become a source of canonical state.

### Holder and Colonist remain distinct

A complete Farm threshold is required for Colonist status.

### Territory and capacity remain deterministic

Graphical representation cannot redefine territorial mathematics.

### Generation and capacity remain distinct

Farms provide population origin.

Territory provides population capacity.

### Current state does not overwrite History

Later state changes cannot retroactively rewrite valid development.

### Capacity does not equal maturity

Historical development remains necessary.

### Dormant, Active and Permanent remain distinct

Representation cannot collapse their meanings.

### Testnet is not canonical History

Testing can validate architecture without becoming the world.

### Simulation is not canonical evidence

Visual life can be richer than recorded state without becoming false History.

### Horizonte remains unresolved

The system cannot infer what has deliberately not been defined.

These invariants matter more than any particular interface design.

---

# What the Model Does Not Define

The Model deliberately does not define every implementation decision.

It does not specify:

- the exact backend topology,
- the exact indexing architecture,
- database schemas,
- caching strategy,
- infrastructure providers,
- internal APIs,
- rendering engines,
- graphical style,
- final SolumView interaction model,
- every future Zip behavior,
- every possible profession,
- every future institution,
- or the outcome of Civilization.

Those questions belong either to:

**Architecture,**

**Experience,**

**internal implementation,**

or:

**Horizonte.**

Keeping those categories separate prevents the public model from becoming either vague or unnecessarily revealing.

---

# The Model at a Glance

The dApp Model is:

**CANONICAL**

It begins from defined Zipvilization meaning.

**STATE-BOUND**

Its factual claims require valid evidence.

**HISTORICAL**

Current state alone cannot explain every valid world state.

**DETERMINISTIC WHERE REQUIRED**

Canonical meaning cannot depend on visual interpretation.

**MODULAR**

Different layers solve different problems.

**UNIFIED**

Those layers access one world.

**HUMAN-READABLE**

Technical evidence can become understandable world concepts.

**MACHINE-READABLE**

Relationships and authority can be followed by AI.

**REPRESENTATION-AWARE**

Visual richness remains distinct from canonical truth.

**TESTABLE**

Substantial architecture can be explored before Genesis.

**DATA-DEPENDENT WHERE NECESSARY**

Some deeper experience requires real quantitative History.

**OPEN**

The model defines foundations without predetermining Civilization.

Its central rule is:

> **One canonical reality can support many depths of experience, but no depth of experience can redefine canonical reality.**

---

# From Model to Machine

The Model tells us what relationships must exist.

The next question is:

> **How can a system support those relationships?**

That is the role of the dApp Architecture.

Architecture takes concepts such as:

- state,
- History,
- derivation,
- Territory,
- Time,
- population,
- maturity,
- and representation

and organizes them into a machine capable of supporting the dApp.

But there is a deliberate boundary.

We can expose enough architecture to demonstrate that the machine is real.

We do not need to publish enough implementation detail to reproduce it.

→ **[Continue to dApp Architecture](/dapp/architecture/)**

---

# Follow the Model

### How is the system organized underneath?

→ **[Architecture](/dapp/architecture/)**

### How does it become a Human and AI experience?

→ **[Experience](/dapp/experience/)**

### How does canonical state become readable?

→ **[SolumTools](/world/solumtools/)**

### How does canonical state become a world?

→ **[SolumWorld](/world/solumworld/)**

### How does Territory become experienceable?

→ **[SolumView](/world/solumview/)**

---

# One World

The model begins before the interface.

The blockchain records evidence.

History preserves change.

Canonical Rules define meaning.

Deterministic relationships create a coherent state of Zipvilization.

The dApp opens that state to Humans and AI.

First as data.

Then as a world.

Eventually as life.

**EVIDENCE**  
↓  
**MEANING**  
↓  
**DATA**  
↓  
**WORLD**  
↓  
**LIFE**  
↓  
**?**

The deeper the experience becomes,

the more important it is that the foundations remain unchanged.

> **The interface can evolve.**
>
> **The representation can evolve.**
>
> **The experience can evolve.**
>
> **The underlying truth must remain coherent.**

Beyond the defined model:

**Horizonte remains open.**
