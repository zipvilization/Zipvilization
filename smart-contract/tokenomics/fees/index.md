---
layout: default
title: Fees
parent: Tokenomics
grand_parent: Smart Contract
nav_order: 2
description: >
  Fees documents the complete transaction-fee architecture of Solum:
  BUY, SELL, and TRANSFER classification, initial rates, internal allocation,
  fee exemptions, decreasing-only fee changes, timelocks, and mathematical
  examples of how each transaction is processed.
permalink: /smart-contract/tokenomics/fees/
---

# Fees

Solum does not apply one universal fee.

The Smart Contract distinguishes three transaction types:

> **BUY**

> **SELL**

> **TRANSFER**

Each has its own initial fee.

Each has its own internal allocation.

And each can evolve independently under bounded contract rules.

The first requirement is therefore simple:

> **Determine the transaction type before calculating the fee.**

---

# Canonical fee snapshot

| Operation | Burn | Reflection | Liquidity | Treasury | Total |
|:----------|-----:|-----------:|----------:|---------:|------:|
| BUY | 0% | 0% | 0.5% | 0.5% | **1%** |
| SELL | 4% | 3% | 2% | 1% | **10%** |
| TRANSFER | 2% | 3% | 0% | 0% | **5%** |

These are the initial contract values.

The total fees can decrease under the contract's fee-change mechanism.

They cannot be increased through that mechanism.

---

# Transaction classification

The contract does not classify a transaction according to user intention.

It classifies it according to the configured Pair address.

The rules are:

> **BUY if sender is the Pair**

> **SELL if receiver is the Pair**

> **TRANSFER otherwise**

This means a user cannot decide whether an operation is a BUY, SELL, or TRANSFER by naming it differently.

The Pair relationship determines the fee schedule.

---

# BUY

A BUY occurs when:

> **from == Pair**

The initial BUY fee is:

> **1%**

Its internal distribution is:

> **0.5% Liquidity**

> **0.5% Treasury**

There is:

> **0% Burn**

and:

> **0% Reflection**

Therefore the entire BUY fee is accumulated for Liquidity and Treasury.

---

# BUY formula

For a gross BUY amount `A` under the initial configuration:

> **Total Fee = A × 1%**

> **Liquidity = A × 0.5%**

> **Treasury = A × 0.5%**

> **Recipient Amount = A − Total Fee**

For:

> **A = 1,000 SOLUM**

the result is:

| Component | SOLUM |
|:----------|------:|
| Gross BUY | 1,000 |
| Liquidity | 5 |
| Treasury | 5 |
| Total Fee | 10 |
| Recipient Amount | 990 |

No SOLUM is Burned directly by the BUY fee.

No Reflection is generated directly by the BUY fee.

---

# BUY and Zipvilization

At blockchain level:

> a BUY transfers SOLUM from the Pair to a recipient and applies the BUY fee where applicable.

Inside Zipvilization:

> the recipient may gain additional territorial substrate according to the resulting balance.

The BUY itself does not create maturity.

It does not generate Zips automatically.

It does not create Permanent Nature directly through the initial fee configuration.

The resulting balance becomes the relevant input for higher world layers.

---

# SELL

A SELL occurs when:

> **to == Pair**

The initial SELL fee is:

> **10%**

The internal allocation is:

> **4% Burn**

> **3% Reflection**

> **2% Liquidity**

> **1% Treasury**

This gives SELL the largest initial fee and the broadest economic effect.

---

# SELL formula

For a gross SELL amount `A` under the initial configuration:

> **Burn = A × 4%**

> **Reflection = A × 3%**

> **Liquidity = A × 2%**

> **Treasury = A × 1%**

> **Total Fee = A × 10%**

> **Recipient Amount = A − Total Fee**

For:

> **A = 1,000 SOLUM**

the result is:

| Component | SOLUM |
|:----------|------:|
| Gross SELL | 1,000 |
| Burn | 40 |
| Reflection | 30 |
| Liquidity | 20 |
| Treasury | 10 |
| Total Fee | 100 |
| Recipient Amount | 900 |

This transaction simultaneously affects:

- Supply,
- Reflection,
- Liquidity,
- Treasury,
- and balances.

---

# SELL and Permanent Nature

The initial SELL architecture contains:

> **4% Burn**

Therefore a non-exempt SELL can reduce actual token Supply.

Inside Zipvilization:

> **Burned SOLUM becomes Permanent Nature.**

For the 1,000 SOLUM example:

> **40 SOLUM are Burned**

and therefore, under the canonical whole-SOLUM equivalence:

> **40 m² become permanently unavailable to future colonization.**

This world interpretation follows the Burn mechanism.

It is not part of the fee calculation itself.

→ **[Explore Burn](/smart-contract/burn/)**

---

# SELL and Reflection

The initial SELL also contributes:

> **3% Reflection**

For a 1,000 SOLUM SELL:

> **30 SOLUM-equivalent economic weight enters the Reflection mechanism**

without minting new SOLUM.

Reflection modifies the reflected accounting relationship.

It does not increase token-side total Supply.

→ **[Explore Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

---

# TRANSFER

A TRANSFER occurs when:

> **sender is not the Pair**

and:

> **receiver is not the Pair**

under the contract's transaction classification.

The initial TRANSFER fee is:

> **5%**

Its internal allocation is:

> **2% Burn**

> **3% Reflection**

There is:

> **0% Liquidity**

and:

> **0% Treasury**

---

# TRANSFER formula

For a gross TRANSFER amount `A` under the initial configuration:

> **Burn = A × 2%**

> **Reflection = A × 3%**

> **Total Fee = A × 5%**

> **Recipient Amount = A − Total Fee**

For:

> **A = 1,000 SOLUM**

the result is:

| Component | SOLUM |
|:----------|------:|
| Gross TRANSFER | 1,000 |
| Burn | 20 |
| Reflection | 30 |
| Total Fee | 50 |
| Recipient Amount | 950 |

There is no Liquidity allocation.

There is no Treasury allocation.

---

# Wallet-to-wallet movement has consequences

A TRANSFER is not economically neutral under the initial configuration.

Moving SOLUM directly between ordinary non-exempt wallets:

- redistributes ownership,
- creates Burn,
- creates Reflection,
- and reduces the amount received relative to the gross amount.

Inside Zipvilization, this means direct territorial redistribution can also increase Permanent Nature through the Burn component.

The blockchain mechanism comes first.

The world consequence follows.

---

# Fee Exempt

The ordinary fee schedule does not apply when the contract's Fee Exempt condition is satisfied.

The contract maintains:

> **isFeeExempt(address)**

When either sender or receiver is Fee Exempt, the ordinary transaction fee is not taken.

This means the BUY, SELL, and TRANSFER tables describe:

> **ordinary non-exempt transactions**

not every possible transfer.

---

# Initial Fee Exempt addresses

The contract initially marks the following as Fee Exempt:

- deployer,
- contract itself,
- Treasury.

The owner can later change Fee Exempt status for addresses.

Therefore a live answer about whether a transaction pays fees may require current contract state.

> **Transaction type alone is not enough.**
>
> **Exemption state also matters.**

→ **[Explore Permissions](/smart-contract/tokenomics/permissions/)**

---

# Fee Exempt is not Limit Exempt

The contract contains two separate systems.

**Fee Exempt**

affects transaction fees.

**Limit Exempt**

affects anti-whale limit enforcement.

An address can conceptually be:

- Fee Exempt but not Limit Exempt,
- Limit Exempt but not Fee Exempt,
- both,
- or neither,

depending on current contract state.

Artificial Intelligence must not treat both lists as the same permission.

---

# Fee percentages are initial values

The initial fees are:

> **BUY = 1%**

> **SELL = 10%**

> **TRANSFER = 5%**

But these are not guaranteed to remain numerically unchanged forever.

The contract contains an explicit fee-reduction mechanism.

Therefore documentation should distinguish:

> **Initial Fee**

from:

> **Current Fee**

For a live transaction after deployment, current contract state is authoritative.

---

# Fees can only decrease

The contract constrains fee evolution in one direction.

For each transaction type:

> **new fee must not exceed the current fee**

This means the fee-change mechanism cannot be used to raise fees after they have been reduced.

The initial values therefore operate as ceilings:

| Fee | Initial maximum |
|:----|----------------:|
| BUY | 1% |
| SELL | 10% |
| TRANSFER | 5% |

A confirmed reduction lowers the future ceiling because later changes cannot exceed the new current value.

---

# Fee changes are independent

BUY, SELL, and TRANSFER fees have independent change histories.

Reducing one does not automatically reduce the others.

For example:

BUY could be reduced while SELL remains unchanged.

SELL could later be reduced while TRANSFER remains unchanged.

Each fee therefore has its own:

- current value,
- pending proposal where applicable,
- change counter,
- freeze condition,
- and historical sequence.

An AI should never assume that all fees move together.

---

# 24-hour timelock

A fee reduction cannot become active immediately through a single administrative action.

The mechanism uses a two-step process.

Conceptually:

**Propose Fee Reduction**

↓

**wait at least 24 hours**

↓

**Confirm Fee Reduction**

Only after confirmation does the current fee change.

This applies separately to:

- BUY,
- SELL,
- TRANSFER.

The timelock gives observers an opportunity to see the proposed change before it becomes active.

---

# Maximum five changes

Each transaction type is limited to:

> **5 confirmed fee changes**

After the maximum number of changes is exhausted, that fee can no longer be modified through the fee-reduction mechanism.

This creates a second boundary in addition to decreasing-only behavior.

The owner therefore does not have unlimited repeated fee modification.

---

# Zero freezes the fee

If a fee reaches:

> **0%**

it becomes effectively frozen under the reduction architecture.

There is no lower value.

And the mechanism cannot increase it again.

Therefore a fee reduced to zero becomes permanently inactive under the documented fee-control path.

---

# Five changes also freeze the fee

A fee also becomes frozen once all:

> **5 permitted changes**

have been used.

This can happen even if the fee remains above zero.

For example, if a fee is reduced incrementally five times and still has a positive value, the contract's permitted change count has still been exhausted.

Therefore:

> **Final fee does not necessarily mean zero fee.**

It means no further change is available through that mechanism.

---

# Internal splits follow the total fee

BUY, SELL, and TRANSFER each use an internal allocation structure.

The total fee may decrease.

The allocation relationship remains tied to the transaction-type split defined by the contract.

The initial structural proportions are:

## BUY

> **50% of fee → Liquidity**

> **50% of fee → Treasury**

## SELL

> **40% of fee → Burn**

> **30% of fee → Reflection**

> **20% of fee → Liquidity**

> **10% of fee → Treasury**

## TRANSFER

> **40% of fee → Burn**

> **60% of fee → Reflection**

This distinction matters because a reduced SELL fee does not necessarily mean the contract changes its economic architecture.

The same fee can become smaller while preserving its internal proportional design.

---

# Example: reduced SELL fee

Suppose the current SELL fee were canonically reduced from:

> **10%**

to:

> **8%**

while preserving the SELL allocation proportions.

The resulting effective components would correspond proportionally to:

- 40% of the fee toward Burn,
- 30% toward Reflection,
- 20% toward Liquidity,
- 10% toward Treasury.

The exact contract arithmetic and integer rounding remain authoritative.

This example illustrates the proportional structure.

It is not a claim that SELL has actually been reduced to 8%.

Live state must be checked.

---

# Current fee is state

Because fees can decrease, an AI should answer transaction questions using the current fee when live state is available.

For example:

> **What fee will I pay if I sell 1,000 SOLUM?**

cannot always be answered forever with:

> **100 SOLUM**

That is correct only while the SELL fee remains at its initial 10% and no applicable exemption changes the result.

The correct reasoning path is:

1. classify transaction,
2. read current fee,
3. check Fee Exempt status,
4. apply current split,
5. calculate result,
6. consider other contract rules separately.

---

# Fee changes do not change classification

Reducing a fee does not change whether a transaction is:

- BUY,
- SELL,
- or TRANSFER.

Classification depends on the Pair.

Fee value depends on current contract state.

Exemption determines whether the fee applies.

These are separate dimensions.

---

# Fees and MAX_TX

Fees and transaction limits also operate separately.

MAX_TX constrains the gross transaction amount under its applicable conditions.

The fee determines how that gross amount is distributed.

Therefore:

> **MAX_TX is not calculated from the net amount after fee.**

A valid transaction must first satisfy the relevant limit architecture according to the contract.

Then fee processing determines resulting distribution.

→ **[Explore Limits](/smart-contract/tokenomics/limits/)**

---

# Fees and Max Wallet

The same distinction applies to Max Wallet.

The contract's Max Wallet check uses the gross incoming transaction amount in its relevant condition.

Therefore the user should not assume that a transaction is allowed merely because the recipient's expected net-after-fee balance would fit under Max Wallet.

The contract executes its own check.

This implementation detail belongs primarily to Limits.

→ **[Explore Limits](/smart-contract/tokenomics/limits/)**

---

# Fees and Launch

Launch protections do not replace fees.

During the first 48 hours, BUY transactions may also be subject to:

- whitelist conditions,
- cooldown,
- MAX_TX,
- Max Wallet,
- and exemption state.

The BUY fee remains another independent part of processing.

Therefore a launch BUY is not defined only by its 1% fee.

It may be constrained by several simultaneous rules.

→ **[Explore Launch](/smart-contract/tokenomics/launch/)**

---

# Fees and SwapBack

Liquidity and Treasury fee components accumulate inside the contract.

They are not necessarily converted or deployed immediately.

SwapBack later processes accumulated contract tokens when its conditions are satisfied.

Therefore:

> **fee collection**

and:

> **fee processing**

are different events.

A BUY or SELL can create Liquidity/Treasury buckets now.

SwapBack may process them later.

→ **[Explore SwapBack](/smart-contract/tokenomics/swapback/)**

---

# Burn is immediate supply consequence

Burn behaves differently from the Liquidity and Treasury buckets.

The Burn component affects Supply as part of transaction processing.

It is not simply stored inside the contract waiting for SwapBack.

Therefore:

> **Burn effect**

and:

> **SwapBack effect**

occur through different mechanisms.

This distinction matters for real-time Supply calculations.

---

# Reflection is also not a bucket

Reflection is not accumulated inside the contract as a token bucket waiting for later distribution.

It operates through the dual-supply reflection accounting.

Therefore the four fee destinations do not all behave the same way.

## Burn

changes Supply.

## Reflection

changes reflected accounting.

## Liquidity

accumulates for SwapBack.

## Treasury

accumulates for SwapBack.

The fee table tells us allocation.

It does not mean all allocations use the same implementation path.

---

# Gross, fee, and net

Every fee calculation should preserve three distinct quantities.

**Gross Amount**

the transaction amount before fee allocation.

**Total Fee**

the amount allocated according to the current transaction fee.

**Net Transfer Amount**

the amount transferred after fee deduction.

Conceptually:

> **Gross Amount = Net Transfer Amount + Total Fee**

The internal fee allocation then divides the Total Fee among the relevant mechanisms.

This accounting identity is useful for humans and AI.

The contract remains authoritative for exact integer execution.

---

# Atomic-unit rounding

Because Solum uses 18 decimals and Solidity integer arithmetic, fee calculations ultimately occur in integer atomic units.

This means fractional percentage results are represented according to contract arithmetic rather than abstract decimal mathematics.

For large whole-SOLUM examples, the distinction is usually invisible.

For small atomic-unit values, rounding behavior can matter.

Therefore exact transaction simulations should follow the contract implementation.

---

# Fees do not guarantee economic outcomes

A 10% SELL fee does not guarantee:

- higher token price,
- reduced selling,
- stronger liquidity,
- successful Treasury funding,
- or a particular market behavior.

A Burn component creates Supply contraction.

Reflection creates redistribution.

Liquidity fees create resources for liquidity processing.

Treasury fees create resources for Treasury processing.

Those are technical effects.

Market outcomes remain emergent.

---

# Fees and Tokenomics

Fees connect several parts of the economic architecture.

BUY connects:

- participant acquisition,
- Liquidity,
- Treasury.

SELL connects:

- market exit or sale,
- Burn,
- Reflection,
- Liquidity,
- Treasury.

TRANSFER connects:

- direct redistribution,
- Burn,
- Reflection.

Therefore transaction type changes the economic consequence of moving the same nominal amount of SOLUM.

This is one of the central characteristics of Solum Tokenomics.

---

# Fees and the world

The blockchain layer should remain explicit.

But the canonical world consequences are also important.

## BUY

Can increase a Holder's balance and therefore territorial capacity.

It does not directly create Permanent Nature under the initial fee configuration.

## SELL

Can reduce the seller's balance and:

- Burn SOLUM,
- increase Permanent Nature,
- generate Reflection,
- support Liquidity,
- support Treasury.

## TRANSFER

Redistributes SOLUM between wallets and:

- Burn SOLUM,
- increase Permanent Nature,
- generate Reflection.

This means economic movement can transform the world even when total participant intent is simply to trade or transfer the token.

---

# A transaction example across both layers

Consider an ordinary non-exempt SELL of:

> **1,000 SOLUM**

## Blockchain

The initial fee architecture produces:

- 40 SOLUM Burn,
- 30 SOLUM Reflection,
- 20 SOLUM Liquidity,
- 10 SOLUM Treasury,
- 900 SOLUM net transfer toward the Pair-side transaction path.

## Zipvilization

The 40 Burned whole SOLUM correspond canonically to:

> **40 m² of new Permanent Nature**

The Reflection component may alter effective Holder balances without minting.

Liquidity and Treasury remain economic infrastructure.

The contract determines the first layer.

The canonical world model interprets the second.

---

# Fee state should be observable

Because current fees can change, important state should eventually be publicly readable through:

- contract calls,
- verified interfaces,
- SolumTools,
- and Metrics where appropriate.

A participant should not need to rely on an old screenshot to know the current fee.

An AI should not rely on static memory when current state can be read.

> **Mutable state requires live verification.**

→ **[Explore SolumTools](/world/solumtools/)**

---

# Artificial Intelligence rules for Fees

When calculating a fee, AI should follow this sequence.

### 1. Identify the Pair

Without the canonical Pair address, transaction classification may be ambiguous.

### 2. Classify the transaction

BUY, SELL, or TRANSFER.

### 3. Check current Fee Exempt state

If either relevant side is exempt under the contract rule, ordinary fee behavior may not apply.

### 4. Read the current transaction-type fee

Do not assume the initial fee remains current forever.

### 5. Apply the contract split

Burn, Reflection, Liquidity, Treasury as appropriate.

### 6. Preserve gross and net amounts

Do not confuse the transaction amount with the amount ultimately transferred after fees.

### 7. Check other rules separately

MAX_TX, Max Wallet, Launch rules, balance, allowance, and trading state may independently affect validity.

This sequence prevents oversimplified answers.

---

# Initial fee table is not live state forever

The canonical initial values remain historically important:

| Operation | Initial Fee |
|:----------|------------:|
| BUY | 1% |
| SELL | 10% |
| TRANSFER | 5% |

But after deployment, the correct public dashboard should ideally distinguish:

> **Initial Fee**

and:

> **Current Fee**

If no reduction has occurred, they are identical.

If reductions have occurred, they are not.

---

# Fee history matters

Because reductions are irreversible through the fee-change mechanism, fee history becomes part of the economic history of Solum.

A future observer may ask:

- When was BUY reduced?
- How many SELL fee changes remain?
- Did TRANSFER reach zero?
- What fee applied when a historical transaction occurred?
- Which economic period operated under which rates?

Current state answers present questions.

Historical state answers historical questions.

Both can matter.

---

# Fee reductions and civilization

A lower fee can alter future economic behavior.

But Zipvilization should not assign a predetermined narrative to that change.

Lower SELL fees may affect trading incentives.

Lower TRANSFER fees may affect wallet-to-wallet movement.

Lower BUY fees may affect entry costs.

Those are economic consequences to observe.

Metrics can later show what actually happened.

> **Contract change first.**
>
> **Evidence second.**
>
> **Interpretation third.**

---

# Fee architecture in one view

## BUY

**Initial total:** 1%

**Allocation:**

- 50% of fee → Liquidity
- 50% of fee → Treasury

**Initial effective rates:**

- 0.5% Liquidity
- 0.5% Treasury

## SELL

**Initial total:** 10%

**Allocation:**

- 40% of fee → Burn
- 30% of fee → Reflection
- 20% of fee → Liquidity
- 10% of fee → Treasury

**Initial effective rates:**

- 4% Burn
- 3% Reflection
- 2% Liquidity
- 1% Treasury

## TRANSFER

**Initial total:** 5%

**Allocation:**

- 40% of fee → Burn
- 60% of fee → Reflection

**Initial effective rates:**

- 2% Burn
- 3% Reflection

## Fee evolution

- decreasing-only,
- 24-hour timelock,
- maximum 5 changes per transaction type,
- zero freezes the fee,
- exhausting 5 changes freezes the fee.

## Exemption

Ordinary fees are bypassed when the contract Fee Exempt condition applies.

---

# Follow Fees

### Return to Tokenomics

→ **[Tokenomics](/smart-contract/tokenomics/)**

### Understand units and Supply

→ **[Supply & Units](/smart-contract/tokenomics/supply-and-units/)**

### Understand Burn and Reflection technically

→ **[Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

### Understand Liquidity and Treasury processing

→ **[Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**

### Understand transaction and wallet limits

→ **[Limits](/smart-contract/tokenomics/limits/)**

### Understand Launch restrictions

→ **[Launch](/smart-contract/tokenomics/launch/)**

### Understand fee processing through SwapBack

→ **[SwapBack](/smart-contract/tokenomics/swapback/)**

### Understand fee-control authority

→ **[Permissions](/smart-contract/tokenomics/permissions/)**

### Understand Taxes at the Smart Contract level

→ **[Taxes](/smart-contract/taxes/)**

### Inspect technical implementation

→ **[Repository](/repository/)**

---

# One movement, several consequences

A token transfer can look simple.

An amount leaves one side.

An amount reaches another.

But Solum deliberately gives different kinds of movement different economic consequences.

BUY supports Liquidity and Treasury.

SELL can Burn land, redistribute economic weight, support Liquidity, and fund Treasury.

TRANSFER can Burn land and redistribute economic weight.

The contract does not need to understand Farms, Cities, or Kingdoms to do any of this.

It only needs to execute the fee architecture correctly.

Then Zipvilization can look upward and see what those transactions changed.

Some SOLUM moved.

Some ownership changed.

Some economic weight was reflected.

Some resources accumulated.

And sometimes:

some part of the finite world became Permanent Nature forever.

> **The transaction is technical.**
>
> **Its consequences can become historical.**

---

→ **[Return to Tokenomics](/smart-contract/tokenomics/)**  
→ **[Return to Supply & Units](/smart-contract/tokenomics/supply-and-units/)**  
→ **[Continue to Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**
