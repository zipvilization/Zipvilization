---
layout: default
title: Burn & Reflection
parent: Tokenomics
grand_parent: Smart Contract
nav_order: 3
description: >
  Burn & Reflection explains Solum's dual-supply accounting model, how
  Reflection redistributes effective token ownership without minting, how real
  Burn reduces totalSupply(), and how Burn becomes Permanent Nature inside
  Zipvilization.
permalink: /smart-contract/tokenomics/burn-and-reflection/
---

# Burn & Reflection

Burn and Reflection both affect Solum's internal accounting.

They do not do the same thing.

**Reflection**

redistributes effective SOLUM ownership without minting new SOLUM.

**Burn**

reduces the actual token Supply.

This distinction is fundamental.

> **Reflection redistributes.**
>
> **Burn removes.**

Inside Zipvilization, Burn has an additional canonical consequence:

> **Burned SOLUM becomes Permanent Nature.**

To understand why these statements are technically different, we need to understand Solum's dual-supply model.

---

# Canonical snapshot

| Mechanism | Initial BUY | Initial SELL | Initial TRANSFER |
|:----------|------------:|-------------:|-----------------:|
| Burn | 0% | 4% | 2% |
| Reflection | 0% | 3% | 3% |

And their core contract effects are different:

| Mechanism | `_tTotal` | `_rTotal` | New SOLUM minted? |
|:----------|:----------:|:---------:|:-----------------:|
| Reflection | Unchanged | Decreases | No |
| Burn | Decreases | Decreases proportionally | No |

The consequences are therefore different.

---

# Two accounting domains

Solum uses two related internal quantities.

## Token-side Supply

`_tTotal`

This is the token Supply returned by:

`totalSupply()`

At deployment:

> **_tTotal = 100,000,000,000,000 SOLUM**

with 18-decimal token precision.

## Reflected Supply

`_rTotal`

This is a much larger internal accounting quantity used by the Reflection mechanism.

Balances are stored internally in reflected units through:

`_rOwned`

The contract converts those reflected balances into human-readable SOLUM using the current reflection rate.

---

# The reflection rate

The contract derives the current rate as:

> **Reflection Rate = _rTotal / _tTotal**

A reflected balance is converted into token units as:

> **SOLUM Balance = Reflected Balance / Reflection Rate**

This relationship is the core of Reflection.

The contract does not need to transfer a Reflection reward individually to every wallet.

Instead, it changes the global reflected accounting relationship.

---

# Holder balances are reflected balances

Internally, ordinary balances are stored in:

`_rOwned[address]`

When `balanceOf(address)` is called, the contract converts that reflected amount using the current reflection rate.

Therefore a Holder's visible SOLUM balance can change even if no ordinary incoming `Transfer` event sent Reflection rewards directly to that wallet.

This is intentional.

> **Reflection is distributed through accounting.**
>
> **It is not distributed through one reward transfer per Holder.**

---

# Reflection

When a qualifying transaction produces a Reflection component, the contract calculates that amount in token units.

It then converts the amount using the current reflection rate.

The Reflection operation reduces:

> **_rTotal**

by the reflected equivalent of the Reflection fee.

It does not reduce:

> **_tTotal**

Therefore:

> **totalSupply() does not increase.**

And:

> **totalSupply() does not decrease because of Reflection alone.**

The token-side Supply remains unchanged.

---

# Why Reflection increases effective balances

Suppose `_tTotal` remains constant while `_rTotal` decreases.

Then:

> **_rTotal / _tTotal**

becomes smaller.

That means the Reflection Rate decreases.

Because a Holder's displayed balance is calculated by dividing their reflected balance by that rate:

> **Reflected Balance / smaller rate = larger effective SOLUM balance**

This is how Reflection redistributes economic weight.

No mint transaction is required.

No new `_tTotal` is created.

The accounting relationship changes.

---

# Reflection is not minting

This deserves an explicit rule.

Reflection can increase the effective SOLUM balance represented by an existing reflected holding.

But the contract does not increase `_tTotal` to do so.

Therefore:

> **Reflection ≠ Minting**

A Holder may gain effective SOLUM through Reflection.

The total token-side Supply does not expand because of that redistribution.

This preserves the finite issuance architecture.

→ **[Explore Supply & Units](/smart-contract/tokenomics/supply-and-units/)**

---

# Reflection is global accounting

The documented contract does not maintain a second token-balance mapping for excluded Reflection accounts.

It uses the reflected ownership model globally.

This means the Reflection mechanism operates through the common `_rOwned` accounting architecture rather than a separate included/excluded Reflection population.

Fee exemptions are a different mechanism.

An address can be Fee Exempt from generating an ordinary transaction fee.

That is not the same thing as being structurally excluded from reflected balance accounting.

These concepts must not be confused.

---

# Reflection sources

Under the initial fee configuration:

## BUY

> **0% Reflection**

## SELL

> **3% Reflection**

## TRANSFER

> **3% Reflection**

Therefore SELL and ordinary wallet-to-wallet TRANSFER can modify the Reflection accounting state.

BUY does not directly contribute a Reflection fee under the initial configuration.

---

# SELL Reflection example

Consider an ordinary non-exempt SELL of:

> **1,000 SOLUM**

The initial SELL Reflection component is:

> **30 SOLUM**

The transaction also includes other components:

- 40 SOLUM Burn,
- 20 SOLUM Liquidity,
- 10 SOLUM Treasury.

But only the Reflection component produces the Reflection-specific `_rTotal` reduction.

The 30 SOLUM are not minted.

They are not transferred individually to every Holder.

The reflected accounting rate changes.

---

# TRANSFER Reflection example

Consider an ordinary non-exempt wallet-to-wallet TRANSFER of:

> **1,000 SOLUM**

The initial Reflection component is:

> **30 SOLUM**

The transaction also Burns:

> **20 SOLUM**

The recipient receives:

> **950 SOLUM**

before considering the indirect future effect of Reflection on reflected balances.

Again:

> **Reflection does not require additional Supply.**

---

# Reflection changes relative ownership

Reflection has an important economic consequence.

A Holder who remains inside the reflected accounting system can experience an increase in effective SOLUM balance as Reflection occurs.

That means ownership distribution can evolve even when the Holder does not directly:

- BUY,
- receive an ordinary TRANSFER,
- or receive newly minted tokens.

This makes current `balanceOf()` state essential.

Historical direct transfers alone do not fully describe current ownership.

---

# Reflection and territorial interpretation

Inside Zipvilization:

> **SOLUM balance contributes to controlled territorial substrate.**

Therefore Reflection can affect the amount of SOLUM represented by a Holder's balance without creating new world substrate.

This is an unusual but important distinction.

The original world does not grow.

The distribution of claims over non-Burned SOLUM can change.

> **Reflection can change control.**
>
> **Reflection does not create new land.**

Any resulting territorial classification must be based on current canonical balance state.

→ **[Explore SolumWorld](/world/solumworld/)**

---

# Reflection can cross a territorial threshold

Because Reflection can change effective Holder balances, it can theoretically affect whether a balance satisfies a canonical territorial threshold.

For example, a balance close to a threshold may later exceed that threshold through the cumulative effect of Reflection.

But the correct chain remains:

**Reflection changes effective SOLUM balance**

↓

**current balance is observed**

↓

**canonical territorial threshold is evaluated**

↓

**SolumWorld determines resulting territorial state**

Reflection itself does not directly execute:

> create City

or:

> upgrade Territory

Those are world interpretations of resulting state.

---

# Reflection does not create maturity

A balance change can affect territorial capacity.

It does not retroactively create biological history.

If Reflection causes a balance to satisfy a higher territorial threshold, any new developmental capacity must still follow the canonical Time and Zip rules.

Therefore:

> **Reflection may change land control.**
>
> **It does not manufacture elapsed time.**

→ **[Understand Time](/world/time/)**

---

# Burn

Burn uses a fundamentally different operation.

When a transaction contains a Burn component, the contract reduces:

> **_tTotal**

and:

> **_rTotal**

by the corresponding reflected amount.

It also emits a transfer event to:

> **address(0)**

for the Burned token amount.

The result is actual token-side Supply reduction.

> **Burn reduces totalSupply().**

---

# Real Burn

This distinction matters because not every token system implements Burn in the same way.

Some systems send tokens to an inaccessible or conventional dead address while leaving `totalSupply()` numerically unchanged.

Solum's documented mechanism does more.

It directly reduces:

> **_tTotal**

Therefore the value returned by `totalSupply()` decreases.

That is why we describe it as:

> **real Burn**

in the token-side accounting sense.

---

# Burn event

When Burn occurs, the contract emits:

> **Transfer(from, address(0), Burn amount)**

This provides a conventional ERC-20-style observable event corresponding to the Burn.

But the event is not the entire mechanism.

The important Supply consequence is:

> **_tTotal decreases.**

An indexer should therefore distinguish Burn event observation from current Supply accounting while connecting both correctly.

---

# Burn preserves the reflection relationship

The contract calculates the current Reflection Rate before processing the transaction.

For Burn, it reduces:

- token-side Supply by `tBurn`,
- reflected Supply by the corresponding `tBurn × rate`.

The code is explicitly designed so that both totals decrease together for real Burn.

This differs from Reflection, where only `_rTotal` decreases.

That difference is what separates:

**Supply contraction**

from:

**Reflection redistribution.**

---

# Burn sources

Under the initial fee configuration:

## BUY

> **0% Burn**

## SELL

> **4% Burn**

## TRANSFER

> **2% Burn**

Therefore ordinary SELL and TRANSFER activity can reduce current SOLUM Supply.

BUY does not directly reduce Supply through its initial fee structure.

---

# SELL Burn example

Consider an ordinary non-exempt SELL of:

> **1,000 SOLUM**

Initial Burn:

> **40 SOLUM**

If current total Supply immediately before the transaction were represented as `S`, then, ignoring other simultaneous Burn events:

> **new total Supply = S − 40 SOLUM**

The same transaction also creates Reflection, Liquidity, and Treasury components.

Those mechanisms must not be confused with the Burn amount.

---

# TRANSFER Burn example

For an ordinary non-exempt TRANSFER of:

> **1,000 SOLUM**

Initial Burn:

> **20 SOLUM**

Therefore direct wallet-to-wallet movement can also reduce current total Supply.

Inside Zipvilization, that produces a permanent territorial consequence.

---

# Burn is not Reflection

The difference can be summarized precisely.

## Reflection

- `_rTotal` decreases,
- `_tTotal` remains unchanged,
- reflection rate changes,
- effective reflected balances redistribute,
- no new SOLUM is minted,
- token-side Supply does not contract from Reflection alone.

## Burn

- `_tTotal` decreases,
- `_rTotal` decreases proportionally,
- token-side Supply contracts,
- a zero-address Transfer event is emitted,
- Burned SOLUM becomes permanently unavailable.

Both mechanisms use the dual-supply architecture.

Their economic effects are different.

---

# Burn is not a Reflection reward

Burned SOLUM is not subsequently distributed as Reflection.

The transaction calculates separate:

- Burn,
- Reflection,
- Liquidity,
- Treasury

components.

Each follows its own execution path.

Therefore a 40 SOLUM Burn and a 30 SOLUM Reflection are not two descriptions of the same 70 SOLUM.

They are distinct allocations from the transaction fee.

---

# Burn does not enter the contract bucket

Burn is also different from Liquidity and Treasury.

Liquidity and Treasury token components are credited to the contract and tracked for later SwapBack.

Burn is not stored for later processing.

Its Supply effect occurs during the transaction.

Therefore:

> **Burn is immediate Supply contraction.**

while:

> **Liquidity and Treasury are accumulated token buckets.**

→ **[Explore Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**

---

# Reflection does not enter the contract bucket

Reflection also does not enter `_tokensForLiquidity` or `_tokensForTreasury`.

It is handled through `_rTotal`.

This gives all four SELL allocations different meanings:

| Component | Primary execution consequence |
|:----------|:------------------------------|
| Burn | Reduces `_tTotal` and `_rTotal` |
| Reflection | Reduces `_rTotal` |
| Liquidity | Accumulates in contract for SwapBack |
| Treasury | Accumulates in contract for SwapBack |

The fee split is economic allocation.

The implementation path depends on the destination.

---

# Permanent Nature

Now we move from blockchain to Zipvilization.

The canonical relationship is:

> **Burned SOLUM = Permanent Nature**

Because:

> **1 whole SOLUM = 1 m²**

a Burn of one whole SOLUM corresponds canonically to one square meter of territorial substrate becoming unavailable to future colonization.

For example:

> **40 whole SOLUM Burned**

corresponds to:

> **40 m² of Permanent Nature**

at the canonical whole-SOLUM territorial level.

---

# Burn does not destroy the planet

The blockchain Supply contracts.

The world interpretation does not require the corresponding land to disappear visually.

Instead, its state changes.

Before Burn:

> potentially colonizable substrate.

After Burn:

> **Permanent Nature.**

The territory remains part of the world.

Civilization loses the ability to claim it again.

This is why Burn has a richer meaning inside Zipvilization than simple token destruction.

→ **[Explore Burn](/smart-contract/burn/)**

---

# Burn changes the colonizable future

Permanent Nature is not Dormant Land.

Dormant Land still preserves future colonization potential.

Permanent Nature does not.

Therefore:

**Pool-held SOLUM**

↓

**Dormant Land**

↓

future colonization remains possible

while:

**Burned SOLUM**

↓

**Permanent Nature**

↓

future colonization becomes impossible

These states must remain distinct in every layer.

→ **[Explore Pool](/smart-contract/pool/)**

---

# The world can become more natural as Supply contracts

This creates the deliberate inversion at the center of Zipvilization.

In crypto:

> Burn means token destruction.

In Zipvilization:

> Burn means the corresponding land becomes permanent Nature.

Therefore declining SOLUM Supply can correspond to increasing Permanent Nature.

Conceptually:

> **Current SOLUM Supply decreases**
>
> while
>
> **Permanent Nature increases**

The two measurements describe different layers of the same irreversible event.

---

# Cumulative Burn

Because the original token-side Supply is known, Burn creates a measurable historical quantity.

At a high level:

> **Cumulative Burn = Initial Supply − Current totalSupply()**

under the documented architecture where real Burn is the mechanism reducing `_tTotal`.

This gives us a direct global measure of how much original SOLUM substrate has been removed from active token Supply.

Inside Zipvilization, that quantity can be interpreted as cumulative Permanent Nature according to the canonical territorial rules.

---

# Percentage of original world Burned

Using the initial Supply as historical denominator:

> **Permanent Nature Share = Cumulative Burn / Initial Supply**

As a percentage:

> **Permanent Nature % = (Cumulative Burn / 100,000,000,000,000) × 100**

This is one of the most fundamental long-term metrics of Zipvilization.

It measures an irreversible transformation of the original world.

→ **[Explore Metrics](/metrics/)**

---

# Burn increases scarcity

Burn reduces current token-side Supply.

That means fewer SOLUM remain in existence after each Burn.

This can alter scarcity.

But scarcity is a technical and economic consequence.

It is not a guarantee of price appreciation.

A smaller Supply does not mathematically guarantee:

- higher price,
- greater demand,
- market success,
- or economic stability.

Tokenomics should distinguish:

> **Supply contraction**

from:

> **market outcome.**

---

# Reflection also changes concentration

Reflection can modify effective balances proportionally through the reflected accounting system.

Therefore Tokenomics must consider two simultaneous distribution forces.

**Burn**

reduces total Supply.

**Reflection**

changes effective ownership distribution without minting.

Together, they mean that Solum economics cannot be analyzed only by looking at direct BUY and SELL amounts.

Current balance state matters.

Current Supply matters.

Reflection history matters.

---

# A combined SELL example

Consider an ordinary non-exempt SELL of:

> **1,000 SOLUM**

under the initial configuration.

The complete fee is:

> **100 SOLUM**

divided into:

| Component | SOLUM | Contract effect |
|:----------|------:|:----------------|
| Burn | 40 | Reduces token and reflected Supply |
| Reflection | 30 | Reduces reflected Supply only |
| Liquidity | 20 | Accumulates in contract |
| Treasury | 10 | Accumulates in contract |
| Net transfer | 900 | Credited to recipient side |

At world level:

> **40 whole SOLUM Burned → 40 m² Permanent Nature**

The Reflection component may alter effective balances elsewhere.

The Liquidity and Treasury components remain available for later SwapBack processing.

One SELL therefore changes several dimensions simultaneously.

---

# A combined TRANSFER example

Consider an ordinary non-exempt TRANSFER of:

> **1,000 SOLUM**

Initial fee:

> **50 SOLUM**

divided into:

| Component | SOLUM | Contract effect |
|:----------|------:|:----------------|
| Burn | 20 | Reduces token and reflected Supply |
| Reflection | 30 | Reduces reflected Supply only |
| Net recipient amount | 950 | Credited to recipient |

At world level:

> **20 whole SOLUM Burned → 20 m² Permanent Nature**

No Liquidity bucket is created.

No Treasury bucket is created.

---

# A BUY does neither initially

Consider an ordinary non-exempt BUY of:

> **1,000 SOLUM**

Initial fee:

> **10 SOLUM**

divided into:

- 5 SOLUM Liquidity,
- 5 SOLUM Treasury.

There is:

> **0 Burn**

and:

> **0 Reflection**

from the BUY fee itself.

Therefore the BUY does not directly change `_tTotal` or `_rTotal` through Burn or Reflection fee components.

Other contract-state changes still occur through the transfer.

---

# Fee reductions reduce Burn and Reflection

Burn and Reflection percentages are derived from the current transaction-type fee.

Therefore if SELL or TRANSFER fees are reduced, the corresponding absolute Burn and Reflection rates decline proportionally according to the fixed internal allocation rules.

This means future Burn intensity is not necessarily permanently fixed at:

> **4% SELL**

and:

> **2% TRANSFER**

Those are initial effective rates.

Current rates depend on current total fees.

→ **[Explore Fees](/smart-contract/tokenomics/fees/)**

---

# Example: reduced SELL fee

If the SELL total fee were reduced canonically to:

> **5%**

the structural SELL split would still allocate:

- 40% of that fee to Burn,
- 30% to Reflection,
- 20% to Liquidity,
- 10% to Treasury.

That would correspond conceptually to effective rates of:

- 2% Burn,
- 1.5% Reflection,
- 1% Liquidity,
- 0.5% Treasury,

subject to exact contract integer arithmetic.

This is an explanatory example.

It does not state that the live SELL fee has actually been changed to 5%.

---

# Reflection arithmetic is integer arithmetic

The contract performs its calculations with integer values.

Reflection Rate is derived through integer division.

Fee components are also calculated through integer arithmetic.

Therefore mathematically neat decimal examples may differ at very small atomic-unit scales because of truncation.

For exact transaction simulation:

> **use contract arithmetic.**

Do not substitute abstract floating-point mathematics for the Solidity implementation.

---

# Burn and atomic units

Burn can also operate on fractional SOLUM represented through atomic units.

The blockchain does not require Burn amounts to be whole SOLUM.

The world canon, however, must define how fractional SOLUM maps into territorial representation if that granularity becomes relevant.

Therefore AI should distinguish:

> **exact Burn amount in token units**

from:

> **whole-square-meter world explanations**

when fractions are present.

Do not silently round an irreversible event.

---

# Reflection and current balances

Because Reflection changes the rate used by `balanceOf()`, a correct current Holder balance should be obtained from contract state.

Do not reconstruct it by simply summing:

> incoming transfers − outgoing transfers

because that ignores Reflection.

This is particularly important for:

- SolumTools,
- indexers,
- Metrics,
- territorial derivation,
- and AI answers.

> **Current balance is state.**
>
> **Transfer history alone is insufficient.**

---

# SolumTools and Reflection

SolumTools should eventually be able to expose relevant Reflection state without forcing ordinary users to understand `_rTotal`.

Potential signals may include:

- current effective balance,
- current total Supply,
- cumulative Burn,
- current transaction fees,
- and historical Reflection-related measurements where technically reconstructable.

The interface can simplify.

The underlying accounting should remain traceable.

→ **[Explore SolumTools](/world/solumtools/)**

---

# Metrics and Reflection

Reflection creates analytical questions that require careful definitions.

For example:

- how much Reflection has occurred historically,
- how Holder balances changed,
- how concentration changed,
- what share of balance growth came from Reflection,
- and how those changes interacted with Burn.

Not every metric may be directly derivable from one current-state variable.

Historical indexing may be necessary.

Metrics should say so.

> **Current state and historical attribution are different problems.**

---

# Artificial Intelligence rules

An AI reasoning about Burn and Reflection should preserve the following distinctions.

### Burn

Reduces current token-side Supply.

### Reflection

Does not increase token-side Supply.

### Burned SOLUM

Is permanently unavailable.

### Reflected balance growth

Does not mean new SOLUM was minted.

### Zero-address Burn event

Is evidence of Burn activity but should be interpreted together with contract behavior.

### Current Holder balance

Should be read from current state when accuracy matters.

### Permanent Nature

Is the canonical world interpretation of Burn, not Solidity terminology.

### Fractional territorial effects

Require explicit world rules rather than automatic inference from 18 token decimals.

---

# What AI must not say

AI should not say:

> **Reflection prints new tokens.**

Incorrect.

It should not say:

> **Burn simply sends tokens to a dead wallet.**

Incomplete for this contract.

It should not say:

> **Reflection transfers rewards individually to every Holder.**

Incorrect description of the accounting mechanism.

It should not say:

> **Every SELL always Burns exactly 4%.**

Only true while the SELL fee remains at its initial 10% and ordinary fees apply.

It should not say:

> **Burned land disappears from the map.**

That is not the canonical world interpretation.

---

# Contract and world side by side

| Contract | Zipvilization |
|:---------|:--------------|
| `_tTotal` | Current token-side territorial substrate reference |
| `_rTotal` | Reflection accounting domain |
| Reflection fee | Redistribution of effective SOLUM ownership |
| Real Burn | Permanent removal of SOLUM |
| Burned SOLUM | Permanent Nature |
| Lower current Supply | Less remaining SOLUM in token existence |
| Reflection balance change | Changed controlled SOLUM without minting |

The two columns are connected.

The first remains technically authoritative for contract behavior.

The second provides canonical world meaning.

---

# Burn & Reflection in one view

## Reflection

Initial effective rate:

- BUY: 0%
- SELL: 3%
- TRANSFER: 3%

Technical effect:

- `_rTotal` decreases,
- `_tTotal` does not increase,
- Reflection Rate changes,
- effective reflected balances redistribute,
- no mint occurs.

## Burn

Initial effective rate:

- BUY: 0%
- SELL: 4%
- TRANSFER: 2%

Technical effect:

- `_tTotal` decreases,
- `_rTotal` decreases proportionally,
- `totalSupply()` decreases,
- a zero-address Transfer event is emitted,
- Burned SOLUM becomes permanently unavailable.

## Zipvilization

> **Burn = Permanent Nature**

Reflection:

> **redistributes existing SOLUM without creating new world substrate.**

---

# Follow Burn & Reflection

### Return to Tokenomics

→ **[Tokenomics](/smart-contract/tokenomics/)**

### Understand Supply and reflected units

→ **[Supply & Units](/smart-contract/tokenomics/supply-and-units/)**

### Understand where Burn and Reflection originate

→ **[Fees](/smart-contract/tokenomics/fees/)**

### Understand accumulated Liquidity and Treasury fees

→ **[Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**

### Understand Burn as a Smart Contract mechanic

→ **[Burn](/smart-contract/burn/)**

### Understand Permanent Nature in the world

→ **[Solum](/world/solum/)**

### Understand canonical world-state derivation

→ **[SolumWorld](/world/solumworld/)**

### Inspect implementation

→ **[Repository](/repository/)**

---

# Destruction below, permanence above

At blockchain level, the distinction is precise.

Reflection removes reflected accounting weight from the global reflected Supply.

Burn removes actual token Supply.

Neither creates new SOLUM.

But only one permanently reduces `totalSupply()`.

That one is Burn.

Zipvilization takes that irreversible technical event and gives it a territorial consequence.

The SOLUM no longer exists as colonizable token substrate.

The corresponding land is not treated as missing.

It becomes something civilization can no longer own.

Permanent Nature.

That creates the inversion at the heart of Solum:

> **Reflection allows ownership to move without creating more world.**
>
> **Burn makes the token world smaller for civilization while making Nature larger forever.**

The mathematics stays visible underneath.

That is what makes the metaphor real.

---

→ **[Return to Tokenomics](/smart-contract/tokenomics/)**  
→ **[Return to Fees](/smart-contract/tokenomics/fees/)**  
→ **[Continue to Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**
