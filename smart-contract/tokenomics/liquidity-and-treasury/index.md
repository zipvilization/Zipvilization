---
layout: default
title: Liquidity & Treasury
parent: Tokenomics
grand_parent: Smart Contract
nav_order: 4
description: >
  Liquidity & Treasury documents how Solum transaction fees are accumulated,
  separated into internal buckets, processed through SwapBack, converted into
  ETH, added to liquidity, and transferred to Treasury, including the contract's
  LP-token ownership and Treasury authority model.
permalink: /smart-contract/tokenomics/liquidity-and-treasury/
---

# Liquidity & Treasury

Not every fee is processed immediately.

Solum separates fee collection from fee execution.

BUY and SELL transactions can create:

> **Liquidity allocation**

and:

> **Treasury allocation**

Those SOLUM amounts accumulate inside the Smart Contract.

Later, SwapBack processes them.

This creates a two-stage architecture:

**Fee collection**

↓

**Accumulation**

↓

**SwapBack**

↓

**Liquidity and Treasury execution**

Understanding that separation is essential.

---

# Canonical snapshot

Under the initial fee configuration:

| Operation | Liquidity | Treasury |
|:----------|----------:|---------:|
| BUY | 0.5% | 0.5% |
| SELL | 2% | 1% |
| TRANSFER | 0% | 0% |

Liquidity and Treasury therefore receive SOLUM from:

- BUY,
- SELL.

They do not receive SOLUM from the ordinary TRANSFER fee.

---

# Internal allocation proportions

The total fee may later decrease.

The internal structural proportions remain defined by transaction type.

## BUY

The BUY fee is split:

> **50% Liquidity**

> **50% Treasury**

At the initial 1% BUY fee, this produces:

- 0.5% Liquidity,
- 0.5% Treasury.

## SELL

The SELL fee is split:

> **20% of the total SELL fee → Liquidity**

> **10% of the total SELL fee → Treasury**

At the initial 10% SELL fee, this produces:

- 2% Liquidity,
- 1% Treasury.

---

# TRANSFER does not fund these buckets

The initial TRANSFER fee is divided entirely between:

- Burn,
- Reflection.

Therefore ordinary wallet-to-wallet TRANSFER does not directly create:

- Liquidity allocation,
- Treasury allocation.

This distinction matters when analyzing how different transaction types fund the system.

---

# Fee collection occurs in SOLUM

Liquidity and Treasury fees are initially collected as SOLUM.

They are not immediately converted into ETH on every transaction.

Conceptually:

**BUY or SELL**

↓

**fee calculated**

↓

**Liquidity SOLUM allocated**

and/or

**Treasury SOLUM allocated**

↓

**SOLUM held by contract**

The contract later decides when enough accumulated balance exists to process SwapBack.

---

# Contract-held SOLUM

The Liquidity and Treasury allocations are credited to the Smart Contract itself.

Internally, the contract also tracks how much of that accumulated SOLUM belongs conceptually to each bucket.

This allows it to distinguish:

> **SOLUM reserved for Liquidity**

from:

> **SOLUM reserved for Treasury**

even though both may physically sit in the contract's token balance before SwapBack.

This distinction is important.

> **Contract balance is custody.**
>
> **Bucket accounting is purpose.**

---

# Contract balance is not one economic category

An AI or analytical system should not assume:

> **all SOLUM held by the contract = Treasury**

or:

> **all SOLUM held by the contract = Liquidity**

The contract can hold accumulated allocations for different purposes.

Therefore current contract balance and internal bucket state must be interpreted together where precise attribution matters.

---

# Liquidity allocation

Liquidity SOLUM is intended to support automated liquidity provision.

But the complete Liquidity allocation is not simply swapped to ETH.

The SwapBack mechanism uses part of the Liquidity tokens as the token side of the liquidity pair.

Conceptually:

**Liquidity SOLUM selected**

↓

**part retained as SOLUM**

+

**part swapped into ETH**

↓

**SOLUM + ETH**

↓

**liquidity added**

This is the basis of the automated liquidity mechanism.

---

# Treasury allocation

Treasury SOLUM follows a different path.

The selected Treasury allocation is swapped to ETH during SwapBack.

That ETH is then sent to the configured Treasury address.

Conceptually:

**Treasury SOLUM**

↓

**Swap to ETH**

↓

**Treasury ETH**

↓

**Treasury address**

Therefore the Treasury receives ETH through the SwapBack path rather than receiving the accumulated Treasury SOLUM directly in the ordinary execution model.

---

# One SwapBack processes both systems

Liquidity and Treasury are economically separate buckets.

Their execution is coordinated through SwapBack.

When SwapBack runs, it determines how much accumulated SOLUM is available to process and how that amount should be attributed proportionally between:

- Liquidity,
- Treasury.

The relevant quantities are selected according to current bucket state and the configured SwapBack maximum.

→ **[Explore SwapBack](/smart-contract/tokenomics/swapback/)**

---

# Proportional processing

Suppose the contract has accumulated both Liquidity and Treasury tokens.

If the complete accumulated amount exceeds the current maximum SwapBack amount, only part of the balance is processed.

The selected processing amount is attributed proportionally to the existing internal Liquidity and Treasury buckets.

This preserves the economic relationship between both allocations.

The contract should not arbitrarily process Treasury while ignoring Liquidity, or vice versa, when both are represented in the selected balance.

---

# Liquidity is divided

The selected Liquidity allocation is effectively divided into two roles.

One portion remains SOLUM.

Another portion contributes to the token amount that is swapped for ETH.

The retained SOLUM later pairs with the Liquidity share of ETH.

This is why automated liquidity provision requires both:

> **token**

and:

> **native asset**

rather than simply selling all Liquidity tokens.

---

# Treasury tokens are swapped

Treasury does not need a retained SOLUM side for liquidity pairing.

Its selected token allocation can be included in the swap-to-ETH portion.

The resulting ETH attributed to Treasury is then transferred to the current Treasury address.

This produces a clear distinction.

## Liquidity

Needs:

- retained SOLUM,
- ETH.

## Treasury

Needs:

- ETH destination.

---

# Swap path

The contract uses the configured V2-style router to perform the relevant token-to-native-asset conversion.

At a high level:

**SOLUM**

↓

**Router**

↓

**ETH**

The exact router, pair, path, deadline, minimum-output calculation, and implementation details belong to the contract and Repository.

The important economic result is that accumulated fee SOLUM can be converted into native asset for:

- Treasury,
- liquidity pairing.

---

# Slippage protection

Swap execution uses a configurable slippage parameter.

Initial value:

> **3%**

The contract constrains the configurable slippage range to:

> **0.5% minimum**

and:

> **8% maximum**

Slippage therefore belongs to the execution layer of Liquidity and Treasury.

It does not change the original fee percentages.

It affects the minimum acceptable output conditions of SwapBack execution.

---

# Liquidity is then added

After the swap:

- retained Liquidity SOLUM exists,
- Liquidity-attributed ETH exists.

The contract calls the configured liquidity-addition mechanism using both assets.

Conceptually:

> **SOLUM + ETH → LP position**

This creates liquidity for the configured SOLUM pair.

The contract automates the operation.

But automation does not answer the ownership question.

---

# LP tokens

When liquidity is added, the liquidity-provider tokens generated by that operation are sent to:

> **the current owner address**

This is a critical contract fact.

The Smart Contract does not automatically send those LP tokens to:

- address(0),
- Treasury,
- the contract itself as permanent custody,
- a locker,
- a multisig,
- or a DAO.

It sends them to the current owner.

> **Automated liquidity provision does not equal automated LP locking.**

---

# LP tokens are not locked by this contract

The contract itself does not enforce a liquidity lock.

Therefore documentation must never claim:

> **Liquidity is locked**

merely because SwapBack automatically adds liquidity.

Those are different statements.

The accurate statement is:

> **The contract can automatically add liquidity.**
>
> **The resulting LP tokens are sent to the current owner.**
>
> **This contract does not itself lock those LP tokens.**

If a separate locker or multisig later holds the LP tokens, that should be documented as a separate verifiable state.

---

# Current owner matters

Because LP tokens are sent to:

> **owner**

the recipient can change if ownership changes before future liquidity additions.

Therefore:

> **LP recipient is not necessarily forever the original deployer.**

It is the owner at the time the liquidity operation executes.

This is another reason current blockchain state matters.

---

# LP ownership is a trust boundary

LP tokens can carry economic authority over the liquidity position.

Therefore their custody belongs to the trust model.

Questions include:

- Who currently owns LP tokens?
- Are they locked externally?
- Are they held by a multisig?
- Can they be removed?
- Has ownership changed?
- Does the current public claim match observable state?

These questions belong to Security and operational transparency.

→ **[Explore Security](/smart-contract/security/)**

---

# Treasury

Treasury is the configured destination for the Treasury share of SwapBack-generated ETH.

It is not necessarily permanently fixed.

The contract allows Treasury to change through a delayed two-step process.

Conceptually:

**Propose new Treasury**

↓

**wait at least 48 hours**

↓

**Confirm new Treasury**

Only then does the configured Treasury change.

---

# Treasury change timelock

The Treasury change delay is:

> **48 hours**

This is longer than the:

> **24-hour fee-reduction timelock**

used elsewhere.

The delay creates a public interval between proposal and confirmation.

This does not remove owner authority.

It makes the transition delayed and observable.

---

# New Treasury exemptions

When a new Treasury is confirmed, the contract automatically marks it:

> **Fee Exempt**

and:

> **Limit Exempt**

This gives the Treasury special operational treatment.

The reason is architectural.

Treasury-related operations should not necessarily be blocked or taxed like an ordinary participant wallet.

But the privileges must remain explicit.

---

# Previous Treasury exemptions

There is an important implementation detail.

When Treasury changes, the contract automatically grants the relevant exemptions to the new Treasury.

It does not automatically remove:

- Fee Exempt status,
- Limit Exempt status

from the previous Treasury.

Therefore the old Treasury may remain exempt unless the owner separately changes those exemption mappings.

This is not something documentation should hide.

It is part of the actual permission model.

→ **[Explore Permissions](/smart-contract/tokenomics/permissions/)**

---

# Treasury is not a DAO

A Treasury address is an economic destination.

That does not automatically make it:

- decentralized,
- community-controlled,
- a DAO,
- a State treasury,
- a Kingdom treasury,
- or a civilizational government.

Those meanings would require additional canonical structures.

The contract simply defines Treasury as a technical destination within its economic architecture.

Future Chapters may add other interpretations.

Until then:

> **Treasury means Treasury.**

---

# Treasury is not the Pool

Treasury and Pool are distinct.

Pool-held SOLUM is canonically associated with:

> **Dormant Land**

Treasury-related economic state has a different function.

A Treasury balance must not be interpreted as Dormant Land merely because the tokens sit outside an ordinary Holder wallet.

State classification matters.

→ **[Explore Pool](/smart-contract/pool/)**

---

# Treasury is not Burn

Treasury SOLUM or Treasury ETH remains economically available according to its actual custody and permissions.

Burned SOLUM does not.

Therefore:

> **Treasury ≠ Permanent Nature**

and:

> **Treasury allocation ≠ Burn**

unless some future explicit mechanism performs a Burn.

The transaction fee architecture keeps those allocations separate.

---

# Liquidity is not Burn

The same distinction applies to Liquidity.

SOLUM used to create liquidity remains part of active economic infrastructure.

It has not been Burned merely because it is no longer sitting in an ordinary Holder wallet.

An LP position and Permanent Nature are categorically different states.

---

# Fee reduction affects funding rate

BUY and SELL fees can decrease.

Therefore future Liquidity and Treasury inflow can also decrease.

For example:

If BUY falls below its initial 1%, the absolute amount allocated to Liquidity and Treasury per ordinary BUY also falls proportionally.

If SELL falls below its initial 10%, the absolute Liquidity and Treasury contribution from SELL also falls proportionally.

Therefore:

> **initial funding rates are not permanent guaranteed rates.**

Current fee state matters.

→ **[Explore Fees](/smart-contract/tokenomics/fees/)**

---

# Liquidity share remains structurally proportional

Under the contract's fee-split architecture:

BUY allocates:

> **50% of the current BUY fee to Liquidity**

SELL allocates:

> **20% of the current SELL fee to Liquidity**

This means fee reductions reduce absolute Liquidity funding while preserving the structural split associated with the relevant transaction type.

The same principle applies to Treasury.

---

# Treasury share remains structurally proportional

BUY allocates:

> **50% of the current BUY fee to Treasury**

SELL allocates:

> **10% of the current SELL fee to Treasury**

Therefore the initial effective rates of:

- 0.5% BUY Treasury,
- 1% SELL Treasury

should be understood as initial values derived from the initial total fees.

They can fall if total fees are reduced.

---

# Example: BUY

Consider an ordinary non-exempt BUY of:

> **1,000 SOLUM**

under the initial configuration.

The BUY fee is:

> **10 SOLUM**

allocated:

| Component | SOLUM |
|:----------|------:|
| Liquidity | 5 |
| Treasury | 5 |
| Recipient | 990 |

The 5 Liquidity SOLUM and 5 Treasury SOLUM are accumulated in the contract for later processing.

They are not necessarily swapped immediately.

---

# Example: SELL

Consider an ordinary non-exempt SELL of:

> **1,000 SOLUM**

under the initial configuration.

The SELL fee contains:

| Component | SOLUM |
|:----------|------:|
| Burn | 40 |
| Reflection | 30 |
| Liquidity | 20 |
| Treasury | 10 |
| Net transfer | 900 |

Only:

> **20 Liquidity SOLUM**

and:

> **10 Treasury SOLUM**

enter the corresponding contract-held accumulation path.

Burn and Reflection follow different execution paths.

---

# Accumulated fees are state

The amount currently available for Liquidity and Treasury processing depends on previous transaction activity and prior SwapBack execution.

Therefore a live answer to:

> **How much SOLUM is waiting for Liquidity?**

or:

> **How much is waiting for Treasury?**

requires current contract state.

Initial fee percentages alone cannot answer it.

---

# SwapBack threshold delays execution

Initial SwapBack threshold:

> **200,000,000 SOLUM**

Until the relevant conditions are satisfied and the contract balance reaches the required threshold, accumulated Liquidity and Treasury SOLUM can remain inside the contract.

Therefore:

> **fee collection can precede fee realization.**

This distinction is important for Metrics.

A Treasury fee can have been collected without its corresponding ETH yet having been sent to Treasury.

---

# Maximum SwapBack

Initial maximum processing amount:

> **1,000,000,000 SOLUM**

If accumulated eligible tokens exceed that amount, SwapBack does not necessarily process everything at once.

The maximum constrains the amount selected for one SwapBack execution.

The remainder can stay accumulated for future processing.

---

# Cooldown

Initial SwapBack cooldown:

> **60 seconds**

The contract requires sufficient time since the previous SwapBack before another eligible SwapBack can occur.

The owner can configure the cooldown within the contract's allowed maximum:

> **15 minutes**

The cooldown affects processing frequency.

It does not change fee generation.

---

# SwapBack can be paused

The owner can disable SwapBack.

When paused:

- fee collection can still occur where ordinary fee logic remains active,
- but automated SwapBack processing does not execute through the normal enabled path.

This can cause Liquidity and Treasury SOLUM to continue accumulating inside the contract.

Therefore:

> **SwapBack enabled state is economically relevant.**

→ **[Explore SwapBack](/smart-contract/tokenomics/swapback/)**

---

# Pausing does not erase the buckets

Disabling SwapBack does not mean previously accumulated Liquidity and Treasury allocations vanish.

The state remains until processed or otherwise affected by actual contract behavior.

An AI should therefore distinguish:

> **SwapBack disabled**

from:

> **no accumulated fees**

They are unrelated claims.

---

# Treasury payment can fail

Treasury receives ETH through a low-level transfer path defined by the implementation.

Operational behavior therefore depends on whether that transfer succeeds under the contract's execution conditions.

Exact failure behavior should be verified from the Solidity implementation when analyzing edge cases.

The important rule is:

> **Configured destination does not eliminate execution risk.**

Security analysis belongs alongside Tokenomics.

---

# Liquidity addition can fail

Adding liquidity depends on:

- router behavior,
- available token amount,
- available ETH,
- allowance,
- pair infrastructure,
- deadline,
- minimum amounts,
- and other implementation conditions.

Automated intent does not guarantee every external call succeeds under every market condition.

That is why SwapBack and Security deserve their own technical documentation.

---

# External dependencies

Liquidity processing depends on external DEX infrastructure.

The Smart Contract therefore relies on components outside its own code, including:

- Router,
- Pair,
- native-asset market path.

These dependencies expand the trust and execution boundary.

Tokenomics describes the economic relationship.

Security evaluates the risk.

---

# Liquidity and market price

Automated liquidity can affect market structure.

But the contract does not guarantee:

- stable price,
- deep liquidity,
- low volatility,
- permanent liquidity availability,
- or profitable trading conditions.

Liquidity provision is infrastructure.

Market outcome remains emergent.

> **Liquidity is not a price guarantee.**

---

# Treasury and project economics

Treasury creates an economic resource for the project.

Its exact use is not dictated by the mere fact that ETH arrives at the Treasury address.

A Treasury can finance development or future systems only according to the actual decisions and canonical structures governing it.

The token contract provides the flow.

It does not automatically provide governance over that flow.

---

# Treasury transparency

A transparent Treasury architecture should eventually allow observers to determine:

- current Treasury address,
- Treasury-change proposals,
- confirmation time,
- ETH received through SwapBack,
- relevant on-chain movements,
- and current permissions.

Where off-chain expenditure occurs, blockchain alone may not describe purpose.

The Atlas should distinguish observable flow from claimed use.

---

# Liquidity transparency

Likewise, participants should eventually be able to inspect:

- Pair address,
- Router address,
- liquidity-addition events,
- LP-token recipient,
- current LP ownership where visible,
- any external lock,
- and any future changes in custody.

This is much stronger than simply stating:

> **Liquidity is provided automatically.**

---

# SolumTools

SolumTools may eventually expose deterministic signals such as:

- current contract SOLUM balance,
- Liquidity bucket,
- Treasury bucket,
- current Treasury address,
- SwapBack enabled state,
- threshold,
- maximum amount,
- cooldown,
- slippage,
- and recent SwapBack state.

That would make the economic mechanism readable without requiring manual contract inspection.

→ **[Explore SolumTools](/world/solumtools/)**

---

# Metrics

Metrics may eventually distinguish:

**Fees collected**

from:

**Fees processed**

from:

**Liquidity added**

from:

**Treasury ETH received**

These are not the same number.

A dashboard that merges them would obscure the actual economic pipeline.

Historical measurement should preserve the stages.

→ **[Explore Metrics](/metrics/)**

---

# Artificial Intelligence rules

An AI answering questions about Liquidity or Treasury should determine:

### Current fees

Because funding rates can decrease.

### Current SwapBack parameters

Because they are configurable.

### Current SwapBack enabled state

Because processing can be paused.

### Current Treasury

Because Treasury can change.

### Current owner

Because LP tokens are sent to owner.

### Current exemption state

Because Treasury and other relevant addresses may have special treatment.

### External custody

Because LP locking, if any, is not enforced by this contract.

Static documentation gives architecture.

Live state gives current reality.

---

# What AI must not say

AI should not say:

> **All Liquidity fees are immediately added to liquidity.**

Incorrect.

They accumulate first.

It should not say:

> **Treasury receives SOLUM directly from every taxed transaction.**

Incomplete under the SwapBack execution model.

It should not say:

> **LP tokens are locked.**

Not by this contract.

It should not say:

> **Treasury is decentralized.**

Not established by the Treasury mechanism itself.

It should not say:

> **The deployer always receives LP tokens.**

The current owner receives them.

Ownership can change.

---

# Contract and Zipvilization

Liquidity and Treasury primarily belong to the economic infrastructure layer.

Unlike Pool and Burn, they do not automatically have direct territorial aliases such as:

> Dormant Land

or:

> Permanent Nature.

That is important.

We should not force every blockchain mechanism into a world metaphor.

Liquidity is market infrastructure.

Treasury is project economic infrastructure.

Future Chapters may create richer civilizational relationships.

Until then, accuracy is more important than symmetry.

> **Not every mechanism needs a metaphor.**

---

# Liquidity & Treasury in one view

## Initial Liquidity funding

BUY:

> **0.5%**

SELL:

> **2%**

TRANSFER:

> **0%**

## Initial Treasury funding

BUY:

> **0.5%**

SELL:

> **1%**

TRANSFER:

> **0%**

## Processing

Liquidity and Treasury SOLUM:

- accumulate inside the contract,
- are tracked separately,
- are later processed by SwapBack.

## Liquidity

Selected Liquidity tokens are divided between:

- retained SOLUM,
- swap-to-ETH allocation.

Then:

> **SOLUM + ETH → liquidity**

## Treasury

Selected Treasury tokens are swapped into ETH.

Treasury's ETH share is sent to:

> **current Treasury address**

## LP tokens

Generated LP tokens are sent to:

> **current owner**

The contract does not lock them.

## Treasury authority

Treasury can change through:

> **proposal → 48 hours → confirmation**

New Treasury becomes:

- Fee Exempt,
- Limit Exempt.

Previous Treasury exemptions are not automatically removed.

---

# Follow Liquidity & Treasury

### Return to Tokenomics

→ **[Tokenomics](/smart-contract/tokenomics/)**

### Understand the fee sources

→ **[Fees](/smart-contract/tokenomics/fees/)**

### Understand Burn and Reflection allocations

→ **[Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

### Understand SwapBack execution

→ **[SwapBack](/smart-contract/tokenomics/swapback/)**

### Understand administrative authority

→ **[Permissions](/smart-contract/tokenomics/permissions/)**

### Understand the broader Tax mechanism

→ **[Taxes](/smart-contract/taxes/)**

### Understand security and LP custody

→ **[Security](/smart-contract/security/)**

### Inspect implementation

→ **[Repository](/repository/)**

---

# From fee to infrastructure

Liquidity and Treasury begin as fractions of a transaction.

A few SOLUM here.

A few SOLUM there.

They accumulate.

Eventually the threshold is reached.

SwapBack transforms that accumulated state.

Some SOLUM becomes ETH.

Some SOLUM remains SOLUM.

Liquidity is added.

Treasury receives its ETH share.

And LP tokens go to the current owner.

Every step matters.

Because transparency is not saying:

> **Part of the fee goes to Liquidity and Treasury.**

Transparency is being able to answer:

> How much?

> In what asset?

> When?

> Through which mechanism?

> Under what threshold?

> With what slippage?

> To which address?

> Who controls the LP?

> What can change?

That is the standard Tokenomics should maintain.

> **Follow the SOLUM.**
>
> **Follow the ETH.**
>
> **Follow the authority.**

---

→ **[Return to Tokenomics](/smart-contract/tokenomics/)**  
→ **[Return to Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**  
→ **[Continue to Limits](/smart-contract/tokenomics/limits/)**
