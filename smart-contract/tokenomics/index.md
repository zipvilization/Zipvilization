---
layout: default
title: Tokenomics
parent: Smart Contract
nav_order: 3
description: >
  Tokenomics documents the complete economic architecture of Solum: fixed
  supply, transaction fees, real Burn, Reflection, Liquidity, Treasury,
  anti-whale limits, launch protections, SwapBack, administrative permissions,
  and their canonical interpretation inside Zipvilization.
permalink: /smart-contract/tokenomics/
---

# Tokenomics

Solum is not defined by Supply alone.

Its economic behavior emerges from a system of interacting rules:

- finite Supply,
- BUY fees,
- SELL fees,
- TRANSFER fees,
- real Burn,
- Reflection,
- Liquidity,
- Treasury,
- MAX_TX,
- dynamic Max Wallet,
- launch protections,
- SwapBack,
- exemptions,
- timelocks,
- and bounded administrative authority.

Together, these mechanisms define the economic foundation of Solum.

This page is the entry point to that system.

> **The contract determines what happens.**
>
> **Zipvilization determines what it means.**

Those two layers are connected.

They must never be confused.

---

# Canonical Tokenomics Snapshot

The following values correspond to the initial configuration and explicit rules of the Solum Smart Contract documented by this Atlas.

| Parameter | Contract value |
|:----------|---------------:|
| Token | Solum |
| Symbol | SOLUM |
| Decimals | 18 |
| Initial Supply | 100,000,000,000,000 SOLUM |
| Post-deployment mint function | None |
| BUY fee | 1% |
| SELL fee | 10% |
| TRANSFER fee | 5% |
| MAX_TX | 10,000,000,000 SOLUM |
| Initial Max Wallet | 30,000,000,000 SOLUM |
| Max Wallet growth delay | 180 days |
| Max Wallet weekly growth | +10% compounded |
| Fee reduction timelock | 24 hours |
| Maximum fee changes | 5 per transaction type |
| Treasury change timelock | 48 hours |
| Launch whitelist window | 60 minutes |
| Launch BUY rules | 48 hours |
| BUY cooldown during launch rules | 60 minutes |
| Initial SwapBack threshold | 200,000,000 SOLUM |
| Initial SwapBack maximum | 1,000,000,000 SOLUM |
| Initial SwapBack cooldown | 60 seconds |
| Initial SwapBack slippage | 3% |

At world level:

> **1 SOLUM = 1 m²**

This equivalence belongs to the canonical interpretation of Solum inside Zipvilization.

---

# Fee architecture

Solum distinguishes three transaction types:

**BUY**

when Solum moves from the configured Pair.

**SELL**

when Solum moves to the configured Pair.

**TRANSFER**

when neither side is the configured Pair.

Their initial fee structures are different.

| Operation | Burn | Reflection | Liquidity | Treasury | Total |
|:----------|-----:|-----------:|----------:|---------:|------:|
| BUY | 0% | 0% | 0.5% | 0.5% | **1%** |
| SELL | 4% | 3% | 2% | 1% | **10%** |
| TRANSFER | 2% | 3% | 0% | 0% | **5%** |

These percentages describe the initial contract configuration.

The total BUY, SELL, and TRANSFER fees can be reduced under strict contract rules.

They cannot be increased through the fee-reduction mechanism.

→ **[Explore Fees](/smart-contract/tokenomics/fees/)**

---

# BUY

The initial BUY fee is:

> **1%**

The fee is divided equally between:

> **0.5% Liquidity**

and:

> **0.5% Treasury**

There is no Burn component.

There is no Reflection component.

For a non-exempt BUY of 1,000 SOLUM under the initial configuration:

| Result | SOLUM |
|:-------|------:|
| Gross BUY | 1,000 |
| Liquidity | 5 |
| Treasury | 5 |
| Recipient transfer amount | 990 |

The contract accumulates the Liquidity and Treasury components for later SwapBack processing.

---

# SELL

The initial SELL fee is:

> **10%**

Its internal distribution follows a fixed:

> **4 / 3 / 2 / 1**

split over the total SELL fee.

That produces:

> **4% Burn**

> **3% Reflection**

> **2% Liquidity**

> **1% Treasury**

For a non-exempt SELL of 1,000 SOLUM under the initial configuration:

| Result | SOLUM |
|:-------|------:|
| Gross SELL | 1,000 |
| Burn | 40 |
| Reflection | 30 |
| Liquidity | 20 |
| Treasury | 10 |
| Recipient transfer amount | 900 |

This means a SELL has four simultaneous economic consequences.

Part of the Solum disappears permanently from total Supply.

Part is redistributed through Reflection.

Part accumulates for Liquidity.

Part accumulates for Treasury.

---

# TRANSFER

The initial wallet-to-wallet TRANSFER fee is:

> **5%**

It is divided:

> **2% Burn**

and:

> **3% Reflection**

There is no Liquidity component.

There is no Treasury component.

For a non-exempt TRANSFER of 1,000 SOLUM:

| Result | SOLUM |
|:-------|------:|
| Gross TRANSFER | 1,000 |
| Burn | 20 |
| Reflection | 30 |
| Recipient transfer amount | 950 |

Moving Solum directly between ordinary wallets therefore changes more than ownership.

It also changes Supply and redistribution.

---

# Fees can decrease

BUY, SELL, and TRANSFER fees are independently configurable.

But the authority is deliberately constrained.

For each transaction type:

- the fee can only remain equal or decrease;
- it cannot exceed its initial value;
- a proposed reduction requires a 24-hour timelock;
- a maximum of 5 confirmed changes is permitted;
- reaching 0 freezes that fee;
- using all 5 changes also freezes that fee.

Initial ceilings are therefore:

| Fee | Maximum |
|:----|--------:|
| BUY | 1% |
| SELL | 10% |
| TRANSFER | 5% |

The contract does not provide the corresponding mechanism to raise them above their current value.

> **Fee evolution is one-directional.**

→ **[Explore Fees](/smart-contract/tokenomics/fees/)**

---

# Fixed fee proportions

The total fees can decrease.

Their internal allocation formulas remain defined by the contract.

BUY:

> **50% Liquidity / 50% Treasury**

SELL:

> **40% Burn / 30% Reflection / 20% Liquidity / 10% Treasury**

TRANSFER:

> **40% Burn / 60% Reflection**

Therefore, if a total fee is reduced, its absolute components decrease with it according to the corresponding split.

The economic proportions remain structurally connected to the total fee.

---

# Fixed Supply

Solum begins with:

> **100,000,000,000,000 SOLUM**

The full initial Supply is assigned to the deployer at construction.

The contract contains no post-deployment mint function.

Solum therefore begins as a finite asset.

But total Supply does not necessarily remain numerically constant.

Burn reduces it.

That distinction matters:

> **No inflationary minting.**
>
> **Deflation through real Burn.**

→ **[Explore Supply & Units](/smart-contract/tokenomics/supply-and-units/)**

---

# Real Burn

Burn is not implemented merely by transferring Solum to a dead wallet while leaving `totalSupply()` unchanged.

When Burn occurs, the contract reduces:

- the token-side total Supply,
- and the corresponding reflected Supply.

A Burn transfer to the zero address is also emitted.

Therefore:

> **Burn reduces totalSupply().**

This is real Supply contraction.

Inside Zipvilization:

> **Burned Solum = Permanent Nature**

Because:

> **1 SOLUM = 1 m²**

Burn has a direct territorial consequence.

If 40 SOLUM are Burned:

> **40 m² become permanently unavailable to future colonization.**

→ **[Explore Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**  
→ **[Explore Burn](/smart-contract/burn/)**

---

# Reflection

Reflection operates differently.

Reflection does not create new Solum.

It changes the relationship between reflected Supply and token Supply so that existing reflected balances represent a greater effective share.

SELL initially contributes:

> **3%**

to Reflection.

TRANSFER initially contributes:

> **3%**

to Reflection.

BUY contributes:

> **0%**

Therefore:

> **Reflection redistributes existing economic weight without minting additional Solum.**

Burn and Reflection both affect the dual-supply architecture.

But they do fundamentally different things.

→ **[Explore Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

---

# Liquidity

Liquidity receives part of:

- BUY fees,
- and SELL fees.

Initially:

> **BUY → 0.5% Liquidity**

> **SELL → 2% Liquidity**

These tokens accumulate inside the contract.

They are not immediately added to liquidity on every transaction.

They enter the Liquidity bucket and are later processed through SwapBack when the relevant conditions are satisfied.

→ **[Explore Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**

---

# Treasury

Treasury receives part of:

- BUY fees,
- and SELL fees.

Initially:

> **BUY → 0.5% Treasury**

> **SELL → 1% Treasury**

The corresponding tokens initially accumulate inside the contract.

SwapBack later converts the relevant portion into ETH and sends Treasury's ETH allocation to the configured Treasury address.

The Treasury address can change.

A change requires:

> **48 hours**

between proposal and confirmation.

→ **[Explore Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**

---

# SwapBack

Liquidity and Treasury fees need an execution mechanism.

That mechanism is SwapBack.

Initial configuration:

| Parameter | Initial value |
|:----------|--------------:|
| Threshold | 200,000,000 SOLUM |
| Maximum processed per SwapBack | 1,000,000,000 SOLUM |
| Cooldown | 60 seconds |
| Slippage | 3% |
| Enabled | Yes |

SwapBack is primarily triggered on SELL transactions when:

- trading is enabled,
- SwapBack is enabled,
- the contract is not already processing SwapBack,
- the configured cooldown has elapsed,
- and the contract token balance reaches the threshold.

The exact execution path is documented separately.

→ **[Explore SwapBack](/smart-contract/tokenomics/swapback/)**

---

# SwapBack parameters are mutable

Unlike MAX_TX, several SwapBack parameters can be changed by the owner.

The contract allows configuration of:

- threshold,
- maximum amount,
- cooldown,
- slippage.

The following explicit bounds exist:

> **Slippage: 0.5% to 8%**

> **Maximum amount must be greater than or equal to threshold**

> **Cooldown cannot exceed 15 minutes**

SwapBack can also be paused by the owner.

The contract does not impose a timelock on these configuration changes.

This authority belongs to the current trust model and must remain visible.

→ **[Explore Permissions](/smart-contract/tokenomics/permissions/)**

---

# Liquidity execution

During SwapBack, Liquidity tokens are divided.

Approximately half of the selected Liquidity allocation remains as SOLUM.

The other Liquidity half is swapped to ETH together with the Treasury allocation.

The resulting ETH is then divided proportionally.

The Liquidity portion is paired with the retained SOLUM through the configured V2-style router.

Treasury's ETH portion is sent to the Treasury address.

This creates an automated path from transaction fees to liquidity and Treasury funding.

---

# LP recipient

There is an important trust boundary.

When the contract adds liquidity, the resulting LP tokens are sent to:

> **the current owner address**

The contract itself does not:

- burn those LP tokens,
- lock them,
- send them automatically to Treasury,
- or enforce a liquidity locker.

Therefore:

> **Liquidity provision is automated.**
>
> **LP locking is not enforced by this contract.**

If LP tokens are later held by a locker, multisig, or another mechanism, that state must be documented separately and verified independently.

→ **[Explore Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**  
→ **[Explore Permissions](/smart-contract/tokenomics/permissions/)**

---

# MAX_TX

The maximum transaction amount is:

> **10,000,000,000 SOLUM**

or:

> **10 billion SOLUM**

Relative to the initial Supply:

> **0.01%**

MAX_TX is defined as a contract constant.

There is no setter for changing it in the documented contract.

The limit applies when neither sender nor receiver is Limit Exempt.

→ **[Explore Limits](/smart-contract/tokenomics/limits/)**

---

# Max Wallet

The initial Max Wallet is:

> **30,000,000,000 SOLUM**

or:

> **30 billion SOLUM**

Relative to the initial Supply:

> **0.03%**

For the first:

> **180 days after deployment**

the limit remains at its initial value.

After that delay, it grows by:

> **10% per complete week, compounded**

Conceptually:

> **Max Wallet = 30B × 1.10ⁿ**

where `n` is the number of complete weeks elapsed after the initial 180-day delay.

The actual contract performs the calculation using integer arithmetic.

→ **[Explore Limits](/smart-contract/tokenomics/limits/)**

---

# Max Wallet is time-dependent

The first progression is:

| Complete weeks after day 180 | Max Wallet |
|-----------------------------:|-----------:|
| 0 | 30.000B |
| 1 | 33.000B |
| 2 | 36.300B |
| 3 | 39.930B |
| 4 | 43.923B |

This is not a manually administered increase.

It is derived from deployment time and the contract formula.

If more than:

> **520 complete weeks**

have elapsed after the growth delay, the function returns the maximum `uint256` value.

At that point, Max Wallet is effectively non-restrictive for practical Solum balances.

---

# A Max Wallet implementation detail

The wallet check uses:

> **current recipient balance + gross transaction amount**

before fees are deducted from the transfer.

This means the limit test is conservative relative to the net amount that the recipient may ultimately receive.

The rule should therefore not be simplified to:

> **net received balance must remain below Max Wallet**

because that is not exactly what the contract executes.

→ **[Explore Limits](/smart-contract/tokenomics/limits/)**

---

# Launch

Trading does not begin automatically at deployment.

The owner activates it through the contract.

When trading is enabled for the first time:

> **launchTime is recorded.**

That timestamp begins the special BUY protection period.

→ **[Explore Launch](/smart-contract/tokenomics/launch/)**

---

# First 60 minutes

For the first:

> **60 minutes after trading begins**

BUY transactions are restricted to whitelisted recipient wallets.

During the same period, the BUY cooldown also applies.

Therefore Phase A is:

> **Whitelist BUY access + 60-minute per-wallet BUY cooldown**

This whitelist is a technical contract mechanism.

Any canonical relationship between that whitelist and Founding Colonists must be explicitly defined by Zipvilization rather than assumed from Solidity alone.

---

# From minute 60 to hour 48

After the whitelist window ends, BUY access becomes public.

But the cooldown remains active until the complete launch BUY-rules period ends.

Therefore Phase B is:

> **Public BUY access + 60-minute per-wallet BUY cooldown**

This continues until:

> **48 hours after launchTime**

---

# After 48 hours

The special launch BUY rules end.

The whitelist gate no longer restricts BUY access.

The launch BUY cooldown no longer applies.

Other independent contract rules may still apply, including:

- MAX_TX,
- Max Wallet,
- fees,
- exemptions,
- and ordinary ERC-20 balance and allowance requirements.

Launch protection and permanent contract mechanics must not be confused.

---

# Launch rules affect BUY transactions

The special 48-hour launch rules are applied to BUY transactions.

They do not impose the same launch restrictions on:

- SELL transactions,
- or ordinary wallet-to-wallet TRANSFER transactions.

MAX_TX, Max Wallet, fees, trading state, and exemptions are separate mechanisms.

→ **[Explore Launch](/smart-contract/tokenomics/launch/)**

---

# Pre-trading state

Before trading is enabled, ordinary public movement is restricted.

A transfer is allowed only when:

> **sender or receiver is Fee Exempt**

This creates an important distinction between:

**contract deployment**

and:

**public trading launch.**

The token can technically exist before ordinary public trading begins.

---

# Exemptions

The contract contains two separate exemption systems.

## Fee Exempt

A Fee Exempt address can participate in transfers without the ordinary transaction fee when either sender or receiver is exempt.

Initially Fee Exempt:

- deployer,
- contract itself,
- Treasury.

## Limit Exempt

A Limit Exempt address can bypass the relevant anti-whale limit checks where the exemption conditions apply.

Initially Limit Exempt:

- deployer,
- contract itself,
- Treasury,
- Router,
- Pair.

These lists can be modified by the owner.

→ **[Explore Permissions](/smart-contract/tokenomics/permissions/)**

---

# Exemption authority

The owner can independently set:

> **Fee Exempt: true / false**

and:

> **Limit Exempt: true / false**

for addresses.

These changes do not use the fee-reduction timelock or Treasury timelock.

They are direct administrative operations.

That authority is part of the contract's trust model.

It should not be hidden behind the broader Fair Access narrative.

---

# Treasury authority

Treasury can be replaced through a two-step process:

**Propose**

↓

**48-hour timelock**

↓

**Confirm**

When the new Treasury is confirmed, it automatically becomes:

- Fee Exempt,
- Limit Exempt.

The contract does not automatically remove those exemptions from the previous Treasury address.

That behavior belongs to the implementation and should be understood when evaluating the current exemption state.

---

# Owner authority

The owner has meaningful but bounded authority.

Among other operations defined by this contract, the owner can:

- enable trading,
- manage the launch whitelist,
- propose and confirm fee reductions,
- manage Fee Exempt addresses,
- manage Limit Exempt addresses,
- propose and confirm Treasury changes,
- pause or resume SwapBack,
- configure SwapBack parameters,
- and transfer ownership.

The owner cannot use the documented fee mechanism to increase transaction fees.

The owner cannot change the constant MAX_TX through a setter in this contract.

The contract exposes no post-deployment mint function.

→ **[Explore Permissions](/smart-contract/tokenomics/permissions/)**

---

# Ownership can move

Ownership itself is transferable.

The current owner can transfer ownership to a non-zero address.

Therefore:

> **deployer**

and:

> **current owner**

must not be assumed to remain the same forever.

Administrative analysis should use current blockchain state once the contract is deployed.

---

# No renounceOwnership function

The documented contract includes ownership transfer.

It does not include a `renounceOwnership()` function.

Therefore claims such as:

> **ownership can be renounced**

should not be made for this implementation unless another canonical mechanism exists outside this contract.

Transparency includes documenting absent capabilities as well as present ones.

---

# Contract classification matters

A transaction is not classified by user intention.

It is classified by addresses.

The contract determines:

> **BUY if `from == pair`**

> **SELL if `to == pair`**

> **TRANSFER otherwise**

This is the authoritative classification for fee behavior.

An interface should not infer fee type merely from what a user calls the transaction.

---

# Fee exemptions override ordinary fee behavior

The BUY, SELL, and TRANSFER fee tables describe ordinary non-exempt transactions.

If either sender or receiver is Fee Exempt, ordinary fees are not taken.

Therefore:

> **transaction type determines the fee schedule**

but:

> **exemption state determines whether that fee schedule is applied.**

Both pieces of state matter.

---

# Tokenomics is stateful

Not every value on this page remains constant forever.

Some values are fixed.

Some decrease.

Some grow with time.

Some can be configured administratively.

Some depend on current blockchain state.

That distinction is essential.

| Mechanism | Behavior |
|:----------|:---------|
| Initial Supply | Fixed at deployment |
| Post-deployment minting | No mint function |
| totalSupply() | Can decrease through Burn |
| MAX_TX | Contract constant |
| Max Wallet | Time-dependent |
| BUY fee | Decreasing-only |
| SELL fee | Decreasing-only |
| TRANSFER fee | Decreasing-only |
| Fee split formulas | Defined by contract |
| Treasury | Administratively changeable with 48h timelock |
| Fee exemptions | Administratively configurable |
| Limit exemptions | Administratively configurable |
| SwapBack enabled state | Administratively configurable |
| SwapBack parameters | Administratively configurable within explicit bounds |
| Ownership | Transferable |
| Launch time | Set when trading is first enabled |

A static description is therefore not enough to determine every future transaction.

Current state matters.

---

# From blockchain economics to Zipvilization

The contract can be understood without Zipvilization.

But Zipvilization gives its state another layer of meaning.

| Blockchain | Zipvilization |
|:-----------|:--------------|
| SOLUM | Territorial substrate |
| 1 SOLUM | 1 m² |
| Holder | Colonist interpretation |
| Balance | Controlled territorial substrate |
| Pool-held Solum | Dormant Land |
| Burned Solum | Permanent Nature |
| Max Wallet | Constraint on early concentration |
| Launch whitelist | Bounded preferential access mechanism where canonically mapped |
| Reflection | Redistribution of existing Solum |
| Liquidity | Market infrastructure |
| Treasury | Project economic resource |
| Tax | Economic state transition |

The mapping must remain explicit.

The narrative cannot override the contract.

---

# Dormant Land

Pool-held Solum represents:

> **Dormant Land**

The Solum already exists.

The world already exists.

But that part of the finite substrate has not yet entered active colonization.

As Solum leaves the relevant Pool state:

> **Dormant Land can recede.**

→ **[Explore Pool](/smart-contract/pool/)**

---

# Permanent Nature

Burned Solum represents:

> **Permanent Nature**

Because Burn reduces actual Supply, the corresponding territorial substrate becomes permanently unavailable to future colonization.

Therefore the world has two fundamentally different non-colonized conditions:

> **Dormant Land — still possible**

and:

> **Permanent Nature — permanently unavailable**

The distinction is economic, technical, territorial, and visual.

---

# Transaction activity changes the world

Under the initial fee configuration:

a SELL can create Permanent Nature.

A TRANSFER can create Permanent Nature.

A BUY does not directly Burn Solum.

Therefore ordinary economic activity can modify the amount of future colonizable substrate.

That relationship is not decorative narrative.

It derives from the actual Burn mechanics plus the canonical equivalence:

> **1 SOLUM = 1 m²**

---

# Reflection changes ownership without inflation

Reflection creates another consequence.

Existing reflected Holders can receive an increasing effective share through the Reflection mechanism without new Solum being minted.

Inside the world, that means territorial balances can evolve even without a direct incoming ordinary transfer.

This is a real contract consequence.

Any territorial interpretation built above Solum must account for current balances rather than assuming balances change only through visible wallet-to-wallet transfers.

---

# Fair Access protects the beginning

MAX_TX, Max Wallet, launch restrictions, whitelist access, and cooldown mechanics constrain the earliest phase of distribution.

But those protections do not permanently prescribe equal outcomes.

Max Wallet grows.

Launch restrictions expire.

Markets continue.

Ownership can redistribute.

The architecture protects the beginning more strongly than the mature world.

> **The contract constrains Genesis.**
>
> **It does not attempt to script civilization forever.**

→ **[Explore Fair Access](/smart-contract/fair-access/)**

---

# A finite world with changing proportions

The initial world begins from a finite substrate:

> **100 trillion SOLUM**

Over time, that substrate can separate conceptually into different conditions.

Some may remain Dormant Land.

Some may be controlled by Colonists.

Some may become Permanent Nature.

And Burn can reduce the amount of Solum still available to future economic and territorial participation.

Therefore one of the deepest Tokenomics questions is not simply:

> **What is the token price?**

It is:

> **What is happening to the finite world?**

---

# What Tokenomics does not determine

Tokenomics does not determine everything.

It does not directly determine:

- territorial maturity,
- Zip development,
- biological time,
- civilization,
- political power,
- alliances,
- war,
- future governance,
- or historical importance.

Those belong to other layers.

Tokenomics provides the economic substrate upon which those systems may operate.

> **Economics creates conditions.**
>
> **It does not write the entire civilization.**

---

# Documentation hierarchy

Tokenomics follows a strict documentation hierarchy.

## Tokenomics Index

Contains the essential economic architecture and all critical headline values.

## Tokenomics subpages

Contain the detailed explanation, formulas, edge cases, examples, permissions, and mechanics.

## Smart Contract pages

Explain the major contract concepts and their relationship with Zipvilization.

## Repository

Contains the technical implementation.

The rule is:

> **Index for orientation.**
>
> **Subpages for understanding.**
>
> **Repository for verification.**

---

# Explore Tokenomics

### Supply, decimals, units, and finite accounting

→ **[Supply & Units](/smart-contract/tokenomics/supply-and-units/)**

### BUY, SELL, and TRANSFER mathematics

→ **[Fees](/smart-contract/tokenomics/fees/)**

### Real Burn and dual-supply Reflection

→ **[Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

### Liquidity allocation, Treasury, and LP ownership

→ **[Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**

### MAX_TX and dynamic Max Wallet

→ **[Limits](/smart-contract/tokenomics/limits/)**

### Whitelist, cooldown, and the first 48 hours

→ **[Launch](/smart-contract/tokenomics/launch/)**

### Automated fee processing

→ **[SwapBack](/smart-contract/tokenomics/swapback/)**

### Owner authority, exemptions, timelocks, and mutable parameters

→ **[Permissions](/smart-contract/tokenomics/permissions/)**

### How contract economics becomes world economics

→ **[Economic Model](/smart-contract/tokenomics/economic-model/)**

---

# Related Smart Contract documentation

### The asset

→ **[Solum Token](/smart-contract/solum-token/)**

### The finite substrate

→ **[Supply](/smart-contract/supply/)**

### Dormant Solum

→ **[Pool](/smart-contract/pool/)**

### Permanent removal

→ **[Burn](/smart-contract/burn/)**

### Transaction taxation

→ **[Taxes](/smart-contract/taxes/)**

### Anti-concentration architecture

→ **[Fair Access](/smart-contract/fair-access/)**

### Trust boundaries

→ **[Security](/smart-contract/security/)**

### Foundational invariants

→ **[Canonical Rules](/smart-contract/canonical-rules/)**

---

# Transparency before interpretation

Solum is intended to become the economic substrate of a world.

That makes precision more important, not less.

A participant should be able to know:

how much Solum exists,

what happens when they buy,

what happens when they sell,

what happens when they transfer,

what gets Burned,

what gets reflected,

what reaches Liquidity,

what reaches Treasury,

what limits apply,

when those limits change,

what happens during Launch,

what authority the owner retains,

what can decrease,

what can change,

what cannot be increased,

and what the contract does not guarantee.

An Artificial Intelligence should be able to answer the same questions from explicit structure rather than inference.

Only after those facts are clear should Zipvilization translate them into the world.

Then the relationship becomes powerful precisely because it is verifiable.

> **Burn is a contract operation.**
>
> **Permanent Nature is its canonical world consequence.**

> **Pool is a contract state.**
>
> **Dormant Land is its canonical world meaning.**

> **A balance is blockchain state.**
>
> **Territorial capacity is derived from it.**

The imagination belongs above the mechanism.

The mechanism remains visible underneath.

That is the economic foundation of Solum.

---

→ **[Return to Smart Contract](/smart-contract/)**  
→ **[Explore Supply & Units](/smart-contract/tokenomics/supply-and-units/)**  
→ **[Open the Repository](/repository/)**
