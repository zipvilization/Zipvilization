---
layout: default
title: Metrics
nav_order: 6
description: >
  Metrics is the public measurement layer of Zipvilization. It presents
  selected, verifiable indicators about Solum, Colonists, Territories, Zips,
  maturity, Permanent Nature, Dormant Land, and the evolving state of the world.
permalink: /metrics/
---

# Metrics

Zipvilization is an experiment.

Experiments need evidence.

Ideas matter.

Architecture matters.

Rules matter.

But eventually we need to ask:

> **What is actually happening?**

That is the purpose of **Metrics**.

Metrics presents selected measurements of the real state and development of Zipvilization.

It does not define the world.

It does not create state.

It does not decide what success should look like.

It measures what can be measured.

> **SolumTools translates state into observable Zipvilization data.**
>
> **Metrics turns selected data into a public view of the experiment.**

→ **[Explore SolumTools](/world/solumtools/)**  
→ **[Explore SolumWorld](/world/solumworld/)**

---

# Evidence before narrative

Zipvilization should never need to say:

> Trust us. The world is growing.

We should be able to show it.

How much Solum remains dormant?

How much territory is controlled by Colonists?

How much has become Permanent Nature?

How many Farms exist?

How many Cities are developing?

How many Territories are mature?

How many Zips have emerged?

How much biological time has accumulated?

How concentrated is territorial ownership?

How is the world changing?

These questions should increasingly have measurable answers.

Metrics exists to make those answers visible.

---

# What Metrics is

Metrics is a presentation layer built on measurable state.

Its role is to:

**select**

important indicators,

↓

**organize**

them into meaningful groups,

↓

**present**

them clearly,

↓

**link**

them back to the underlying state and rules.

A metric should not exist merely because a number is available.

It should help us understand the world.

---

# What Metrics is not

Metrics is not:

- a marketing dashboard,
- a token-price page,
- a promise of growth,
- a leaderboard by default,
- a substitute for SolumTools,
- a substitute for SolumWorld,
- or a source of canonical state.

If Metrics displays incorrect information, the world has not changed.

The metric is wrong.

Authority remains below the presentation layer.

---

# The measurement chain

The measurement architecture begins with blockchain state.

**Smart Contract**

executes.

↓

**Blockchain**

records.

↓

**Canonical Rules**

define how valid state is interpreted inside Zipvilization.

↓

**SolumTools**

reads, derives and translates that state into deterministic Zipvilization data.

↓

**Metrics**

selects and presents measurements.

↓

**SolumWorld / SolumView**

can use the same grounded data to represent and experience the world.

This distinction matters.

> **The blockchain preserves the state.**
>
> **Canonical Rules define its meaning inside Zipvilization.**
>
> **SolumTools translates that state into observable world data.**
>
> **Metrics measures it.**
>
> **SolumWorld and SolumView give it visual form.**

No presentation layer creates canonical truth.

→ **[Explore Canonical Rules](/smart-contract/canonical-rules/)**

---

# From SOLUM to Territory

Territorial metrics require a deterministic translation from the on-chain unit to the territorial architecture.

The fundamental relationship begins with:

> **1 SOLUM = 1 m²**

But the operational territorial model does not need to process civilization only as individual square metres.

Zipvilization introduces a larger deterministic territorial unit:

> **1 Tile = 1,000,000 SOLUM**
>
> **1 Tile = 1,000,000 m²**
>
> **1 Tile = 1 km²**

The Tile connects raw SOLUM balances to the territorial structure used by the world.

This produces the basic translation:

**SOLUM**

↓

**Tiles**

↓

**Farms**

↓

**higher territorial structures**

The relationship is deterministic.

The graphical representation may evolve.

The underlying quantities may not.

---

# The territorial scale

The territorial hierarchy follows a fixed ×32 scale.

| Level | Tiles | SOLUM | Area |
|:--|--:|--:|--:|
| Farm | 8 | 8,000,000 | 8 km² |
| City | 256 | 256,000,000 | 256 km² |
| State | 8,192 | 8,192,000,000 | 8,192 km² |
| Kingdom | 262,144 | 262,144,000,000 | 262,144 km² |

Therefore:

**1 City = 32 Farm-equivalents**

**1 State = 32 City-equivalents**

**1 Kingdom = 32 State-equivalents**

These equivalences describe total territorial scale.

They should not be confused with graphical composition.

---

# Mathematical scale is not graphical composition

Zipvilization distinguishes between:

**territorial quantity**

and

**territorial representation.**

A City contains 256 Tiles mathematically.

Its graphical territorial structure can represent that capacity as:

**16 Farms**

plus

**City-level territory.**

The 16 Farms occupy:

`16 × 8 = 128 Tiles`

The remaining:

`128 Tiles`

belong to the City-level representation.

Together:

`128 + 128 = 256 Tiles`

The same structural principle can extend upward.

A higher level integrates visible lower-level structures while also introducing territory belonging to its own scale.

This allows the world to remain mathematically exact without requiring every higher territorial level to be rendered simply as 32 identical copies of the level below.

> **Mathematical equivalence does not require graphical equivalence.**

SolumWorld and SolumView may interpret territorial structure visually.

They may not alter its underlying quantity.

---

# The Farm is the primary territorial unit

For measurement, maturity and historical reconstruction, the most important territorial structure is the **Farm**.

> **The Farm is the primary territorial unit of maturity.**

A Farm requires:

**8 Tiles**

which represents:

**8,000,000 SOLUM**

and:

**8 km² of Territory.**

Higher territorial levels organize much larger quantities of Territory.

But they do not erase the primary structure beneath them.

This matters computationally.

A City does not make its underlying primary territory disappear.

A State does not erase the territorial development that preceded it.

A Kingdom does not replace its historical foundations.

The hierarchy accumulates.

It does not overwrite.

---

# Why the Farm matters to the backend

Colonist Territory can change.

A Colonist may:

- acquire SOLUM,
- receive SOLUM,
- transfer SOLUM,
- sell SOLUM,
- receive reflection where applicable,
- expand Territory,
- reduce Territory,
- later acquire Territory again.

If historical reconstruction depended only on the Colonist's current highest territorial label, changes could become difficult to interpret consistently.

The primary territorial model provides a stable reference.

Conceptually:

**Blockchain history**

↓

**SOLUM state**

↓

**Tile state**

↓

**primary territorial state**

↓

**maturity**

↓

**higher territorial interpretation**

This makes it possible to reconstruct development from the underlying territorial structure rather than treating City, State or Kingdom as isolated historical objects.

> **Higher levels organize the Territory.**
>
> **The primary territory preserves the computational reference.**

This distinction is fundamental for SolumTools.

---

# Territory and Zips share the same substrate

The Tile also connects Territory with population capacity.

> **1 Tile = capacity for 1 Zip**

Therefore the territorial scale also establishes maximum Zip capacity:

| Level | Tiles | Maximum Zip capacity |
|:--|--:|--:|
| Farm | 8 | 8 |
| City | 256 | 256 |
| State | 8,192 | 8,192 |
| Kingdom | 262,144 | 262,144 |

This does not mean all potential Zips exist immediately.

Territory establishes capacity.

Time establishes emergence.

> **Territory defines possibility.**
>
> **Time turns possibility into population.**

→ **[Discover Zips](/world/zips/)**  
→ **[Understand Time](/world/time/)**

---

# Maturity begins at the primary territory

A complete Farm has capacity for 8 Zips.

Its population does not appear at once.

Zips emerge progressively through canonical biological cycles.

The base sequence is:

**1 Zip**

↓

**2 Zips**

↓

**3 Zips**

↓

**...**

↓

**8 Zips**

When the primary territorial unit completes its biological development, that primary territory is mature.

If sufficient Territory exists for a higher territorial level, development can continue at the next scale.

The higher levels therefore build on completed primary development rather than replacing it.

This creates a progression in which:

**Territory**

provides capacity,

**Time**

provides development,

and

**Zips**

express biological emergence.

---

# Maturity must remain reconstructable

This architecture has an important consequence.

Maturity should not be treated only as a current label.

It is part of history.

A Colonist's present Territory may differ from their Territory at an earlier block.

The measurement system should therefore be capable of asking:

- how much Territory existed,
- how it was organized,
- which primary territorial structures existed,
- how much maturity had accumulated,
- how many Zips could have emerged,
- and which higher territorial states were valid

at a given point in history.

The stable reference remains the primary territorial structure.

This makes historical reconstruction possible even when Territory later changes.

> **Current state tells us what exists now.**
>
> **Primary territorial history helps explain how it got there.**

---

# The world itself is the main metric

The most important measurements in Zipvilization may not be financial.

They may describe the transformation of the planet.

At Genesis, most of the world is Dormant Land.

If participation grows, that balance changes.

Some Solum enters active civilization.

Some becomes Permanent Nature.

Territories develop.

Zips emerge.

History accumulates.

One of the simplest long-term views of Zipvilization may therefore be:

**Dormant Land**

vs.

**Colonized Territory**

vs.

**Permanent Nature**

That single relationship can tell us something fundamental:

> **How much of the original barren world has changed?**

→ **[Discover Solum](/world/solum/)**

---

# Dormant Land

Dormant Land represents Solum still waiting outside active civilization.

Metrics may eventually show:

- total Dormant Land,
- percentage of the world still dormant,
- historical change,
- rate of transition into active territory,
- and distribution over time.

This is not merely a supply statistic.

It is a measurement of unrealized world potential.

At Genesis, Dormant Land may dominate.

Over time, it may recede.

If it does, that transformation should be observable.

---

# Permanent Nature

Burn creates one of the most consequential measurable states in Zipvilization.

Technically:

Solum leaves circulation permanently.

Inside the world:

that territory becomes **Permanent Nature**.

Metrics may expose:

- total burned Solum,
- percentage of the finite world now permanent,
- historical growth of Permanent Nature,
- and its relationship to active civilization.

Permanent Nature is especially important because it records an irreversible decision.

That makes it more than a token statistic.

It is part of the historical geography of Zipvilization.

→ **[Understand Burn](/smart-contract/burn/)**

---

# Colonists

Participation is central to the experiment.

Metrics should therefore help us understand not only how much Solum exists, but how broadly participation is distributed.

Potential indicators include:

- number of Holders,
- number of Colonists under the canonical interpretation,
- distribution of Solum,
- concentration,
- new participants over time,
- active territorial positions,
- and Founding Colonist participation where relevant.

The objective is not to turn every participant into a ranking.

The objective is to understand whether the world is becoming populated by independent actors.

→ **[Discover Colonists](/world/colonists/)**

---

# Territories

Territorial development creates another major group of measurements.

Metrics may show:

- Tiles,
- Farms,
- Cities,
- States,
- Kingdoms,
- developing Territories,
- mature Territories,
- territorial distribution,
- residual Territory,
- and concentration by scale.

But these measurements must remain derived from the underlying territorial mathematics.

A higher-level structure is not an arbitrary label.

It represents a deterministic quantity and organization of Territory.

At the same time:

A City is not necessarily a mature City.

A Kingdom is not automatically powerful.

A large Territory is not automatically successful.

Metrics should measure the state.

It should not invent meaning beyond the canonical definitions.

→ **[Explore Territories](/world/territories/)**

---

# Zips

Zips provide the biological dimension of the world.

Potential metrics include:

- total Zip population,
- maximum Zip capacity,
- emerged Zips,
- Zips by territorial level,
- mature biological cores,
- developing biological structures,
- total information expressed in bits or bytes,
- and biological growth over time.

Because:

> **1 Zip = 1 bit**

the same state can be presented in both biological and computational language.

And because:

> **1 Tile = capacity for 1 Zip**

population capacity remains mathematically grounded in Territory.

But again:

**capacity is not population.**

And:

**population is not civilization.**

Metrics must not collapse those concepts.

→ **[Discover Zips](/world/zips/)**

---

# Time and maturity

Time creates measurable development.

Metrics can expose:

- completed cycles,
- biological maturity,
- age of primary Territories,
- higher-level maturity,
- historical maturation events,
- distance to future milestones,
- and cumulative developmental progression.

The canonical unit remains:

> **1 cycle = 65,536 blocks**

Human-readable estimates may be presented where useful.

But they should remain clearly identified as translations of canonical block progression.

The calculation architecture should remain capable of tracing higher-level development back to the primary territorial structure from which it emerged.

→ **[Understand Time](/world/time/)**

---

# Economic signals

As Zipvilization develops, economic mechanisms can create measurable flows.

Taxes are one example.

Future Chapters may introduce others.

Metrics may eventually display:

- tax flows,
- distribution,
- accumulation,
- territorial economic activity,
- production,
- exchange,
- or other canonical economic indicators.

But only after those mechanics exist.

A future idea should never appear in Metrics as current state.

> **Conceptual is not measurable.**
>
> **Implemented and active can become measurable.**

→ **[Explore the Smart Contract](/smart-contract/)**  
→ **[Explore the Chapters](/chapters/)**

---

# Metrics should reveal concentration

Territorial concentration matters to the experiment.

A finite world controlled by a handful of participants may behave very differently from one distributed across thousands of independent Colonists.

Metrics should therefore be capable of exposing concentration honestly.

That does not mean concentration is automatically wrong.

It means it should be visible.

The experiment should be able to observe the consequences of its own distribution.

This is especially relevant to:

**Fair Access**

and

**participation before investment.**

→ **[Explore Fair Access](/smart-contract/fair-access/)**  
→ **[Read the Principles](/principles/)**

---

# Metrics are not a leaderboard

A measurement system can easily become competitive by default.

Largest Holder.

Largest Kingdom.

Most Zips.

First City.

Most Permanent Nature.

Some rankings may eventually be interesting.

But they should not become the primary way Zipvilization understands itself.

The project is not trying to answer only:

> Who has the most?

It is trying to answer:

> **What is happening to the world?**

That requires broader measurements.

Distribution.

Development.

Maturity.

Participation.

Transformation.

History.

The world matters more than the ranking.

---

# Current state and historical change

A snapshot is useful.

A timeline is often more meaningful.

Metrics should eventually be able to distinguish:

**current state**

from

**historical evolution.**

For example:

Current Dormant Land tells us how much remains.

Historical Dormant Land tells us how quickly the world changed.

Current mature Cities tell us what exists.

Historical territorial reconstruction tells us how that development emerged from primary Territory.

Current Permanent Nature tells us how much exists.

Historical Burn tells us when irreversible decisions were made.

Current Zip population tells us how many have emerged.

Historical maturity tells us how that population developed through Time.

The world is not only a state.

It is a sequence.

---

# Metrics and SolumTools

SolumTools is the data foundation of the dApp.

It reads blockchain state and history and applies canonical relationships to translate them into Zipvilization.

That translation can include:

- SOLUM,
- Tiles,
- primary Territory,
- higher territorial structures,
- maturity,
- Zips,
- Dormant Land,
- Permanent Nature,
- Colonists,
- and historical transitions.

Metrics selects some of those deterministic signals for public presentation.

For example:

SolumTools may expose signals representing:

- dormant land,
- permanent nature,
- primary territorial units,
- mature Cities,
- Zip population,
- completed cycles.

Metrics may present them as human-readable measurements.

Any numerical examples used in documentation must remain clearly illustrative.

Real Metrics must always come from current canonical state.

> **Never use example data as live data.**

This distinction is especially important for Artificial Intelligence.

→ **[Explore SolumTools](/world/solumtools/)**

---

# Metrics, SolumWorld and SolumView

Metrics, SolumWorld and SolumView can consume different views of the same grounded data.

Their roles are different.

**Metrics**

measures and presents selected indicators.

**SolumWorld**

gives the global state visual form.

**SolumView**

can bring an individual Territory to life.

The graphical layers may aggregate, simplify or simulate visual activity where their own rules allow it.

They may not rewrite the underlying territorial mathematics.

For example:

a City does not need to display 256 literal square objects merely because it contains 256 Tiles.

But its representation cannot imply a territorial state incompatible with those 256 Tiles.

> **The data defines the limits of the representation.**
>
> **The representation does not redefine the data.**

---

# Metrics and Artificial Intelligence

AI should be able to distinguish several categories clearly:

**Canonical state**

what exists.

**Derived state**

what deterministic canonical relationships allow the system to calculate from that state.

**Metric**

a selected measurement of canonical or derived state.

**Representation**

how valid state is presented visually or experientially.

**Interpretation**

what someone believes the measurement may imply.

For example:

> Territorial concentration increased.

may be a measurable fact.

> The civilization is becoming politically unstable.

would be an interpretation unless a canonical system defines such a state.

AI must not turn interpretation into measurement.

It must also not turn graphical representation into canonical quantity.

The correct path is:

**State**

↓

**Deterministic derivation**

↓

**Metric**

↓

**Evidence**

↓

**Interpretation, clearly identified**

→ **[Explore Artificial Intelligence](/trinomial/artificial-intelligence/)**

---

# Metrics must be traceable

An important public metric should ideally provide a path back toward its source.

A user should be able to move from:

> **Mature Cities: X**

toward:

- the relevant SolumTools signal,
- the canonical definition of maturity,
- the primary territorial calculation,
- the territorial threshold,
- the relevant biological rules,
- the underlying block history,
- and ultimately the technical source.

This is the same architecture used across the Atlas.

**Summary**

↓

**Explanation**

↓

**Canonical rule**

↓

**Derived state**

↓

**Blockchain state**

↓

**Technical source**

A human can stop when the answer is sufficient.

An AI can continue until the evidence is explicit.

---

# Metrics should admit uncertainty

Not everything will always be measurable.

Some states may depend on systems that do not yet exist.

Some historical data may not yet be indexed.

Some metrics may require further technical infrastructure.

Some interpretations may remain unresolved.

When that happens, Metrics should say so.

**Unavailable**

is better than invented.

**Not yet measurable**

is better than estimated without basis.

**Unknown**

is better than false precision.

This principle protects the credibility of the experiment.

---

# What should be measurable first?

At the beginning, the most useful Metrics are likely to be foundational.

## World

- total SOLUM,
- Dormant Land,
- active SOLUM,
- Permanent Nature.

## Participation

- Holders,
- Colonists,
- distribution,
- concentration.

## Territory

- Tiles,
- primary territorial units,
- Farms,
- Cities,
- States,
- Kingdoms,
- developing vs. mature structures.

## Biology

- maximum Zip capacity,
- emerged Zips,
- mature biological structures,
- cycles completed.

## Time

- current canonical progression,
- primary territorial maturity,
- historical maturation.

## Contract

- relevant public flows,
- Taxes,
- Burn,
- and other implemented canonical mechanics.

The exact public dashboard can evolve.

The categories provide the initial structure.

---

# Civilization will create new metrics

The metrics available at any moment depend on what Zipvilization can actually observe and what canonical systems exist.

Genesis begins with relatively simple measurable state.

As new structural layers become meaningful, new classes of observation become possible.

The Chapters describe that progression.

They do not prescribe a sequence of economic or political systems.

For example:

**Genesis** can expose:

- Supply,
- balances,
- transactions,
- Burn,
- Pool state.

**Observability** can make those signals structured and legible.

**Territory & World Coherence** can introduce measurable world relationships such as:

- Tiles,
- Dormant Land,
- Permanent Nature,
- territorial distribution,
- territorial capacity,
- primary territorial structures.

**Colonists & Roles** can introduce measurements related to:

- Colonists,
- participation,
- observable behavior,
- canonically defined roles.

**Time, History & Evolution** can introduce:

- Zips,
- developmental cycles,
- territorial maturity,
- historical transitions,
- accumulated change.

**Emergence** can eventually make entirely new classes of metrics meaningful as canonical civilization systems develop.

These could potentially include:

- production,
- specialization,
- economic activity,
- trade,
- political organization,
- cooperation,
- conflict,
- alliances,
- governance,
- larger collective structures.

But these metrics should not exist merely because they are imaginable.

> **A metric requires something real to measure.**

---

# Future civilization metrics

Production, economics, politics, alliances and governance are not predefined Chapters.

They are possible dimensions of an evolving civilization.

If canonical systems for them are introduced, Metrics can observe their resulting state.

Conceptually:

**CANONICAL SYSTEM**

↓

**OBSERVABLE STATE**

↓

**METRIC**

Not:

**POSSIBLE IDEA**

↓

**METRIC**

This distinction prevents the observation layer from presenting future concepts as current reality.

---

# Metrics follow the experiment

Metrics should evolve with Zipvilization.

They should not attempt to predict its complete future measurement model at Genesis.

A Farm may eventually produce measurable activity.

Cities may create specialization or economic complexity.

States may make political or macroeconomic signals meaningful.

Kingdoms may create measurable cooperation, conflict or larger structures.

But those measurements become canonical only when the systems beneath them become canonical.

> **First the system exists.**
>
> **Then it can be observed.**
>
> **Then it can be measured.**

Metrics follows the experiment.

It does not define the experiment.

---

# Metrics at a glance

Metrics should help answer:

## How much of the world is still dormant?

→ Dormant Land

## How much has entered civilization?

→ Active territorial state

## How much has become Permanent Nature?

→ Burn / Permanent Nature

## How many people are participating?

→ Holders / Colonists

## How is land distributed?

→ Territorial distribution and concentration

## How is raw SOLUM organized into Territory?

→ SOLUM / Tiles / Farms / higher territorial structures

## How developed is the world?

→ Territory / maturity / Zips / cycles

## What is changing?

→ Historical progression and reconstruction

## What economic state exists?

→ Active contract and canonical economic metrics

The purpose is not maximum data.

The purpose is meaningful evidence.

---

# Follow Metrics through the Atlas

### What translates the underlying state into Zipvilization data?

→ **[SolumTools](/world/solumtools/)**

### What gives global state visual form?

→ **[SolumWorld](/world/solumworld/)**

### What brings individual Territory to life?

→ **[SolumView](/world/solumview/)**

### What does the world mean?

→ **[The World](/world/)**

### What is the territorial substrate?

→ **[Solum](/world/solum/)**

### Who participates?

→ **[Colonists](/world/colonists/)**

### What territorial structures exist?

→ **[Territories](/world/territories/)**

### What population exists?

→ **[Zips](/world/zips/)**

### How does development progress?

→ **[Time](/world/time/)**

### What defines the interpretation rules?

→ **[Canonical Rules](/smart-contract/canonical-rules/)**

### What new measurements may appear later?

→ **[Chapters](/chapters/)**

### Where are the technical mechanics?

→ **[Smart Contract](/smart-contract/)**

### Where is the deeper source?

→ **[Repository](/repository/)**

---

# Measure the experiment

Zipvilization begins with a question.

Can a digital civilization emerge from finite territory, public rules, time, and participation?

That question should not be answered by marketing.

It should be answered by what happens.

How many people arrive.

How they distribute themselves.

How much of the world awakens.

How much becomes Nature forever.

How Territory organizes itself.

How primary territorial structures mature.

How Zips emerge.

How higher territorial levels develop.

How history can be reconstructed.

How economic and political systems evolve when they eventually exist.

Perhaps the experiment succeeds.

Perhaps it fails.

Perhaps it produces something we did not expect.

Metrics should not protect us from that answer.

It should help us see it.

> **The Atlas explains the experiment.**
>
> **Metrics shows us what the experiment is actually doing.**

---

→ **[Return Home](/)**  
→ **[Explore the Chapters](/chapters/)**  
→ **[Continue to Founding Colonists](/founding-colonists/)**
