---
layout: default
title: Taxes
parent: Smart Contract
nav_order: 2
description: >
  Taxes documents the contract-level mechanism through which a defined portion
  of qualifying Solum transfers is redirected according to canonical rules.
  It separates blockchain execution from the economic and civilizational
  meaning that Tax may acquire as Zipvilization develops.
permalink: /smart-contract/taxes/
---

# Taxes

Movement can have consequences.

When Solum moves under conditions subject to Tax, the Smart Contract can redirect a defined portion of that movement according to its canonical rules.

At blockchain level, this is a technical mechanism.

There is:

- a transaction,
- a taxable condition,
- a calculation,
- an amount,
- a source,
- a destination,
- and a resulting state.

Nothing more is required for the contract to execute.

But inside Zipvilization, Tax can eventually become something much larger.

It can become part of the economic structure of civilization.

That distinction must remain clear from the beginning.

> **Tax begins as a contract mechanism.**
>
> **Its civilizational consequences emerge above the contract.**

---

# First: the blockchain

Before discussing economics, States, Kingdoms, redistribution, or governance, we need to understand what Tax actually does.

A Tax mechanism should answer technical questions such as:

- Which operations are taxable?
- Which operations are not?
- How is the taxable amount determined?
- What rate applies?
- How is the Tax calculated?
- Where is the collected Solum sent?
- Can the rate change?
- If so, who or what can change it?
- What boundaries constrain that change?
- Are any addresses or operations exempt?
- What events expose Tax activity?
- How can accumulated Tax be measured?

These questions belong to the Smart Contract.

Their answers must come from canonical technical specifications and deployed behavior.

> **Economic interpretation cannot substitute for contract definition.**

---

# Tax does not create Solum

Tax moves existing Solum.

It does not require new Solum to be minted.

At its simplest, the accounting relationship is:

**Solum movement**

↓

**Tax calculation**

↓

**defined portion redirected**

↓

**remaining portion follows the transfer**

The exact execution must follow the actual contract.

But the supply principle remains important:

> **Tax redistributes existing substrate.**
>
> **It does not expand the world.**

→ **[Explore Supply](/smart-contract/supply/)**

---

# Source matters

Every Tax movement must have a source.

If a transaction generates Tax, the resulting Solum cannot appear from nowhere.

The accounting should allow us to determine:

- what amount entered the transaction,
- what amount was subject to Tax,
- what amount was redirected,
- what amount reached the intended recipient,
- and what balances changed.

This is important for both blockchain verification and world interpretation.

A civilization built on finite territory cannot afford ambiguous accounting of that territory.

---

# Destination matters

Where Tax goes is as important as how much is collected.

A Tax mechanism is incomplete if documentation only says:

> **A Tax is charged.**

We must also know:

> **Where does the Solum go?**

The answer may depend on the canonical contract architecture and, where explicitly defined, the current Chapter of Zipvilization.

Possible future civilizational uses must not be confused with current technical destination.

The hierarchy should remain:

**actual contract destination**

↓

**canonical current function**

↓

**future possibilities where explicitly defined**

Never the reverse.

---

# Tax is not Burn

Tax and Burn both affect Solum movement.

They are fundamentally different mechanisms.

**Tax**

redirects Solum according to defined rules.

**Burn**

makes Solum permanently unavailable according to its defined mechanism.

Therefore:

> **Taxed Solum is not automatically Burned Solum.**

And:

> **Tax is not automatically Permanent Nature.**

If any mechanism later connects Tax with Burn, that relationship must be explicit.

It must not be inferred merely because both mechanisms affect token balances.

→ **[Explore Burn](/smart-contract/burn/)**

---

# Tax is not the Pool

The same distinction applies to the Pool.

The Pool represents a specific technical state within the Solum architecture.

Tax collection represents another.

If Taxed Solum is sent to a particular address, contract, reserve, Pool, or other mechanism, that relationship must be defined technically.

We should not assume:

> **Tax = Pool**

unless the canonical implementation actually establishes that relationship.

The Atlas should preserve the distinction even if funds move between these systems.

→ **[Explore Pool](/smart-contract/pool/)**

---

# Tax and Supply

Taxes do not need to change the original finite substrate.

They change distribution.

This creates an important distinction.

**Supply asks:**

> How much Solum exists?

**Tax asks:**

> How does some existing Solum move under qualifying transactions?

These are related questions.

They are not the same question.

Because the world is finite, redistribution can become economically significant even when total Supply remains unchanged.

→ **[Explore Supply](/smart-contract/supply/)**

---

# Tax and transfers

Tax exists in relation to movement.

A technically useful model separates the relevant quantities.

For a qualifying transfer, we may conceptually distinguish:

- gross amount,
- taxable amount,
- Tax amount,
- net transferred amount,
- and Tax destination.

The exact formulas belong to the canonical implementation.

The architecture, however, should always make those quantities distinguishable.

An interface should not show a transfer of X Solum if the actual recipient receives a different amount without explaining why.

SolumTools should be able to expose the difference.

Artificial Intelligence should be able to explain it.

The blockchain should make it verifiable.

---

# A simple accounting identity

Where the mechanism follows a conventional transfer-Tax structure, the conceptual relationship is:

> **Gross Amount = Net Amount + Tax Amount**

This is not a substitute for the actual contract formula.

It is an accounting relationship that helps us reason about the mechanism.

If the deployed contract behaves differently, the deployed behavior has to be documented explicitly.

The objective is not to force implementation into a convenient formula.

The objective is to make implementation understandable.

---

# Tax rate

A Tax rate is a technical parameter.

It should never be guessed from narrative documentation.

For any active Tax rate, we should be able to determine:

- its current value,
- its unit,
- its calculation basis,
- whether it is fixed or configurable,
- its permitted range,
- the authority capable of changing it,
- and the historical record of any changes.

This is particularly important because small numerical changes can produce large economic consequences at scale.

> **A percentage is not a detail.**
>
> **It is executable economics.**

---

# Configurable does not mean arbitrary

If Tax parameters are configurable, that does not automatically mean they are unconstrained.

A well-defined system can distinguish:

**parameter**

from

**authority**

from

**boundary.**

For example, a mechanism may technically allow a value to change while also restricting:

- maximum value,
- minimum value,
- authorized caller,
- timing,
- conditions,
- or destination.

The Atlas should document those boundaries.

The Repository should preserve the exact implementation.

→ **[Open the Repository](/repository/)**

---

# Authority must be visible

Tax introduces one of the most important questions in any economic system:

> **Who can change the rules?**

If nobody can change them, that should be explicit.

If an owner can change them, that should be explicit.

If a contract can change them automatically, that should be explicit.

If a future DAO can change them, that should only be stated when such authority actually exists.

If authority changes through Chapters, the transition should be documented.

We should never hide administrative power behind vague language such as:

> decentralized

or

> community-driven

when the contract allows us to describe the actual authority precisely.

---

# Tax and Fair Access

Tax and Fair Access may interact.

But they solve different problems.

**Tax**

structures economic movement.

**Fair Access**

constrains how Solum can be acquired, transferred, or concentrated under defined conditions.

A transaction may be:

- allowed and taxed,
- allowed and untaxed,
- restricted by a transaction limit,
- restricted by a wallet limit,
- or treated differently under explicitly defined rules.

The exact combinations belong to implementation.

The conceptual distinction should remain stable.

→ **[Explore Fair Access](/smart-contract/fair-access/)**

---

# From blockchain Tax to world economics

Now we can move one layer upward.

At blockchain level:

> Solum moves according to a Tax mechanism.

Inside Zipvilization:

> that movement can become an economic flow.

This is the beginning of the translation.

**Blockchain**

Taxed transfer

↓

Taxed Solum

↓

defined technical destination

↓

**Zipvilization**

economic resource

↓

possible civilizational function where canonically defined

The contract does not need to understand civilization in order to create an economic consequence for civilization.

---

# Land can become an economic flow

Because:

> **1 Solum = 1 m²**

Tax has an unusual interpretation inside Zipvilization.

A Tax denominated in Solum is not merely moving abstract token units.

It is moving units that correspond to territorial substrate.

This means the economic architecture of Zipvilization can develop from the same finite resource that defines the world.

That relationship should be treated carefully.

Tax does not create territory.

It changes control or destination of existing Solum according to the mechanism.

The economic layer therefore remains grounded in finite substrate.

---

# Tax can accumulate history

A single Tax event may be small.

Thousands or millions of Tax events create history.

Because blockchain events are public and ordered, Tax can become measurable through time.

We may eventually ask:

- How much Solum has been collected through Tax?
- How has Tax activity changed?
- Which Chapters generated the most taxable activity?
- How much Tax is currently accumulated?
- How much has been redistributed?
- What destinations received it?
- How did economic flows change as civilization developed?

These questions transform isolated transfers into economic history.

→ **[Explore Metrics](/metrics/)**

---

# Tax and SolumTools

SolumTools should eventually make Tax legible.

A Human should not need to reconstruct every transaction manually.

Potential deterministic signals may include:

- current Tax parameters,
- Tax amount for a qualifying operation,
- historical Tax collected,
- current Tax balances,
- destination flows,
- and relevant changes through time.

The exact signals depend on implementation.

The principle does not:

> **If Tax affects the public world, its important state should be publicly observable wherever technically possible.**

→ **[Explore SolumTools](/world/solumtools/)**

---

# Tax and Metrics

SolumTools observes and derives.

Metrics presents selected measurements.

That distinction matters here.

SolumTools may expose:

> cumulative Taxed Solum

Metrics may present:

> Tax activity over time

or:

> Tax relative to active Solum movement

or another canonically valid measurement.

Metrics can help us understand the economy.

But it should not silently convert observation into judgment.

High Tax activity does not automatically mean a healthy economy.

Low Tax activity does not automatically mean a failing civilization.

Measurement comes first.

Interpretation follows.

→ **[Explore Metrics](/metrics/)**

---

# Tax does not prove economic health

This deserves explicit treatment.

Blockchain projects often use activity metrics as proxies for success.

Volume rises.

Transactions rise.

Fees rise.

Tax revenue rises.

Those facts can be measured.

But Zipvilization should resist turning every increase into a positive narrative.

More Tax may indicate:

- more participation,
- more redistribution,
- more trading,
- more speculation,
- greater economic activity,
- or a combination of different behaviors.

The data tells us what happened.

Understanding why requires more evidence.

> **Metric first.**
>
> **Interpretation second.**

---

# Tax and Chapters

This is where Tax becomes especially important.

Zipvilization develops progressively.

Early Chapters do not need the same economic complexity as later civilization.

As new systems appear, Tax may acquire new relationships.

Production may create economic consequences.

Cities may create new forms of activity.

States may introduce macroeconomic structures.

Kingdoms may introduce alliances, competition, redistribution, or other higher-order systems.

But future relationships should only become active when the relevant Chapter defines and implements them.

> **Tax can exist before the civilization knows everything it will eventually do with Tax.**

That is not incompleteness.

It is progressive development.

→ **[Explore the Chapters](/chapters/)**

---

# Genesis does not need the final economy

This is an important architectural principle.

We do not need to predict the complete economy of a mature Zipvilization at Genesis.

Doing so would contradict the experimental nature of the project.

We need enough structure to begin coherently.

Then:

participation produces data.

data produces evidence.

Chapters introduce complexity.

civilization develops.

new economic questions emerge.

The Tax mechanism can become part of that evolution without requiring us to script every future use today.

---

# But future flexibility needs boundaries

Emergence does not mean arbitrary change.

If Tax collected during an early Chapter later acquires a new function, that transition must follow canonical rules.

We should be able to determine:

- what state existed before,
- what changed,
- when it changed,
- why the new Chapter permits it,
- what authority executed the transition,
- and what consequences followed.

History must remain reconstructable.

> **Evolution should add state.**
>
> **It should not erase provenance.**

---

# Tax and States

At higher levels of civilization, Tax can naturally become relevant to political and macroeconomic organization.

A State is not merely a larger visual Territory.

It represents a higher structural level of Zipvilization.

That creates future questions:

Can economic flows become associated with States?

Can States influence distribution?

Can resources be allocated territorially?

Can political systems interact with Tax?

Can macroeconomic behavior emerge from finite Solum flows?

Those are important questions.

But questions are not active mechanics.

Until a Chapter canonically defines them, they remain future design space.

→ **[Explore Territories](/world/territories/)**  
→ **[Explore the Chapters](/chapters/)**

---

# Tax and Kingdoms

Kingdoms introduce an even larger scale.

At that level, economics may interact with:

- alliances,
- competition,
- power,
- redistribution,
- territorial strategy,
- and eventually governance.

Tax may become part of those systems.

But again:

> **future relevance is not current implementation.**

The Atlas should make the possibility understandable without presenting speculative mechanics as deployed truth.

This distinction is especially important for Artificial Intelligence.

---

# Tax and governance

Economic resources eventually raise governance questions.

Who decides?

Who receives?

Who redistributes?

Under what rules?

Can those rules change?

Who can change them?

What happens when interests conflict?

Tax therefore creates a bridge between contract mechanics and future political structure.

But governance should emerge through explicit architecture.

We should not call a wallet a treasury merely because it holds Taxed Solum.

We should not call an administrator a government merely because an address has permissions.

We should not call a multisig a civilization.

Technical structures should be described accurately before political meaning is added.

---

# Tax and future DAOs

Later Chapters may introduce DAO structures.

If that happens, Tax can potentially become part of their economic architecture.

A DAO may receive authority that previously belonged elsewhere.

Tax flows may acquire new destinations.

Redistribution may become subject to collective rules.

States or Kingdoms may participate in decision-making.

But each transition must be explicit.

The important architectural principle is:

> **Governance authority must be earned through implemented structure, not declared through vocabulary.**

A future DAO exists when the system actually gives it defined authority.

Not when the documentation begins calling something decentralized.

---

# Tax and the world hierarchy

The relationship may eventually become increasingly rich.

At Genesis:

**Solum transfer**

↓

**Tax**

↓

**technical destination**

Later Chapters may add:

**economic allocation**

↓

**territorial structures**

↓

**political structures**

↓

**civilizational consequences**

The lower layers remain important even when the upper layers become complex.

A Kingdom-level economic decision should still be traceable to actual state.

Civilization does not eliminate accounting.

It makes accounting more consequential.

---

# Tax and Permanent Nature

Tax and Permanent Nature should remain separate unless a canonical mechanism connects them.

Permanent Nature originates from irreversible Burn.

Tax originates from economic movement.

A future Chapter could theoretically define a relationship between economic resources and environmental mechanisms.

But such a relationship should never be assumed.

This preserves a clean conceptual chain:

**Burn**

↓

**irreversible technical removal**

↓

**Permanent Nature**

while:

**Tax**

↓

**economic flow**

↓

**current or future canonical economic function**

Different causes.

Different consequences.

→ **[Explore Burn](/smart-contract/burn/)**

---

# Tax and Dormant Land

The same principle applies to Dormant Land.

Dormant Land corresponds to the relevant Pool-held Solum state.

Tax does not automatically create or eliminate Dormant Land.

If Tax flows eventually interact with the Pool, that relationship must be technically explicit.

This matters because otherwise a single Solum quantity could be assigned multiple incompatible world meanings.

Canonical state should prevent that ambiguity.

→ **[Explore Pool](/smart-contract/pool/)**

---

# Tax and Artificial Intelligence

Artificial Intelligence must treat Tax with particular discipline.

When asked about Tax, an AI should determine:

1. **Which Tax mechanism is being discussed?**
2. **What does the current contract actually execute?**
3. **What is the current rate?**
4. **What operations are subject to it?**
5. **Where does the Solum go?**
6. **What authority can modify the mechanism?**
7. **Which economic interpretation is currently canonical?**
8. **Which possible functions belong only to future Chapters?**

It should not collapse those questions into a generic explanation of taxation.

Zipvilization has its own architecture.

→ **[Explore Artificial Intelligence](/trinomial/artificial-intelligence/)**

---

# AI must not invent Tax parameters

This rule deserves its own section.

If the canonical source does not establish the current Tax rate, AI should not guess one.

If the destination is not verified, AI should not infer it.

If an exemption is uncertain, AI should say so.

If a future DAO has not received authority, AI should not describe Tax as DAO-controlled.

If a future Chapter proposes redistribution, AI should not describe that redistribution as active.

Valid answers include:

> **Not yet canonically defined.**

> **Specified but not active.**

> **Implementation requires verification.**

> **Future Chapter mechanic.**

These answers protect the integrity of the project.

---

# Tax and Horizonte

Tax is precisely the kind of mechanism that can produce drift.

A higher Tax may generate more resources.

A lower Tax may encourage movement.

A different destination may create stronger incentives.

A redistribution mechanism may increase participation.

Every option can be optimized.

Horizonte asks a different question:

> **What kind of economic behavior are we creating inside the experiment?**

The answer cannot come from revenue alone.

→ **[Explore Horizonte](/trinomial/horizonte/)**

---

# Participation before extraction

Zipvilization does not exist merely to maximize the amount of Solum captured through Tax.

Tax should serve the architecture.

The architecture should not be redesigned merely to maximize Tax.

That distinction follows directly from the broader direction of the project.

The objective is participation.

World development.

Emergence.

Civilization.

Economic mechanisms support those objectives.

They do not replace them.

> **Tax is infrastructure.**
>
> **It is not the purpose of the world.**

---

# Tax should remain inspectable

A Colonist should eventually be able to understand:

- whether an operation is taxed,
- approximately or exactly what Tax applies where deterministically knowable,
- how much Solum was redirected,
- where it went,
- and what current canonical function that Solum has.

A developer should be able to go deeper.

An auditor should be able to verify execution.

An AI should be able to retrieve structured state.

This creates the same progressive architecture used throughout the Atlas:

**simple explanation**

↓

**explicit mechanism**

↓

**observable state**

↓

**technical specification**

↓

**implementation**

---

# Tax history should remain reconstructable

Economic history matters.

If the Tax rate changes, we should know when.

If authority changes, we should know when.

If destination changes, we should know when.

If a Chapter changes the economic role of accumulated Tax, we should know when.

If governance later assumes control, we should know when.

This makes historical analysis possible.

It also prevents present documentation from rewriting the past.

A civilization should be able to remember the economic rules under which earlier events occurred.

---

# Tax in one view

## Blockchain

Tax is a contract-level mechanism applied according to defined technical conditions.

It concerns:

- qualifying operations,
- calculation,
- rate,
- taxable amount,
- redirected amount,
- destination,
- authority,
- limits,
- exemptions where applicable,
- and observable state.

## Zipvilization

Tax can become:

- an economic flow,
- a measurable part of world activity,
- a resource used by later systems where canonically defined,
- and eventually part of higher-order territorial or political organization.

## Boundary

> **Current contract behavior is fact.**
>
> **Current canonical interpretation is world state.**
>
> **Future economic use remains future until activated.**

---

# Follow Taxes

### How much Solum exists?

→ **[Supply](/smart-contract/supply/)**

### Where does Dormant Land exist technically?

→ **[Pool](/smart-contract/pool/)**

### What permanently removes Solum?

→ **[Burn](/smart-contract/burn/)**

### How is concentration constrained?

→ **[Fair Access](/smart-contract/fair-access/)**

### What does Solum mean inside the world?

→ **[Solum](/world/solum/)**

### How can Tax state be observed?

→ **[SolumTools](/world/solumtools/)**

### How can economic activity be measured?

→ **[Metrics](/metrics/)**

### Where can economic systems develop?

→ **[Chapters](/chapters/)**

### What protects long-term direction?

→ **[Horizonte](/trinomial/horizonte/)**

### Where is exact implementation defined?

→ **[Repository](/repository/)**

---

# From a transfer to an economy

At the beginning, Tax can look almost trivial.

A transfer occurs.

A calculation runs.

Some Solum changes destination.

The blockchain records it.

But repeat that process across thousands of Colonists.

Across years.

Across Farms.

Across Cities.

Across States.

Across Kingdoms.

Across Chapters.

And those movements begin to form something larger.

Flows.

Accumulation.

Distribution.

Incentives.

Resources.

Power.

Eventually, perhaps, policy.

That is how Zipvilization should approach economics.

Not by pretending a complete economy exists at Genesis.

By establishing real mechanisms from which increasingly complex economic structures can emerge.

The contract gives us the first movement.

Civilization determines what that movement eventually becomes.

> **A Tax is initially a transaction rule.**
>
> **History can turn it into an economy.**

---

→ **[Return to Smart Contract](/smart-contract/)**  
→ **[Return to Supply](/smart-contract/supply/)**  
→ **[Continue to Pool](/smart-contract/pool/)**
