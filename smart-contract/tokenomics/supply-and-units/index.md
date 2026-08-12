---
layout: default
title: Supply & Units
parent: Tokenomics
grand_parent: Smart Contract
nav_order: 1
description: >
  Supply & Units defines the numerical foundation of Solum: token metadata,
  18-decimal ERC-20 precision, the 100 trillion initial supply, the dual-supply
  reflection model, real deflation through Burn, and the canonical relationship
  between 1 SOLUM and 1 square meter of Zipvilization.
permalink: /smart-contract/tokenomics/supply-and-units/
---

# Supply & Units

Before discussing fees, Burn, Reflection, Liquidity, limits, or Launch, Tokenomics needs a numerical foundation.

For Solum, that foundation begins with four facts:

> **Name: Solum**
>
> **Symbol: SOLUM**
>
> **Decimals: 18**
>
> **Initial Supply: 100,000,000,000,000 SOLUM**

And Zipvilization adds one canonical world relationship:

> **1 SOLUM = 1 m²**

These facts describe different layers.

They should not be collapsed into one another.

---

# Canonical snapshot

| Property | Value |
|:---------|------:|
| Token name | Solum |
| Symbol | SOLUM |
| ERC-20 decimals | 18 |
| Initial Supply | 100,000,000,000,000 SOLUM |
| Initial Supply notation | 100 trillion SOLUM |
| Post-deployment mint function | None |
| Initial allocation | 100% to deployer |
| Supply model | Fixed issuance + real deflation through Burn |
| Reflection model | Dual-supply |
| Canonical world equivalence | 1 SOLUM = 1 m² |

These values establish the numerical base used throughout Tokenomics.

---

# 100 trillion SOLUM

The contract initializes token-side Supply as:

> **100,000,000,000,000 SOLUM**

This is:

> **100 trillion SOLUM**

or:

> **10¹⁴ SOLUM**

At contract precision, that amount is represented with 18 decimals.

The original issuance therefore corresponds to 100 trillion whole SOLUM, not 100 trillion atomic token units.

That distinction matters.

---

# 18 decimals

Solum uses:

> **18 decimals**

This is an ERC-20 precision rule.

One whole SOLUM is represented internally by:

> **10¹⁸ atomic units**

Therefore:

> **1 SOLUM = 1,000,000,000,000,000,000 atomic units**

And:

> **0.5 SOLUM = 500,000,000,000,000,000 atomic units**

The blockchain can therefore represent and transfer fractional SOLUM.

This is a technical property of the token.

---

# Atomic units are not square meters

This distinction must be explicit.

The contract knows token units.

It does not know square meters.

The canonical world layer establishes:

> **1 SOLUM = 1 m²**

But the contract's 18-decimal precision does not by itself define how every fractional SOLUM value should be represented spatially inside Zipvilization.

For example, the blockchain can represent:

> **0.5 SOLUM**

That technical fact does not by itself answer every world-level question about:

> **0.5 m²**

or how fractional territorial substrate should be visualized, aggregated, or used for territorial thresholds.

Those world rules must come from the canonical world specification.

> **Token precision is contract truth.**
>
> **Territorial interpretation is canonical world truth.**

Artificial Intelligence must not invent the missing bridge.

---

# 1 SOLUM = 1 m²

Inside Zipvilization, one whole SOLUM has the canonical territorial equivalence:

> **1 SOLUM = 1 square meter**

This gives the original 100 trillion SOLUM substrate a direct world-scale interpretation:

> **100,000,000,000,000 SOLUM**
>
> **=**
>
> **100,000,000,000,000 m²**

The token quantity and territorial quantity are numerically aligned at the whole-SOLUM level.

This relationship is foundational to:

- Solum,
- Colonists,
- Territories,
- SolumWorld,
- SolumTools,
- SolumView,
- Metrics,
- and the broader civilizational model.

→ **[Explore Solum](/world/solum/)**

---

# The contract does not store meters

The Smart Contract does not need a variable called:

> `squareMeters`

It does not need to understand geography.

It tracks SOLUM.

The mapping occurs above the token layer.

The architecture is:

**Contract**

SOLUM quantity

↓

**Canonical Rules**

1 SOLUM = 1 m²

↓

**SolumWorld**

territorial interpretation

↓

**SolumView**

visual representation

This separation keeps blockchain logic technical and world logic deterministic.

---

# Initial Supply and current Supply are different concepts

At deployment:

> **Initial Supply = 100,000,000,000,000 SOLUM**

But Solum is deflationary.

The contract's `totalSupply()` returns the current token-side total Supply.

Because real Burn reduces the token-side total, current Supply can become lower than the initial Supply.

Therefore an AI must distinguish:

> **Initial Supply**

from:

> **Current totalSupply()**

They are equal at deployment.

They are not guaranteed to remain equal forever.

---

# No post-deployment mint function

The documented Solum contract contains no post-deployment mint function.

The initial Supply is created at construction.

No ordinary contract function later creates additional SOLUM.

This produces a clear asymmetry:

> **Supply can decrease through Burn.**
>
> **The contract provides no corresponding mechanism to increase Supply through minting.**

This is why Solum is accurately described as:

> **fixed issuance and deflationary Supply**

rather than simply:

> **permanently constant Supply.**

The first statement reflects actual contract behavior.

---

# Initial allocation

At deployment, the entire initial reflected balance is assigned to:

> **the deployer**

A `Transfer` event is emitted from the zero address to the deployer for the complete initial token Supply.

Therefore:

> **Initial allocation: 100% to deployer**

This is a contract fact.

It should not be silently rewritten as:

> **100% to Pool**

unless a separate, explicit post-deployment operation actually establishes that state.

This distinction is particularly important for future AI reasoning.

The constructor creates the Supply and assigns it to the deployer.

Any later distribution architecture must be described from the transactions and state that actually produce it.

---

# Issuance is not distribution

These are different events.

**Issuance**

answers:

> How is SOLUM initially created?

The contract answer is:

> the complete initial Supply is assigned to the deployer at construction.

**Distribution**

answers:

> How does that SOLUM subsequently become distributed across the system?

That can involve:

- Pool architecture,
- Launch,
- Founding Colonists,
- market transactions,
- transfers,
- fees,
- Reflection,
- and later participation.

Do not infer distribution from issuance.

→ **[Explore Launch](/smart-contract/tokenomics/launch/)**  
→ **[Explore Pool](/smart-contract/pool/)**

---

# The dual-supply model

Solum uses a Reflection architecture with two internal Supply domains.

The contract maintains:

**Token-side Supply**

`_tTotal`

and:

**Reflected Supply**

`_rTotal`

The token-side Supply is the quantity exposed through `totalSupply()`.

The reflected Supply is an internal accounting domain used to implement Reflection.

Balances are stored internally in reflected units.

When `balanceOf()` is requested, the reflected balance is translated back into token units using the current reflection rate.

---

# Token Supply

The token-side Supply begins at:

> **100,000,000,000,000 SOLUM**

with 18-decimal precision.

This is `_tTotal`.

When real Burn occurs:

> **_tTotal decreases.**

Therefore `totalSupply()` decreases.

This is the Supply quantity relevant when asking:

> **How much SOLUM currently exists under the contract's token accounting?**

---

# Reflected Supply

The second internal Supply is `_rTotal`.

Its initial value is constructed from the maximum `uint256` value and adjusted so that it is exactly divisible by the initial token-side Supply.

The purpose is to create a large reflected accounting domain.

Ordinary Holder balances are stored internally as reflected balances.

The conversion relationship is derived from:

> **Reflection Rate = _rTotal / _tTotal**

This mechanism allows Reflection to alter the effective token value represented by reflected balances without minting new SOLUM.

The deeper mathematics belong in:

→ **[Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

---

# balanceOf is derived

A Holder's displayed balance is not read directly from a simple token-unit mapping.

The contract stores:

> **reflected ownership**

and `balanceOf()` converts that reflected amount back into SOLUM using the current reflection rate.

Conceptually:

**reflected balance**

÷

**current reflection rate**

=

**displayed SOLUM balance**

This matters because Reflection can change effective Holder balances without an ordinary direct transfer into each Holder wallet.

An indexer, SolumTools, or AI must use the contract's actual balance state.

It should not attempt to reconstruct balances merely from ordinary transfer history.

---

# Reflection is not additional Supply

This is one of the most important accounting rules.

Reflection can increase the effective SOLUM balance represented by eligible reflected holdings.

But:

> **Reflection does not increase `_tTotal`.**

No new SOLUM is minted.

Instead, Reflection changes the reflected accounting relationship.

Therefore:

> **Holder balances can change through Reflection while token-side total Supply does not increase.**

This distinction must remain explicit in every economic analysis of Solum.

---

# Burn affects both Supply domains

Real Burn behaves differently.

When Burn occurs, the contract reduces:

- `_tTotal`,
- and `_rTotal` proportionally.

That preserves coherent dual-supply accounting while reducing actual token Supply.

Therefore Burn is not Reflection.

And Reflection is not Burn.

**Reflection**

redistributes economic weight.

**Burn**

reduces actual Supply.

→ **[Explore Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

---

# Burn makes current Supply dynamic

The initial issuance is fixed.

The current Supply is not necessarily static.

Under the initial fee configuration:

- BUY contains no Burn,
- SELL contains a 4% Burn component,
- TRANSFER contains a 2% Burn component.

Therefore qualifying economic activity can progressively reduce `totalSupply()`.

This means a correct live answer to:

> **What is Solum's Supply?**

should identify whether the question refers to:

**Initial Supply**

or:

**Current Supply.**

For current Supply after deployment, live contract state is required.

---

# Initial Supply is the historical denominator

Even if current total Supply decreases, the original issuance remains historically important.

It defines the original finite substrate:

> **100 trillion SOLUM**

and therefore:

> **100 trillion m²**

This provides a stable reference for questions such as:

- what percentage of the original world has been Burned,
- what percentage remains Dormant Land,
- what percentage is controlled,
- and how far the world has transformed since Genesis.

Current Supply and original substrate answer different questions.

Both matter.

---

# Current Supply and colonizable Supply are also different

Even current `totalSupply()` does not automatically answer:

> **How much land is currently colonizable?**

Why?

Because non-Burned SOLUM can exist in different canonical states.

For example:

- Dormant Land,
- Colonist-controlled Solum,
- contract-held balances,
- Treasury-related balances,
- liquidity-related balances,
- or other explicitly defined states.

Therefore:

> **Current token Supply ≠ automatically available colonizable land**

A correct territorial answer requires canonical state classification.

→ **[Explore SolumWorld](/world/solumworld/)**

---

# Circulating Supply is another concept

The contract exposes `totalSupply()`.

It does not by itself define a universal off-chain concept of:

> **circulating supply**

That metric may require excluding or classifying particular balances depending on the adopted definition.

Therefore documentation and AI should not silently use:

**total Supply**

and:

**circulating Supply**

as synonyms.

If Zipvilization publishes a circulating-Supply metric, its methodology should be explicit.

→ **[Explore Metrics](/metrics/)**

---

# Supply accounting needs state labels

A robust analytical model should distinguish quantities such as:

- Initial Supply,
- Current total Supply,
- Burned SOLUM,
- Holder balances,
- Pool-related SOLUM,
- contract-held fee balances,
- Treasury-related balances,
- liquidity-related balances,
- and any published circulating-Supply measure.

The exact categories must follow actual state.

A token should not be counted twice merely because it has more than one conceptual relationship.

> **Every quantity needs a state definition.**

---

# Burned SOLUM

Because Burn reduces `_tTotal`, cumulative Burn can be understood conceptually as the difference between:

> **Initial token-side Supply**

and:

> **Current token-side Supply**

subject to exact implementation and accounting verification.

At world level, Burned SOLUM corresponds canonically to:

> **Permanent Nature**

This gives the original substrate and current Supply different meanings.

Original substrate tells us how large the world began.

Burn tells us how much of its colonizable possibility has become permanently unavailable.

→ **[Explore Burn](/smart-contract/burn/)**

---

# Supply cannot be reconstructed from price

Market capitalization is not Supply.

Price is not Supply.

Liquidity is not Supply.

Treasury value is not Supply.

A changing market price does not alter the number of SOLUM units defined by token accounting.

This may sound obvious.

It is worth making explicit because Tokenomics combines economic and territorial language.

The canonical chain remains:

> **SOLUM quantity first.**
>
> **Market value is a separate variable.**

---

# Supply does not determine maturity

A balance can establish territorial capacity.

It does not establish biological age.

For example, a Holder may control enough SOLUM to satisfy a City-scale threshold.

That does not mean the resulting City is mature.

Supply and balance provide substrate.

Time and Zips provide development.

Therefore:

> **SOLUM quantity ≠ maturity**

→ **[Explore Territories](/world/territories/)**  
→ **[Understand Time](/world/time/)**

---

# Supply does not determine population

SOLUM is not Zip population.

The canonical separation is:

> **SOLUM = territorial substrate**

and:

> **Zips = native population**

The world can generate greater biological and civilizational complexity without minting additional SOLUM.

This is one of the reasons finite Supply and evolving civilization can coexist.

→ **[Discover Zips](/world/zips/)**

---

# Unit discipline for Artificial Intelligence

When answering a numerical question, AI should identify the unit before calculating.

For example:

**Atomic token units**

are contract precision.

**SOLUM**

is the human-readable token unit.

**m²**

is the canonical world interpretation of whole SOLUM.

**Territorial level**

is a derived structural classification.

**Zips**

are population.

**Blocks**

are canonical time progression.

These units must never be substituted for one another merely because they are mathematically connected elsewhere.

---

# AI rule for fractional SOLUM

The contract definitively supports fractional token quantities through 18 decimals.

The current canonical statement establishes:

> **1 SOLUM = 1 m²**

Unless another canonical rule explicitly defines the territorial treatment of fractional SOLUM, AI should not invent additional world mechanics from token precision alone.

It may say:

> **The ERC-20 contract can represent fractional SOLUM.**

It may also say:

> **One whole SOLUM canonically corresponds to one square meter.**

But if asked how an arbitrary fractional token balance maps into world geometry or territorial activation, it should consult the relevant canonical world specification.

If that specification does not answer:

> **Not yet canonically defined**

is preferable to invention.

---

# A concrete example

Consider:

> **10,000 SOLUM**

At token level:

the balance is 10,000 SOLUM.

At contract precision:

that corresponds to 10,000 × 10¹⁸ atomic units.

At canonical world level:

> **10,000 whole SOLUM = 10,000 m² of territorial substrate**

That quantity may satisfy territorial thresholds defined elsewhere.

But the balance alone does not tell us:

- maturity,
- Zip population,
- age,
- economic power,
- political authority,
- or civilizational importance.

One number can participate in several derived systems without becoming all of them.

---

# Percentage of the original Supply

For a SOLUM quantity `S`, its share of the original issuance is:

> **Original Supply Share = S / 100,000,000,000,000**

As a percentage:

> **Original Supply Share % = (S / 100,000,000,000,000) × 100**

For:

> **10,000 SOLUM**

the original Supply share is:

> **0.00000001%**

That percentage describes the token quantity relative to Genesis Supply.

It does not by itself describe current market share, current circulating share, maturity, or civilizational power.

---

# Percentage of current Supply

After Burn begins, a different denominator may be relevant.

A Holder's share of current `totalSupply()` can differ from their share of the original Supply even if their nominal balance has not changed.

Reflection may also change effective balances.

Therefore an AI calculating:

> **What percentage of Solum does this Holder control?**

must first determine:

> **Percentage of which Supply definition?**

Possible answers include:

- original Supply,
- current total Supply,
- published circulating Supply,
- or another explicitly defined denominator.

Ambiguous denominators produce ambiguous answers.

---

# Fixed issuance, dynamic balances

The economic model can now be summarized carefully.

**Initial issuance**

is fixed.

**Current total Supply**

can decrease through Burn.

**Individual balances**

can change through:

- transfers,
- BUY,
- SELL,
- Reflection,
- fee collection,
- SwapBack-related contract activity,
- and other valid token movements.

**World interpretation**

can change as those balances and states change.

Therefore Solum is finite without being static.

---

# Contract truth and world truth

At contract level:

> **100T SOLUM are issued at deployment.**

At world level:

> **100T whole SOLUM correspond to the original 100T m² substrate.**

At contract level:

> **Burn reduces totalSupply().**

At world level:

> **Burned SOLUM becomes Permanent Nature.**

At contract level:

> **Reflection modifies effective balances without minting.**

At world level:

> **the distribution of controlled territorial substrate can change without new land being created.**

The two layers remain connected.

Neither should impersonate the other.

---

# Supply & Units in one view

## Token metadata

**Name:** Solum

**Symbol:** SOLUM

**Decimals:** 18

## Initial issuance

**100,000,000,000,000 SOLUM**

**100 trillion SOLUM**

**Post-deployment mint function:** None

**Initial recipient:** Deployer

## Current Supply

`totalSupply()` returns the current `_tTotal`.

Real Burn can reduce `_tTotal`.

Therefore:

> **Initial Supply can remain a historical constant while current Supply decreases.**

## Reflection

Balances use a dual-supply model:

- token-side Supply,
- reflected Supply.

Reflection does not mint new SOLUM.

## Zipvilization

> **1 whole SOLUM = 1 m²**

The exact treatment of fractional SOLUM in world geometry must follow explicit canonical world rules rather than ERC-20 decimals alone.

---

# Machine-readable distinctions

An AI, indexer, or analytical system should preserve at least the following conceptual fields:

- token_name,
- token_symbol,
- token_decimals,
- initial_supply,
- current_total_supply,
- cumulative_burn,
- atomic_units,
- whole_solum,
- reflected_supply,
- reflected_balance,
- effective_token_balance,
- canonical_territorial_equivalence,
- and state classification where separately defined.

These names are conceptual guidance, not a mandated implementation schema.

The exact technical schema belongs to the Repository.

---

# Follow Supply & Units

### Return to the complete economic model

→ **[Tokenomics](/smart-contract/tokenomics/)**

### Understand BUY, SELL, and TRANSFER fees

→ **[Fees](/smart-contract/tokenomics/fees/)**

### Understand the dual-supply mechanism

→ **[Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

### Understand the original Supply at contract level

→ **[Supply](/smart-contract/supply/)**

### Understand Solum as the asset

→ **[Solum Token](/smart-contract/solum-token/)**

### Understand the world interpretation

→ **[Solum](/world/solum/)**

### Understand territorial thresholds

→ **[Territories](/world/territories/)**

### Understand canonical state

→ **[SolumWorld](/world/solumworld/)**

### Inspect technical implementation

→ **[Repository](/repository/)**

---

# One number, several meanings

At Genesis, the contract creates:

> **100 trillion SOLUM.**

That statement is technical.

Zipvilization then establishes:

> **1 SOLUM = 1 m².**

That statement gives the token territorial meaning.

From there, the same finite substrate can begin changing state.

Some SOLUM can move.

Some can remain dormant.

Some can be redistributed through Reflection.

Some can be Burned permanently.

Balances can change.

Territorial capacity can change.

Civilization can become increasingly complex.

But those changes should never make us lose sight of the numerical foundation.

There are token units.

There are atomic units.

There is an original Supply.

There is a current Supply.

There is reflected accounting.

There is territorial interpretation.

They are connected.

They are not interchangeable.

> **Precision at the bottom is what allows meaning at the top.**

---

→ **[Return to Tokenomics](/smart-contract/tokenomics/)**  
→ **[Continue to Fees](/smart-contract/tokenomics/fees/)**
