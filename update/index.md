---
layout: default
title: Update — V1 → V2
nav_order: 99
description: >
  Master reference for the Zipvilization V2 documentation update.
  This page defines the concepts, relationships, files and validation
  criteria required to migrate the Atlas from V1 to V2 without losing
  canonical coherence.
permalink: /update/
---

# Update — V1 → V2

**Master reference for the V2 documentation remodel.**

Zipvilization is moving from **V1 to V2**.

This is not a change of project.

It is not a replacement of the foundations.

It is a deeper and more complete expression of what Zipvilization already is, how Colonists will experience it, how its different systems relate to each other, and how its future can remain open without weakening its canonical foundations.

V1 documented many individual components in considerable depth.

But those components were often explained from the perspective of architecture, rules and backend logic.

What was less developed was the relationship between them.

Especially:

- what a Colonist actually experiences,
- how SolumTools, SolumWorld and SolumView work together,
- how the dApp evolves with the civilization,
- how the Chapters relate to that evolution,
- what remains immutable,
- what can evolve,
- and where Horizonte begins.

V2 addresses those gaps.

> **V1 defined the pieces.**
>
> **V2 connects them into an experience.**

This page is the reference for that migration.

If another page conflicts with this document during the V2 remodel, the conflict must be reviewed rather than silently resolved.

---

# 1. Purpose of V2

The purpose of V2 is not to make the Atlas larger.

It is to make Zipvilization clearer.

The update must:

1. preserve valid V1 concepts,
2. correct genuine contradictions,
3. expand concepts that were correct but incomplete,
4. connect previously isolated systems,
5. explain the Colonist experience,
6. distinguish canonical truth from visual representation,
7. clarify the role of the dApp,
8. clarify the relationship between SolumTools, SolumWorld and SolumView,
9. reconnect the Chapters with their original purpose,
10. establish the relationship between immutable foundations and open future,
11. preserve Horizonte,
12. improve navigation for both Humans and AI.

This is a deep documentation remodel.

It is **not** permission to rewrite everything.

> **Correct but incomplete is not the same as incorrect.**

Existing text should be preserved whenever it remains compatible with V2.

---

# 2. The central V2 distinction

V1 documented the architecture extensively.

V2 must also document the experience.

These are different perspectives on the same system.

### Architecture

Explains:

- blockchain state,
- Smart Contract behavior,
- canonical rules,
- data derivation,
- indexing,
- backend systems,
- technical responsibilities,
- state preservation,
- representation boundaries.

### Experience

Explains:

- what a Colonist sees,
- what a Colonist understands,
- what a Colonist can observe,
- how the world becomes visible,
- how an individual Territory becomes explorable,
- how interaction can progressively emerge.

Both are necessary.

Neither replaces the other.

> **Architecture explains how it works.**
>
> **Experience explains what it becomes for a Colonist.**

---

# 3. One dApp

SolumTools, SolumWorld and SolumView must not be documented as three unrelated products or three independent websites.

They solve different technical problems.

They may require different architectures.

They may be developed separately.

But they belong to a single Zipvilization experience.

> **The architecture is modular.**
>
> **The experience is unified.**

The frontend and final UX remain open to development.

A Colonist may experience SolumTools and SolumWorld simultaneously.

A wallet search may combine individual statistics with the visual location of a Territory.

Entering that Territory may transition naturally into SolumView.

The technical boundaries do not need to become UX boundaries.

→ [The dApp](/dapp/)

---

# 4. The Colonist experience

The dApp must be understandable from the Colonist's perspective.

A holder has **SOLUM**.

A Colonist has a relationship with **Solum**.

The dApp makes that relationship experienceable.

The current conceptual progression is:

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

The question mark is intentional.

It represents **Horizonte**.

This sequence is not a rigid software roadmap.

It describes increasing depth of experience.

---

# 5. SolumTools — Data

[SolumTools](/world/solumtools/) is the foundation of the dApp.

Its fundamental function is:

> **Translate blockchain state and history into Zipvilization data.**

The blockchain provides technical reality.

It can expose:

- addresses,
- balances,
- transfers,
- blocks,
- Pool state,
- Burn,
- contract interactions,
- historical state.

Canonical rules define what valid technical states mean inside Zipvilization.

SolumTools applies those rules and exposes the resulting information in the language of Zipvilization.

Examples include:

**address / holder → Colonist**

**SOLUM balance → Territory**

**Pool-held SOLUM → Dormant Land**

**burned SOLUM → Permanent Nature**

**blocks → Time**

**Territory + Time → development and maturity**

**canonical Zip rules → Zip population**

SolumTools does not create canonical truth.

It reads and translates it.

> **Canonical rules define the meaning.**
>
> **SolumTools applies those rules to translate and expose the data.**

---

# 6. Minimum SolumTools experience

The earliest useful SolumTools experience should make the current state of Zipvilization understandable.

Its minimum useful scope includes:

### Colonists

How many Colonists currently exist.

### Territory

How much Territory has been colonized.

### Territorial structures

How many:

- Farms,
- Cities,
- States,
- Kingdoms

exist according to canonical rules.

### Dormant Land

How much SOLUM remains in the Pool and therefore how much Territory remains Dormant and available for colonization.

### Permanent Nature

How much SOLUM has been burned and therefore how much Territory has become Permanent Nature.

### Zips

The current Zip population derived from valid state and canonical rules.

This is the first public translation from blockchain activity into a readable civilization.

---

# 7. SolumTools evolution

SolumTools is not limited to global counters.

Its natural development increases the depth with which present and past can be observed.

A useful conceptual progression is:

**BASE DATA**

↓

**TIME**

↓

**COLONISTS / WALLETS**

↓

**INTERACTIONS**

↓

**ROLES**

↓

**HISTORY**

This can eventually include:

- maturity,
- territorial development,
- historical state,
- wallet-level statistics,
- individual Colonist profiles,
- activity,
- Territory history,
- contribution to Permanent Nature,
- territorial accumulation,
- interaction patterns,
- roles derived from behavior over Time.

SolumTools therefore represents both:

**present**

and

**past**.

---

# 8. SolumWorld — World

[SolumWorld](/world/solumworld/) is the graphical representation of Solum and Zipvilization.

Its fundamental function is:

> **Give valid Zipvilization state a graphical form.**

SolumTools and SolumWorld are intimately connected.

They are two representations of the same underlying reality.

**SolumTools → DATA**

**SolumWorld → IMAGE**

SolumWorld does not define canonical truth.

It determines how valid state is represented visually as a coherent world.

This distinction must remain explicit:

> **Canonical state determines what is true.**
>
> **SolumWorld determines what that truth looks like as a world.**

---

# 9. Minimum SolumWorld experience

SolumWorld does not require a complex world at Genesis.

Its earliest expression can be simple.

A highly pixelated Solum can represent the principal states of the world.

Current conceptual visual language:

**Dormant Land → brown**

**Permanent Nature → green and blue**

**Colonized Territory → yellow and gray**

These visual conventions may evolve during frontend development.

Their purpose is to establish the principle:

> **The visual world must remain grounded in real state.**

SolumWorld may aggregate, simplify and interpret valid data graphically.

It does not need to represent every SOLUM literally as one visible pixel.

But its representation may not contradict canonical reality.

---

# 10. SolumWorld is primarily state, not life

SolumWorld represents the world in its primarily **static** form.

Static does not mean technically motionless.

The interface may:

- rotate,
- move,
- zoom,
- animate transitions,
- interpolate visual changes,
- simulate movement for presentation.

But its principal object is the representation of valid world state.

It answers:

> **What does Solum look like now?**

As Zipvilization accumulates:

- Colonists,
- Territory,
- Time,
- development,
- Permanent Nature,
- Dormant Land,
- Zips,
- structures,
- history,

SolumWorld can gain increasing visual resolution.

---

# 11. SolumTools + SolumWorld

V2 must avoid presenting SolumTools and SolumWorld as completely separate stages of the user experience.

They can coexist.

A Colonist may see:

**statistics + planet**

**data + geography**

**wallet information + Territory location**

**history + visual state**

at the same time.

The relationship is:

> **Data explains the world.**
>
> **The world gives the data form.**

Their development can also overlap.

SolumTools begins first because reliable translation is required before reliable representation.

SolumWorld can then emerge and evolve alongside it.

Neither requires the other to disappear.

---

# 12. SolumView — Life

[SolumView](/world/solumview/) represents a change in depth.

It is not simply SolumWorld with more zoom.

SolumView begins when the experience enters an **individual Territory**.

Its context is always connected to:

**wallet**

↓

**Colonist**

↓

**Territory**

↓

**internal experience**

Its fundamental function is:

> **Bring an individual Territory to life.**

Where SolumWorld primarily represents world state, SolumView can represent dynamic territorial life.

---

# 13. SolumView is not a literal inventory

SolumView must not be interpreted as a one-to-one graphical reproduction of wallet statistics.

If a Colonist has a state corresponding to:

- many Farms,
- multiple Cities,
- large Territory,
- many Zips,

the interface does not need to render every canonical quantity as a literal graphical object.

SolumView may create a functional visual representation of that Territory.

It can make visible:

- Zips,
- structures,
- development,
- maturity,
- activity,
- change,
- internal areas,
- other future systems.

The representation can be simulated.

The underlying truth cannot.

> **Visual life may be simulated.**
>
> **Canonical truth may not.**

A Zip may walk without each step being an on-chain event.

A building may contain visual activity that exists for experience rather than canonical state.

Animation may occur between canonical state changes.

But simulated behavior must never silently become false canonical history.

---

# 14. The boundary of representation

V2 must distinguish three concepts clearly:

### Canonical truth

What is valid according to blockchain state, contract behavior, Time and canonical rules.

### Visual representation

How valid state is represented graphically.

### Simulation

Non-canonical visual or behavioral activity used to make the world understandable, dynamic or immersive.

These layers may interact.

They may not be confused.

A representation may simplify reality.

A simulation may animate reality.

Neither may rewrite reality.

---

# 15. Development sequence

The current development logic is:

### Genesis

Begin with the essential SolumTools experience.

Zipvilization starts producing real state and real history.

### SolumTools expansion

Add increasing depth:

- Time,
- maturity,
- wallets,
- individual Colonists,
- interactions,
- roles,
- history.

### SolumWorld emergence

Begin representing the same valid state graphically.

SolumTools and SolumWorld then grow together.

### Increasing resolution

Data and image gain depth as the civilization itself gains depth.

### SolumView

When SolumTools and SolumWorld are sufficiently developed, begin the dynamic individual-Territory experience.

### Beyond SolumView

Do not define a final state.

SolumView is not the endpoint of Zipvilization.

→ [Horizonte](/trinomial/horizonte/)

---

# 16. The dApp grows with the civilization

The dApp should not pretend at Genesis that a mature civilization already exists.

At Genesis there may be:

- little history,
- few Colonists,
- limited Territory,
- limited development,
- few Zips,
- simple visual state.

That is not a weakness.

It is the starting condition.

> **The dApp begins with the civilization.**

As Zipvilization produces more reality, the dApp gains more reality to represent.

This relationship must remain visible throughout V2.

---

# 17. SOLUM and Solum

V2 must clarify the different but related meanings of the word.

### SOLUM

The on-chain unit.

### 1 SOLUM

Represents **1 m²** of Territory.

### Solum

The land itself and, collectively, the world formed by that territorial substrate.

Context determines scale.

> **SOLUM is the unit.**
>
> **Solum is the land.**
>
> **Solum is the world.**

[Zipvilization](/) is the civilization that emerges on Solum.

The authoritative explanation should ultimately live in:

→ [SOLUM / Solum](/world/solum/)

---

# 18. The Chapters establish the DNA

The [Chapters](/chapters/) must not be reduced to a frontend roadmap.

They establish the structural conditions under which Zipvilization can develop.

They define its **DNA**.

> **The Chapters do not define everything Zipvilization will become.**
>
> **They define the foundations it must never stop being.**

Their meaning must be understandable both structurally and experientially.

---

# 19. Chapter 0 — EXIST

Genesis establishes existence.

Before Genesis there is:

- architecture,
- documentation,
- code,
- preparation,
- testing.

After Genesis there is:

- real state,
- real interaction,
- real Time,
- real consequences,
- real history.

From the Colonist perspective:

> **There is now something real to observe.**

Genesis is not the final product.

> **Genesis ignites the process.**

---

# 20. Chapter 1 — OBSERVE

Observability makes real state readable.

The blockchain records technical reality.

The system must make that reality understandable without replacing it.

This is where the foundations of SolumTools become especially important.

From the Colonist perspective:

> **I can read the world.**

Observation does not create authority.

> **Observation ≠ Control**

---

# 21. Chapter 2 — WORLD

Valid state acquires coherent territorial and graphical expression.

Territory becomes geography.

Dormant Land, Permanent Nature and colonized Territory become parts of a visible Solum.

SolumWorld becomes increasingly relevant.

From the Colonist perspective:

> **I can see the world.**

But graphical representation does not replace canonical truth.

The image follows the state.

---

# 22. Chapter 3 — ACT

Chapter 3 must be interpreted carefully.

**ACT does not mean that a Colonist can already directly modify the internal world of their Territory.**

The Colonist remains primarily an observer of that internal world.

They do not yet necessarily:

- construct manually,
- command Zips,
- place objects,
- redesign Territory,
- control internal development.

The action occurs through interaction with the underlying system.

A Colonist interacts with SOLUM and the Smart Contract.

Those interactions produce consequences.

Those consequences affect Zipvilization.

And over Time, those consequences describe the Colonist.

> **Your actions have consequences in the world.**

This is the foundation of Colonist roles.

---

# 23. Roles emerge from behavior

Roles should not be understood primarily as classes selected by a user.

They can emerge from observable behavior over Time.

For example, a Colonist may become notable for:

- holding large amounts of Territory,
- expanding Territory,
- maintaining Territory over Time,
- generating Permanent Nature through interactions that produce Burn,
- participating frequently,
- contributing strongly to particular state changes,
- other measurable behavioral patterns.

A Colonist can express multiple characteristics.

Roles describe history.

They do not replace it.

> **Roles are not assigned.**
>
> **They emerge from behavior over Time.**

SolumTools can progressively make those patterns measurable and visible.

---

# 24. There are no good or bad Colonists

This principle must become explicit in V2.

Zipvilization does not assign moral value to valid interactions simply because they produce different outcomes.

A BUY is not inherently good.

A SELL is not inherently bad.

A TRANSFER is not inherently good or bad.

Each interaction produces consequences according to the system.

Those consequences change Zipvilization.

> **There are no good or bad Colonists.**
>
> **There are different actions, different consequences and different histories.**

Roles must therefore remain primarily **descriptive**, not moral judgments.

> **Roles describe behavior. They do not judge it.**

---

# 25. Example — BUY

A broad wave of BUY interactions can:

- move SOLUM out of the Pool,
- reduce Dormant Land,
- increase colonized Territory,
- create or expand Colonist Territories,
- alter territorial distribution,
- create new conditions for development over Time.

This changes Zipvilization.

It becomes part of history.

The system records the consequence.

It does not declare the actor morally good.

---

# 26. Example — SELL

A SELL can produce very different consequences.

According to the documented contract mechanics, it can contribute to:

- Territory returning toward the Pool,
- increasing Dormant Land,
- increasing Territory available for future acquisition,
- Burn,
- creation of Permanent Nature,
- Reflection toward remaining participants,
- changes in territorial distribution.

A SELL therefore does not simply mean:

**someone left**

or:

**something bad happened**.

It transforms the world in another way.

Permanent Nature may increase.

Dormant Land may increase.

Other Colonists may receive Reflection.

The territorial configuration changes.

That also becomes history.

---

# 27. Actions and consequences

This becomes a fundamental V2 principle:

> **Every valid interaction can have consequences.**
>
> **Those consequences become part of Zipvilization.**
>
> **What persists becomes history.**

The system defines the conditions under which actions occur.

It does not need to define a moral interpretation of every outcome.

This is another expression of:

> **We define the conditions.**
>
> **We do not define the outcome.**

---

# 28. Chapter 4 — REMEMBER

Time allows consequences to accumulate.

Without memory, interactions are isolated events.

With Time and persistent state, they become history.

Territories develop.

Colonist behavior accumulates.

Roles gain historical meaning.

Permanent Nature records irreversible consequence.

The world acquires a past.

From the Colonist perspective:

> **My Territory has history.**
>
> **My actions have a history.**
>
> **The world remembers.**

---

# 29. Chapter 5 — EMERGE

Once many actors interact with the same persistent system over Time, patterns can emerge that were not individually scripted.

Different territorial concentrations.

Different relationships with Nature.

Different Colonist histories.

Different roles.

Different behaviors.

Different forms of organization.

The system can become more complex without requiring every outcome to be predetermined.

From the Colonist perspective:

> **What we do together can produce something that was not written in advance.**

That is the beginning of emergence.

---

# 30. Horizonte

The Chapters establish the DNA.

They do not establish the ceiling.

After the currently defined foundations comes:

**?**

That is [Horizonte](/trinomial/horizonte/).

The future may contain forms of interaction that are not yet defined.

Possible future layers may include:

- deeper Colonist-to-Territory interaction,
- Colonist-to-Colonist interaction,
- richer Zip behavior,
- visual extensions,
- resources,
- NFTs,
- exchange systems,
- markets,
- alliances,
- political structures,
- conflicts,
- cooperation,
- social systems,
- systems that do not yet have names.

These are possibilities.

They are not promises.

They must not be converted into predetermined destiny.

> **The foundation is defined.**
>
> **The possibilities are not.**

---

# 31. Extensibility without rewriting

V2 must establish a fundamental rule for future development:

> **New layers may expand Zipvilization. They may not rewrite it.**

Future systems may add:

- meaning,
- interaction,
- representation,
- simulation,
- social structure,
- economic systems,
- creative systems,
- new experiences.

But a new layer may not silently alter canonical truth already accumulated beneath it.

It may not rewrite history because a new feature prefers another history.

It may not convert Permanent Nature back into ordinary Territory if Permanent Nature is canonically irreversible.

It may not invent canonical events that never occurred.

It may not replace valid historical state with a more convenient narrative.

The future can add depth.

It cannot require a different past.

---

# 32. Immutable does not mean static

V2 must avoid using **immutable** as a synonym for **unchanging world**.

Zipvilization is intended to change.

Colonists act.

Territory changes.

Dormant Land changes.

Permanent Nature changes.

Time passes.

Structures develop.

Zips emerge.

History accumulates.

New systems can appear.

New forms of interaction can become possible.

What must remain protected is the integrity of canonical truth and accumulated history.

> **Immutable does not mean static.**
>
> **Zipvilization can evolve without rewriting its history.**

This distinction is fundamental to V2.

---

# 33. Core and future layers

A useful V2 mental model is:

### CORE

- SOLUM
- Territory
- Time
- Zips
- Dormant Land
- Permanent Nature
- Canonical Rules
- valid state
- accumulated history

### OBSERVATION

- SolumTools

### WORLD REPRESENTATION

- SolumWorld

### TERRITORIAL EXPERIENCE

- SolumView

### FUTURE INTERACTION

Potential additional systems between:

- Colonist ↔ Territory,
- Colonist ↔ Zips,
- Colonist ↔ Colonist,
- world ↔ community,
- systems not yet defined.

Higher layers may extend lower layers.

They may not silently rewrite them.

---

# 34. The V2 documentation network

V2 should not duplicate every concept across every page.

Each important concept needs a natural authoritative home.

Other pages should summarize and link to it.

### The dApp

Authoritative focus:

**The Colonist experience and integration of SolumTools, SolumWorld and SolumView.**

→ `/dapp/`

### SolumTools

Authoritative focus:

**Translation of blockchain state and history into Zipvilization data.**

→ `/world/solumtools/`

### SolumWorld

Authoritative focus:

**Graphical representation of valid world state.**

→ `/world/solumworld/`

### SolumView

Authoritative focus:

**Dynamic experience inside an individual Territory.**

→ `/world/solumview/`

### Solum

Authoritative focus:

**SOLUM as unit, Territory as land, Solum as world.**

→ `/world/solum/`

### Chapters

Authoritative focus:

**The structural DNA and progressive conditions of Zipvilization.**

→ `/chapters/`

### Colonists & Roles

Authoritative focus:

**Actors, consequences, behavioral history and emergent roles.**

→ `/chapters/colonists-roles/`

### Horizonte

Authoritative focus:

**Open possibility beyond the defined foundations.**

→ `/trinomial/horizonte/`

### Canonical Rules

Authoritative focus:

**What future interpretation and implementation may not contradict.**

→ `/smart-contract/canonical-rules/`

### Principles

Authoritative focus:

**High-level principles that remain valid across the project.**

→ `/principles/`

---

# 35. Files requiring major V2 review

The following pages require substantial conceptual review.

## `/world/solumtools/`

Integrate:

- SolumTools as dApp data foundation,
- blockchain → Zipvilization translation,
- present + past,
- minimum Genesis experience,
- Time,
- wallets,
- interactions,
- roles,
- history,
- relationship with SolumWorld,
- relationship with the unified dApp.

## `/world/solumworld/`

Integrate:

- graphical state of Solum,
- static-world concept,
- minimum pixelated representation,
- Dormant / Nature / colonized visual states,
- visual authority versus canonical authority,
- DATA + IMAGE relationship with SolumTools,
- increasing resolution,
- boundary before individual Territory life.

## `/world/solumview/`

Integrate:

- individual wallet / Colonist / Territory context,
- dynamic Territory,
- functional simulation,
- non-literal representation,
- Zips and internal life,
- canonical truth versus visual simulation,
- future interaction,
- SolumView is not the endpoint.

## `/world/index.md`

Integrate:

- World = what exists,
- dApp = how it is experienced,
- correct SolumTools / SolumWorld / SolumView relationship,
- remove incorrect attribution of canonical authority to SolumWorld,
- preserve SolumWorld authority over visual state.

## `/world/solum/`

Integrate:

- SOLUM as token/unit,
- 1 SOLUM = 1 m²,
- Solum as land,
- Solum as world,
- relationship to Zipvilization.

## `/chapters/index.md`

Major review.

Integrate:

- Chapters as DNA,
- not software releases,
- not frontend roadmap,
- structural + Colonist interpretation,
- EXIST → OBSERVE → WORLD → ACT → REMEMBER → EMERGE → ?,
- Horizonte after the defined foundations.

## `/chapters/colonists-roles/`

Major review.

Integrate:

- ACT does not yet mean internal Territory control,
- contract interaction as action,
- consequences,
- roles emerging from behavior,
- descriptive rather than moral roles,
- no good/bad Colonists,
- BUY / SELL examples,
- Time and history as role inputs.

## `/chapters/observability/`

Review:

- SolumTools role,
- observation versus authority,
- translated data,
- relationship with the dApp.

## `/chapters/territory-world/`

Review:

- world representation,
- canonical state versus visual state,
- SolumWorld,
- Colonist experience of seeing the world.

## `/chapters/time-history/`

Review:

- accumulated consequences,
- Colonist history,
- Territory history,
- role development over Time,
- persistent truth.

## `/chapters/emergence/`

Review:

- open outcomes,
- interaction between actors,
- no predetermined social outcome,
- bridge toward Horizonte,
- extensibility without rewriting.

---

# 36. Files requiring targeted V2 correction

These pages should not necessarily be rewritten.

They require targeted correction or integration.

## `/metrics/`

Correct old architecture where SolumWorld is given authority over canonical existence.

Metrics should derive from valid translated state.

## `/smart-contract/canonical-rules/`

High priority.

Remove or rewrite rules that assign canonical world-state authority to SolumWorld.

Add the distinction:

**canonical truth ≠ visual representation ≠ simulation**

Consider anchoring:

> **New layers may expand Zipvilization. They may not rewrite it.**

## `/smart-contract/burn/`

Ensure:

**Burn → Permanent Nature**

is canonical and does not depend on SolumWorld interpretation.

SolumWorld represents Permanent Nature visually.

## `/smart-contract/pool/`

Ensure:

**Pool-held SOLUM → Dormant Land**

is canonical and does not depend on SolumWorld interpretation.

SolumWorld represents Dormant Land visually.

## `/smart-contract/solum-token/`

Review references to SolumWorld and canonical interpretation.

## `/smart-contract/fair-access/`

Review architectural references only where required.

## `/smart-contract/taxes/`

Review architectural references and consequences of interaction.

Potentially connect BUY / SELL / TRANSFER consequences to Colonist behavior without moral framing.

## `/principles/`

Integrate:

- actions and consequences,
- no moral classification of valid actors,
- extensibility without rewriting,
- immutable does not mean static,
- future layers cannot rewrite accumulated truth.

## `/trinomial/`

Correct obsolete SolumWorld canonical-authority language.

Preserve the Trinomial's actual function.

## `/trinomial/human/`

Review obsolete architecture references.

Potentially connect Human action to consequences without implying total control.

## `/trinomial/artificial-intelligence/`

Correct obsolete SolumWorld / SolumTools / SolumView ordering.

Preserve AI evidence-before-narrative principles.

## `/trinomial/horizonte/`

Strengthen:

- defined foundation / undefined possibilities,
- Chapters as DNA,
- open future,
- SolumView not endpoint,
- extensibility without rewriting,
- immutable history beneath open possibility.

---

# 37. Files requiring integration review

These pages are broadly coherent and should only be changed where V2 genuinely improves navigation or clarity.

## `/`

Home.

Add or strengthen the path toward the dApp.

Do not duplicate the entire dApp explanation.

## `/status/`

Preserve:

**DEFINED ≠ BUILT ≠ LIVE**

Update SolumTools / SolumWorld / SolumView descriptions only where necessary.

Do not rebuild Status.

## `/world/civilization/`

Clarify:

- civilization exists in accumulated state, Time, interaction and history,
- the dApp makes that civilization experienceable,
- SolumView does not create canonical civilization through simulation.

## `/genesis/`

Ensure the early dApp experience matches the real Genesis state.

Do not imply a mature visual world at launch.

## `/founding-colonists/`

Review only if V2 terminology creates a useful connection.

Do not overload recruitment material with architecture.

## `/repository/`

Correct current reason for privacy.

The Repository is not merely private while awaiting eventual public release.

Current principle:

> **Private where integrity requires it. Public wherever it doesn't.**

---

# 38. Deep technical and AI nodes

The `/0x5a4950/` documentation requires a separate V2 audit.

Do not perform blind textual replacements.

These documents contain:

- formal notation,
- deliberate unresolved variables,
- test propositions,
- intentionally incorrect statements for machine reasoning,
- distinctions between representation and implementation.

A phrase appearing to contradict V2 may be:

- a hypothesis,
- a negative example,
- a question,
- an intentionally unresolved proposition.

Each occurrence must be interpreted in context.

The machine-documentation principles remain:

- preserve symbol types,
- preserve unresolved variables,
- do not infer canon,
- do not treat representation as implementation,
- do not treat observation as authority,
- do not resolve Horizonte,
- report contradictions,
- preserve meaningful absence.

---

# 39. What V2 must not do

The remodel must not:

- rewrite valid documentation simply because it is old,
- convert every page into UX copy,
- remove technical depth,
- turn Chapters into product releases,
- turn Horizonte into a roadmap,
- present possible future systems as promises,
- imply SolumView is the final form of Zipvilization,
- make SolumWorld the source of canonical truth,
- make SolumTools the creator of canonical meaning,
- treat simulation as canonical history,
- treat BUY as morally good,
- treat SELL as morally bad,
- rank Colonists morally,
- confuse role with reward,
- confuse visual state with canonical state,
- confuse current implementation with final possibility,
- imply that the dApp creates the underlying civilization,
- invent functionality merely to fill documentation gaps.

---

# 40. V2 validation questions

Every major page modified during V2 should be tested against these questions.

### Canon

Does this page distinguish what is canonical from what is representation?

### State

Does it distinguish real state from simulated visual behavior?

### Authority

Does it assign authority to the correct component?

### SolumTools

Is SolumTools translating rather than inventing meaning?

### SolumWorld

Is SolumWorld representing valid state rather than creating canonical state?

### SolumView

Is SolumView clearly an individual-Territory dynamic experience rather than a literal wallet map?

### dApp

Does the page understand that the Colonist experiences one integrated dApp?

### Chapters

Does it treat Chapters as structural DNA rather than a software roadmap?

### Actors

Does it describe Colonist behavior without imposing unnecessary moral judgment?

### Consequences

Does it recognize that valid interactions can produce different but meaningful consequences?

### History

Can future layers extend the system without rewriting accumulated truth?

### Horizonte

Does the page preserve open possibility instead of prematurely defining the future?

### Status

Does it distinguish what is defined, built and live?

### Humans and AI

Can a Human understand the page without reconstructing the repository?

Can an AI follow explicit relationships to the authoritative pages?

---

# 41. Migration method

V2 should be implemented progressively.

For each updated ZIP:

### 1. Read the current file

Never rewrite from memory when the current version is available.

### 2. Compare against this V2 reference

Identify:

- contradiction,
- incomplete concept,
- missing relationship,
- obsolete architecture,
- missing link,
- no change required.

### 3. Preserve valid depth

Do not simplify technical documentation merely to make it easier to read.

### 4. Add the missing perspective

Where appropriate, connect:

**architecture ↔ experience**

### 5. Link rather than duplicate

If another page is authoritative for a concept, summarize and link.

### 6. Validate terminology

Especially:

- SOLUM / Solum,
- Territory,
- Colonist,
- Time,
- Zips,
- Dormant Land,
- Permanent Nature,
- SolumTools,
- SolumWorld,
- SolumView,
- dApp,
- Chapters,
- Horizonte.

### 7. Validate current status

Do not present future functionality as live.

### 8. Validate canonical boundaries

Representation and simulation must not become false canonical truth.

### 9. Re-audit globally

After major groups of pages are updated, search the complete Atlas again for contradictions and obsolete relationships.

---

# 42. Recommended migration order

The current recommended order is:

**1 — The dApp**

Created.

Defines the Colonist experience and acts as the first V2 reference.

**2 — SolumTools**

Establish the data foundation.

**3 — SolumWorld**

Establish the graphical world.

**4 — SolumView**

Establish dynamic Territory.

**5 — World**

Reconnect ontology and experience.

**6 — Solum**

Clarify unit, land and world.

**7 — Chapters**

Rebuild their role as Zipvilization DNA.

**8 — Colonists & Roles**

Anchor actions, consequences and behavioral roles.

**9 — Time / History / Emergence**

Connect persistent consequences to civilization.

**10 — Principles**

Anchor the major V2 principles.

**11 — Canonical Rules**

Formalize boundaries and remove obsolete authority assignments.

**12 — Horizonte**

Connect immutable foundation to open future.

**13 — Metrics / Smart Contract / Trinomial**

Correct remaining architectural references.

**14 — Home / Status / Civilization / Genesis**

Integrate and link without unnecessary rewriting.

**15 — 0x5a4950**

Deep contextual audit.

**16 — Global audit**

Check the entire Atlas as one semantic network.

---

# 43. V2 core statements

The following statements summarize the current V2 model and should remain mutually compatible throughout the Atlas.

> **One dApp. One world. Increasing depth.**

> **The architecture is modular. The experience is unified.**

> **Canonical rules define the meaning. SolumTools applies those rules to translate and expose the data.**

> **SolumTools is the data foundation of the dApp.**

> **SolumTools represents present and past.**

> **SolumTools and SolumWorld are data and image of the same underlying reality.**

> **Canonical state determines what is true. SolumWorld determines what that truth looks like as a world.**

> **SolumWorld is primarily the static visual representation of Solum.**

> **SolumView begins inside an individual Territory.**

> **SolumView is dynamic, functional and increasingly immersive.**

> **Visual life may be simulated. Canonical truth may not.**

> **The dApp begins with the civilization.**

> **The Chapters establish the DNA.**

> **ACT means actions have consequences. It does not yet mean direct control of Territory.**

> **Roles emerge from behavior over Time.**

> **Roles describe behavior. They do not judge it.**

> **There are no good or bad Colonists. There are different actions, different consequences and different histories.**

> **Every valid interaction can become part of the history of Zipvilization.**

> **New layers may expand Zipvilization. They may not rewrite it.**

> **Immutable does not mean static.**

> **The foundation is defined. The possibilities are not.**

> **SolumView is not the endpoint.**

> **We define the conditions. We do not define the outcome.**

---

# 44. Definition of V2 completion

V2 is not complete when every file has been rewritten.

V2 is complete when the Atlas can be read as one coherent system.

A Human should be able to understand:

- what Zipvilization is,
- what SOLUM is,
- what Solum is,
- what Territory means,
- what becoming a Colonist means,
- what they can experience through the dApp,
- how that experience begins,
- how it can deepen,
- why their actions have consequences,
- how those consequences become history,
- why different Colonists can develop different roles,
- why the system does not require good and bad actors,
- what is canonical,
- what is visual,
- what may be simulated,
- what is immutable,
- what can evolve,
- and why the future remains open.

An AI should be able to determine:

- which page is authoritative for each concept,
- which relationships are canonical,
- which systems translate state,
- which systems represent state,
- which systems simulate experience,
- which functionality is current,
- which functionality is future,
- which statements describe possibilities rather than promises,
- and where interpretation must stop.

The objective is not uniformity.

It is coherence.

---

# V2

Zipvilization already had its foundations.

V2 does not replace them.

It connects them.

It makes the relationship between blockchain, Territory, Time, Colonists, world, history and experience explicit.

It explains what a Colonist actually has beyond SOLUM.

It explains how a world can begin as data, become visible, become explorable and eventually become interactive.

It establishes the boundary between simulation and truth.

It establishes the relationship between action and consequence.

It establishes the Chapters as DNA rather than destination.

And it protects the most important property of the project:

a defined foundation beneath an undefined future.

> **V1 defined the pieces.**
>
> **V2 connects the system.**
>
> **Horizonte keeps it open.**
