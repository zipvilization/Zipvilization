---
layout: default
title: SwapBack
parent: Tokenomics
grand_parent: Smart Contract
nav_order: 7
description: >
  SwapBack documents the automated processing of accumulated Liquidity and
  Treasury SOLUM: trigger conditions, threshold, processing cap, cooldown,
  proportional bucket accounting, slippage protection, token-to-ETH swap,
  liquidity creation, Treasury payment, administrative controls, and failure
  boundaries.
permalink: /smart-contract/tokenomics/swapback/
---

# SwapBack

Liquidity and Treasury fees do not complete their economic function when they are collected.

They accumulate first.

SwapBack processes them later.

The mechanism converts accumulated contract-held SOLUM into:

- liquidity infrastructure,
- Treasury ETH.

At a high level:

**Liquidity + Treasury fees accumulate**

↓

**SwapBack conditions are satisfied**

↓

**a bounded amount of SOLUM is selected**

↓

**Liquidity and Treasury buckets are allocated proportionally**

↓

**part of the SOLUM is swapped for ETH**

↓

**SOLUM + ETH are added to Liquidity**

↓

**remaining ETH is sent to Treasury**

This page documents that process.

> **Fee collection creates the resources.**
>
> **SwapBack deploys them.**

---

# Canonical Snapshot

| Parameter | Initial contract value |
|:----------|-----------------------:|
| SwapBack enabled | Yes |
| Trigger transaction | SELL |
| Initial threshold | 200,000,000 SOLUM |
| Initial maximum per SwapBack | 1,000,000,000 SOLUM |
| Initial cooldown | 60 seconds |
| Initial slippage | 3% |
| Allowed slippage range | 0.5%–8% |
| Maximum cooldown | 15 minutes |
| Maximum amount rule | Must be ≥ threshold |
| Processing basis | Contract token balance + bucket accounting |
| Liquidity execution | SOLUM + ETH |
| Treasury execution | ETH transfer |
| LP recipient | Current owner |
| SwapBack pause authority | Owner |
| Config authority | Owner |
| Config timelock | None in this contract |

These values describe the initial configuration and explicit contract constraints.

Several are mutable.

Current live state may therefore differ after deployment.

---

# What funds SwapBack

SwapBack processes two internal fee buckets:

> **Liquidity**

and:

> **Treasury**

These buckets are created from ordinary non-exempt BUY and SELL fees.

Under the initial fee configuration:

## BUY

> **0.5% → Liquidity**

> **0.5% → Treasury**

## SELL

> **2% → Liquidity**

> **1% → Treasury**

## TRANSFER

> **0% → Liquidity**

> **0% → Treasury**

The contract tracks the accumulated purposes separately.

→ **[Explore Fees](/smart-contract/tokenomics/fees/)**

---

# Two internal buckets

The contract maintains:

`_tokensForLiquidity`

and:

`_tokensForTreasury`

These values represent the accumulated SOLUM allocations awaiting processing.

They are accounting buckets.

The actual tokens are held by the Smart Contract address.

Therefore:

> **contract token balance**

and:

> **sum of economic buckets**

are related but conceptually distinct quantities.

---

# Collection and processing are different events

When a qualifying BUY or SELL generates Liquidity or Treasury fees:

the corresponding SOLUM is transferred into the contract.

At that moment:

- fee collection has occurred,
- bucket accounting has increased.

SwapBack may not occur yet.

It requires its own conditions.

Therefore:

> **Collected ≠ Processed**

This distinction is essential for both Metrics and AI.

---

# Initial threshold

The initial SwapBack threshold is:

> **200,000,000 SOLUM**

SwapBack will not proceed through its normal trigger path unless the contract's token balance is at least that threshold.

Therefore small accumulated fee balances can remain inside the contract until enough SOLUM has accumulated.

The threshold concerns execution timing.

It does not change the fee rates themselves.

---

# Initial maximum processing amount

The initial maximum amount processed in one SwapBack is:

> **1,000,000,000 SOLUM**

or:

> **1 billion SOLUM**

If the contract holds less than that amount but at least the threshold:

the available contract balance can become the processing amount.

If the contract holds more:

the amount processed is capped at the configured maximum.

Conceptually:

> **Amount to Process = min(contract token balance, SwapBack maximum)**

subject to the threshold and other execution conditions.

---

# Threshold and maximum are different

These two values answer different questions.

**Threshold**

asks:

> Has enough SOLUM accumulated to permit SwapBack?

**Maximum**

asks:

> Once SwapBack is permitted, how much can this execution process at most?

Initial values:

> **Threshold = 200M SOLUM**

> **Maximum = 1B SOLUM**

Therefore reaching 200M can permit processing.

It does not require exactly 200M to be processed.

---

# Maximum must remain above threshold

When the owner changes SwapBack configuration, the contract requires:

> **maximum amount ≥ threshold**

This prevents a configuration in which the minimum balance required to trigger processing is larger than the maximum amount permitted for one processing operation.

It is an explicit contract invariant.

---

# SwapBack cooldown

Initial cooldown:

> **60 seconds**

SwapBack requires:

> **current timestamp ≥ lastSwapBackTime + cooldown**

before another normal execution can trigger.

The cooldown therefore limits processing frequency.

It does not limit:

- BUY frequency,
- SELL frequency,
- fee collection,
- or Treasury use.

It belongs specifically to SwapBack execution.

---

# Cooldown can change

The owner can configure the SwapBack cooldown.

The contract imposes an upper bound:

> **15 minutes maximum**

A cooldown of:

> **0 seconds**

is also permitted by the explicit upper-bound condition.

Therefore the allowed contract range is:

> **0 to 15 minutes**

The initial value is:

> **60 seconds**

This is current-state-sensitive configuration.

---

# Slippage

Initial SwapBack slippage:

> **3%**

The contract stores this value in basis points.

Initial value:

> **300 basis points**

The configurable range is:

> **50 to 800 basis points**

which corresponds to:

> **0.5% to 8%**

This parameter affects the minimum acceptable output calculation for the token-to-ETH swap where router quotation is available.

---

# Slippage does not change fees

Slippage and transaction fees are separate.

A 3% SwapBack slippage setting does not mean:

> **users pay an additional 3% fee.**

It controls the swap-execution protection used when accumulated contract tokens are converted into ETH.

Therefore:

> **Transaction Fee ≠ SwapBack Slippage**

An AI should never add the two percentages together as if they represented one user-facing tax.

---

# When SwapBack can trigger

The contract checks several conditions.

SwapBack requires:

- SwapBack enabled,
- not already inside SwapBack,
- trading enabled,
- receiver of the current transaction is the Pair,
- cooldown elapsed,
- contract token balance at least threshold.

The Pair condition means:

> **SwapBack is triggered primarily on SELL.**

Technically, the contract requires:

> **to == Pair**

for the normal trigger path.

---

# BUY does not normally trigger SwapBack

For a BUY:

> `from == Pair`

and the receiver is not the Pair.

Therefore the normal `_shouldSwapBack()` condition fails.

A BUY can create additional Liquidity and Treasury SOLUM.

But it does not normally trigger SwapBack itself.

Collection and trigger are separate.

---

# TRANSFER does not normally trigger SwapBack

For an ordinary wallet-to-wallet TRANSFER:

the receiver is not the Pair.

Therefore it does not satisfy the normal SELL-side SwapBack trigger.

Also, ordinary TRANSFER fees do not fund Liquidity or Treasury under the initial fee architecture.

---

# SELL is the trigger

A SELL has:

> **to == Pair**

Therefore it is the transaction type capable of satisfying the normal SwapBack trigger condition.

But not every SELL causes SwapBack.

The other conditions must also be true.

For example:

- threshold reached,
- cooldown elapsed,
- SwapBack enabled.

---

# SwapBack happens before the triggering SELL is processed

This is an important implementation detail.

Inside `_transfer()` the contract checks `_shouldSwapBack()` before it calculates and applies the fees for the current transfer.

Therefore, when a SELL triggers SwapBack:

> **SwapBack processes previously accumulated state before the current SELL's new fee allocations are added.**

The current SELL can subsequently create new Liquidity and Treasury allocations.

Those new allocations are not what caused the already-running SwapBack to meet its threshold.

This matters for exact transaction analysis.

---

# The triggering SELL still continues afterward

After SwapBack finishes successfully, the contract continues processing the original SELL.

That SELL can then:

- transfer its net amount,
- Burn its Burn allocation,
- apply Reflection,
- add new Liquidity SOLUM,
- add new Treasury SOLUM.

Therefore a triggering SELL can both:

> **cause old accumulated buckets to be processed**

and:

> **create new bucket balances afterward.**

The two stages occur within the same outer transaction.

---

# Reentrancy guard

SwapBack uses an internal lock.

During execution:

> `_inSwapBack = true`

and afterward:

> `_inSwapBack = false`

The transfer fee logic also checks `_inSwapBack`.

This prevents the contract's own swap-related token movements from recursively taking ordinary transaction fees through the same path.

It also prevents nested normal SwapBack triggering.

---

# SwapBack movements do not take ordinary fees

The ordinary fee condition includes:

> **not currently in SwapBack**

Therefore internal SwapBack token movement is not treated like an ordinary taxable participant transaction.

This prevents the economic processing mechanism from repeatedly taxing itself.

---

# lastSwapBackTime is updated at entry

When `_swapBack()` begins, the contract sets:

> **lastSwapBackTime = block.timestamp**

before checking some of the later internal execution conditions.

This means the cooldown timestamp is associated with entering the SwapBack routine.

That is an implementation detail worth preserving for exact analysis.

---

# Contract token balance is measured from reflected accounting

The contract derives its current token balance through the Reflection conversion mechanism.

It converts the contract's reflected ownership into token units.

Therefore SwapBack operates on the effective current SOLUM balance of the contract.

Reflection architecture remains relevant even to contract-held fee tokens.

→ **[Explore Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

---

# Selecting the processing amount

Once the threshold is satisfied:

the contract begins with its effective token balance.

Then:

if that balance exceeds the current SwapBack maximum,

the processing amount is capped.

Conceptually:

**Contract token balance**

↓

**apply maximum cap**

↓

**Amount to Process**

This amount becomes the basis for proportional bucket processing.

---

# Bucket total

The contract calculates:

> **Liquidity Bucket + Treasury Bucket**

If their sum is zero:

SwapBack exits without attempting the proportional calculations.

This avoids division by zero.

Under ordinary production fee flows, those buckets should describe the economic purpose of collected fee tokens.

But the contract explicitly handles a zero-bucket state.

---

# Proportional bucket scaling

The amount selected for one SwapBack may be smaller than the total accumulated buckets.

Therefore the contract scales the Liquidity allocation proportionally.

Conceptually:

> **Liquidity Selected = Liquidity Bucket × Amount to Process / Total Bucket**

Treasury receives the remainder of the selected processing amount:

> **Treasury Selected = Amount to Process − Liquidity Selected**

This keeps the processing mix proportional to accumulated bucket state.

---

# Why Treasury uses the remainder

The contract derives the selected Liquidity amount first.

Because Solidity integer division can truncate, Treasury is calculated as the remaining selected amount.

This ensures:

> **Liquidity Selected + Treasury Selected = Amount to Process**

exactly at integer-token-unit level.

That prevents processing-accounting loss from the proportional split itself.

---

# Liquidity is divided in half

The selected Liquidity SOLUM is then divided.

Conceptually:

> **Liquidity Token Half = Liquidity Selected / 2**

This amount remains SOLUM for later pairing with ETH.

The rest of the selected processing amount is swapped into ETH.

That swapped amount includes:

- the other Liquidity portion,
- the Treasury portion.

---

# tokensToSwap

Conceptually:

> **Tokens to Swap = Amount to Process − Liquidity Token Half**

This includes all selected Treasury SOLUM plus the Liquidity portion that needs to become ETH.

The retained Liquidity half is not swapped.

It remains available as the token side of the LP addition.

---

# Odd-number rounding

Because Solidity uses integer arithmetic:

> **Liquidity Selected / 2**

can truncate by one atomic unit when the amount is odd.

The contract then derives the swapped amount from the full processing amount minus the retained half.

For exact accounting at atomic-unit scale, use the implementation rather than assuming perfectly symmetric decimal halves.

---

# Buckets are reduced before the external swap

Before calling the router, the contract reduces the internal Liquidity and Treasury buckets by the selected amounts.

This is a significant implementation detail.

The sequence is:

**select bucket amounts**

↓

**reduce bucket accounting**

↓

**approve router**

↓

**perform external swap**

If the subsequent transaction reverts entirely, normal EVM transaction atomicity reverts state changes as well.

But within successful/non-reverting paths, the bucket reduction occurs before the external conversion call.

---

# A special zero-ETH path

The contract includes handling for environments where the swap returns without increasing the contract's ETH balance.

If:

> **ETH gained = 0**

the function returns without adding liquidity or paying Treasury.

The code comments identify this primarily as a pure-mock/testing accommodation.

The buckets have already been reduced in that non-reverting path.

This is an implementation behavior, not a general economic promise.

For production analysis, actual router behavior and execution environment matter.

---

# Router approval

Before processing the swap and liquidity addition, the contract sets an allowance for the Router sufficient for:

- tokens being swapped,
- retained Liquidity tokens that will later be added to the LP.

The Router can then pull the required SOLUM through the relevant calls.

Approval is part of the execution path.

---

# Best-effort minimum output

Before swapping, the contract attempts to ask the Router for an output quote through:

> `getAmountsOut`

If the call succeeds:

the quoted output is reduced by the configured slippage percentage to derive a minimum acceptable output.

Conceptually:

> **Minimum Output = Quoted Output × (1 − Slippage)**

With the initial 3% configuration:

> **Minimum Output = Quoted Output × 97%**

subject to integer arithmetic.

---

# What “best effort” means

The quote call is wrapped in error handling.

If `getAmountsOut` fails:

the contract returns:

> **minOut = 0**

rather than cancelling SwapBack solely because quotation was unavailable.

This is why the source describes the mechanism as:

> **Best-effort slippage guard**

This is an important security and execution detail.

---

# minOut can therefore be zero

An AI must not assume that configured slippage always guarantees a non-zero minimum-output protection.

If the Router quotation call fails:

> **minimum output becomes zero**

for that swap execution path.

The swap can then proceed using that zero minimum.

This belongs both to Tokenomics and Security.

→ **[Explore Security](/smart-contract/security/)**

---

# Defensive slippage cap

The internal minimum-output calculation defensively ensures that the basis-point value used does not exceed the denominator.

The administrative setter already restricts configured slippage to a much narrower 0.5%–8% range.

This second check is therefore defensive.

---

# Token-to-ETH swap

The contract then swaps:

> **tokensToSwap**

from SOLUM into ETH through the configured Router.

The path is:

**SOLUM**

↓

**wrapped native asset route**

↓

**ETH received by the contract**

The ETH balance before and after the swap is compared to determine:

> **ETH gained**

from this execution.

---

# Fee-on-transfer-compatible swap path

The Router function used is designed to support tokens with transfer fees.

That is relevant because SOLUM itself contains custom fee behavior.

However, during SwapBack, `_inSwapBack` prevents ordinary SOLUM transaction fees from applying to the contract's internal processing path.

The Router interface remains compatible with fee-on-transfer-style token behavior.

---

# ETH allocation

After determining total ETH gained, the contract calculates how much belongs to Liquidity.

The relevant token-side quantity is the Liquidity portion that was swapped.

Conceptually:

> **Liquidity Swap Portion = Liquidity Selected − Liquidity Token Half**

Then:

> **ETH for Liquidity = ETH Gained × Liquidity Swap Portion / Tokens to Swap**

Treasury receives:

> **ETH for Treasury = ETH Gained − ETH for Liquidity**

Again, Treasury takes the remainder after integer proportional calculation.

---

# Liquidity addition

If both:

- retained Liquidity SOLUM > 0,
- ETH allocated to Liquidity > 0,

the contract adds liquidity using both assets.

The Router receives:

> **SOLUM + ETH**

and creates the corresponding liquidity position.

The minimum token and ETH amounts passed to the liquidity-addition function are:

> **0**

for both sides in the documented implementation.

This should be understood separately from the slippage calculation used for the preceding token-to-ETH swap.

---

# LP recipient

The liquidity-addition call sends resulting LP tokens to:

> **current owner**

This is explicit in the contract.

The recipient is not automatically:

- Treasury,
- the Smart Contract,
- address(0),
- a locker,
- a multisig.

Therefore:

> **SwapBack automates liquidity creation.**
>
> **It does not automate LP locking.**

→ **[Explore Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**

---

# Treasury ETH payment

After Liquidity allocation, any remaining Treasury ETH is sent to:

> **current Treasury**

through a direct native-asset call.

If that payment fails:

the contract requires success and the transaction reverts.

Therefore Treasury receiving behavior is part of successful SwapBack execution.

---

# Treasury failure can revert the triggering SELL

Because SwapBack occurs inside the outer SELL transaction, a failing Treasury ETH transfer can cause the entire transaction to revert.

This is an important operational consequence.

A Treasury address unable to receive ETH correctly can therefore affect SELL execution when a SwapBack is triggered.

That is part of the trust and availability model.

---

# Router failure can also revert execution

Likewise, if the Router swap or liquidity operation reverts:

the outer transaction can revert.

SwapBack is not an asynchronous background service.

It runs as part of the blockchain transaction that triggers it.

Therefore external DEX execution can affect the success of that SELL.

---

# SwapBack is not guaranteed on every SELL

A SELL only triggers processing when all required conditions are true.

For example:

- contract balance may be below threshold,
- cooldown may still be active,
- SwapBack may be paused.

Therefore a dashboard should distinguish:

> **SELL occurred**

from:

> **SwapBack occurred**

They are not synonymous.

---

# SwapBack can be paused

The owner can pause the mechanism.

The underlying state variable is changed so that `_shouldSwapBack()` returns false.

While paused:

- BUY/SELL fee collection can continue under the current fee architecture,
- Liquidity and Treasury buckets can continue accumulating,
- automated processing is suspended.

Therefore:

> **Paused processing does not mean paused fee collection.**

---

# Pause has no timelock in this contract

The owner can change the SwapBack paused state directly.

The documented contract does not impose a waiting period on this operation.

That must remain visible in the Permissions model.

→ **[Explore Permissions](/smart-contract/tokenomics/permissions/)**

---

# SwapBack configuration authority

The owner can directly change:

- threshold,
- maximum amount,
- cooldown,
- slippage.

The contract applies explicit bounds to some values.

But there is:

> **no configuration timelock in this contract**

for these changes.

Therefore the current configuration should be read from chain when transaction-level accuracy matters.

---

# Threshold has no explicit positive minimum

The setter does not require the threshold to be greater than zero.

Therefore:

> **threshold = 0**

is not rejected by the explicit configuration conditions, provided the other constraints are satisfied.

This could materially alter how frequently the `_shouldSwapBack()` balance condition is satisfied.

It is part of owner-configurable authority.

---

# Maximum amount has no explicit upper bound

The contract requires:

> **maximum amount ≥ threshold**

but does not impose an explicit maximum numerical ceiling in the configuration setter.

Therefore the owner can increase the processing cap substantially, subject to available balances and ordinary uint256 limits.

Again:

> **initial 1B maximum is configuration, not an immutable ceiling.**

---

# Slippage has explicit bounds

Unlike threshold and maximum amount, slippage is bounded.

Allowed:

> **0.5%–8%**

Not allowed through the setter:

- below 0.5%,
- above 8%.

This is an enforced configuration range.

---

# Cooldown has only an upper bound

Allowed:

> **0 to 15 minutes**

The initial setting is:

> **60 seconds**

Therefore the owner can make SwapBack eligible much more frequently by setting cooldown to zero.

Or less frequently by increasing it up to 15 minutes.

This changes execution cadence.

---

# Configuration changes are observable

When SwapBack configuration changes, the contract emits an event containing:

- threshold,
- maximum amount,
- cooldown,
- slippage.

Likewise, pausing emits its own event.

This provides a public basis for configuration history.

An indexer can reconstruct changes from events and current state.

---

# Initial configuration is not permanent configuration

This distinction should appear whenever we publish SwapBack parameters.

Initial:

- threshold = 200M,
- maximum = 1B,
- cooldown = 60 seconds,
- slippage = 3%.

But a live answer should read:

> **current configuration**

because the owner can change all four.

Tokenomics documents both:

**Genesis configuration**

and:

**mutability rules.**

---

# SwapBack and Fees

Fee reductions can change how quickly the Liquidity and Treasury buckets grow.

If BUY or SELL fees decrease:

less SOLUM may accumulate per comparable transaction.

Therefore reaching the same SwapBack threshold may take different amounts of economic activity over time.

SwapBack configuration and fee configuration interact economically without being the same mechanism.

→ **[Explore Fees](/smart-contract/tokenomics/fees/)**

---

# SwapBack does not process Burn

Burn happens immediately inside fee processing.

It does not wait for SwapBack.

Therefore SwapBack never needs to convert Burned SOLUM into ETH.

The SOLUM has already been permanently removed.

---

# SwapBack does not process Reflection

Reflection also follows its own immediate accounting path.

It does not accumulate in the Smart Contract's Liquidity/Treasury buckets.

Therefore:

> **SwapBack processes Liquidity + Treasury only.**

It does not process:

- Burn,
- Reflection.

→ **[Explore Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

---

# SwapBack and Reflection accounting

Although SwapBack does not process Reflection fees, the contract's own SOLUM balance is still represented through reflected ownership.

Therefore the effective token balance used for threshold checking and processing is derived through the Reflection accounting model.

The systems are separate but technically connected.

---

# SwapBack and Launch

SwapBack requires:

> **trading enabled**

Therefore it cannot trigger through its normal path before `enableTrading()`.

After trading begins, a qualifying SELL can trigger it even while the special 48-hour BUY launch rules remain active.

The Launch restrictions are BUY-specific.

SwapBack is SELL-triggered.

→ **[Explore Launch](/smart-contract/tokenomics/launch/)**

---

# SwapBack and Limits

The triggering SELL is subject to the broader transaction architecture.

However, the Pair is initially Limit Exempt, and limit behavior must follow actual current exemption state.

SwapBack's internal contract operations run under their own `_inSwapBack` handling.

Therefore ordinary user limits and internal processing should not be collapsed into one rule.

→ **[Explore Limits](/smart-contract/tokenomics/limits/)**

---

# SwapBack and Treasury authority

Changing Treasury changes where future Treasury ETH is sent.

Because Treasury can change through a 48-hour timelock, SwapBack must use the Treasury address current at execution time.

Historical fee collection does not permanently bind those accumulated Treasury tokens to the Treasury address that existed when each fee was originally collected.

The current contract configuration determines the payment destination when processing occurs.

This is an important economic consequence.

---

# Collected under one Treasury, paid to another

Consider:

- Treasury A is active,
- Treasury allocations accumulate,
- Treasury changes canonically to Treasury B before SwapBack processes those tokens.

When a later SwapBack executes:

the current `treasury` variable is used.

Therefore the ETH resulting from those selected Treasury tokens is sent to:

> **Treasury B**

not automatically Treasury A.

This follows from execution-time state.

It is worth making explicit.

---

# LP recipient also uses execution-time ownership

The same temporal principle applies to LP tokens.

If fees accumulated while Owner A controlled the contract, but ownership is transferred to Owner B before liquidity is added:

the LP tokens generated by the later SwapBack go to:

> **Owner B**

because `_addLiquidity()` uses the current `owner`.

Again:

> **collection-time authority and execution-time authority can differ.**

---

# Economic pipeline

The complete ordinary pipeline is:

**BUY / SELL**

↓

**Liquidity + Treasury fee SOLUM collected**

↓

**contract balance and buckets grow**

↓

**SELL occurs**

↓

**SwapBack eligibility checked**

↓

**threshold + cooldown + enabled state verified**

↓

**bounded amount selected**

↓

**Liquidity/Treasury proportional attribution**

↓

**Liquidity half retained**

↓

**remaining selected SOLUM swapped to ETH**

↓

**ETH split proportionally**

↓

**Liquidity SOLUM + Liquidity ETH added**

↓

**LP tokens → current owner**

↓

**Treasury ETH → current Treasury**

This is the full operational path.

---

# Example architecture

Suppose the selected SwapBack processing amount is:

> **300 SOLUM**

and the selected proportional bucket allocation is:

> **200 SOLUM Liquidity**

> **100 SOLUM Treasury**

This example is illustrative only.

The contract would conceptually retain:

> **100 SOLUM**

as the Liquidity token half.

It would swap:

> **200 SOLUM**

consisting of:

- 100 Liquidity-side SOLUM,
- 100 Treasury SOLUM.

If the swap produced:

> **2 ETH**

and the swapped Liquidity/Treasury proportions were exactly equal, conceptually:

- 1 ETH would be allocated to Liquidity,
- 1 ETH would be allocated to Treasury.

Then:

> **100 SOLUM + 1 ETH**

would be used for liquidity,

and:

> **1 ETH**

would go to Treasury.

Exact production results depend on integer arithmetic and market execution.

---

# This example is not contract state

The numbers above are explanatory.

They do not describe:

- current accumulated buckets,
- current ETH output,
- current liquidity,
- or current Treasury receipts.

Live values must come from blockchain state.

This distinction is especially important for AI.

---

# Market execution changes the ETH result

The contract determines how many SOLUM are selected.

The DEX market determines how much ETH the swap actually produces within the execution constraints.

Therefore Treasury ETH and Liquidity ETH are not fixed percentages of nominal SOLUM value.

They depend on:

- current reserves,
- price,
- price impact,
- router output,
- slippage protection,
- transaction execution.

Token allocation is deterministic.

Market conversion output is state-dependent.

---

# Price impact and slippage are different

A large SwapBack can affect market price through its token-to-ETH swap.

Configured slippage determines acceptable execution relative to the router quotation where available.

It does not eliminate:

- price impact,
- reserve effects,
- MEV risk,
- or market movement.

Therefore:

> **Slippage tolerance is not a guarantee of neutral market execution.**

---

# Maximum processing helps bound individual executions

The SwapBack maximum can limit how many accumulated contract tokens are sold in one processing operation.

The initial cap is:

> **1B SOLUM**

This can reduce the size of an individual automated swap relative to processing the entire accumulated contract balance at once.

But because the owner can reconfigure the cap, its current value is part of the trust model.

---

# Threshold creates batching

The threshold means the contract batches fee processing rather than swapping every small fee immediately.

This can reduce execution frequency.

But batching also means each eventual swap can be larger.

The economic design therefore balances:

- frequency,
- gas,
- price impact,
- accumulated size,
- market conditions.

The contract provides configurable parameters rather than a permanently fixed execution cadence.

---

# SwapBack and Security

SwapBack expands the contract's external interaction surface.

It depends on:

- Router calls,
- output quotation,
- token swap,
- ETH receipt,
- liquidity addition,
- Treasury ETH reception.

Security therefore needs to evaluate:

- Router trust,
- Pair correctness,
- slippage behavior,
- owner configuration authority,
- Treasury behavior,
- LP custody,
- external-call failure,
- and execution ordering.

→ **[Explore Security](/smart-contract/security/)**

---

# SwapBack and SolumTools

SolumTools should eventually be able to expose:

- SwapBack enabled state,
- current threshold,
- current maximum,
- current cooldown,
- current slippage,
- last SwapBack time,
- contract token balance,
- Liquidity bucket,
- Treasury bucket,
- next cooldown eligibility,
- current Treasury,
- current owner.

This would allow humans and AI to understand whether SwapBack is currently likely to execute.

→ **[Explore SolumTools](/world/solumtools/)**

---

# SwapBack and Metrics

Metrics should preserve different stages of the pipeline.

Potential measurements include:

- Liquidity fees collected,
- Treasury fees collected,
- SOLUM processed through SwapBack,
- ETH generated,
- ETH allocated to Liquidity,
- ETH sent to Treasury,
- liquidity additions,
- processing frequency,
- current accumulated buckets.

These are different metrics.

A single label such as:

> **Treasury Tax**

would lose important information.

→ **[Explore Metrics](/metrics/)**

---

# Artificial Intelligence rules

When answering a SwapBack question, AI should determine:

### 1. Is SwapBack currently enabled?

Do not assume the initial state remains current.

### 2. Is trading enabled?

Normal SwapBack triggering requires it.

### 3. Is the transaction a SELL?

Normal triggering requires `to == Pair`.

### 4. Has the cooldown elapsed?

Use current `lastSwapBackTime` and current cooldown.

### 5. Is contract token balance above current threshold?

Use current state.

### 6. What is the current maximum processing amount?

Initial 1B may have changed.

### 7. What are the current Liquidity and Treasury buckets?

Processing is proportional.

### 8. What is current slippage?

Initial 3% may have changed.

### 9. Who is current owner?

LP tokens go there.

### 10. What is current Treasury?

Treasury ETH goes there.

The architecture is static.

The execution state is dynamic.

---

# What AI must not say

AI should not say:

> **SwapBack runs every 60 seconds.**

Incorrect.

60 seconds is the initial minimum cooldown between eligible executions, not a scheduled timer.

It should not say:

> **SwapBack runs whenever the contract reaches 200M SOLUM.**

Incomplete.

It also requires SELL trigger, trading enabled, enabled state, and cooldown.

It should not say:

> **Every SELL performs SwapBack.**

Incorrect.

It should not say:

> **The triggering SELL's fees are included in the SwapBack that it triggered.**

Not in the documented execution order.

SwapBack occurs before that SELL's fee allocation.

It should not say:

> **Slippage is permanently 3%.**

Incorrect.

It is configurable from 0.5% to 8%.

It should not say:

> **LP tokens are locked.**

Incorrect for this contract alone.

It should not say:

> **Treasury receives the Treasury fee immediately on each BUY or SELL.**

Incorrect.

Treasury allocation accumulates first and is later processed.

---

# Fixed, bounded, and configurable

SwapBack contains several different parameter classes.

## Initial configuration

- threshold: 200M SOLUM,
- maximum: 1B SOLUM,
- cooldown: 60 seconds,
- slippage: 3%.

## Explicitly bounded

Slippage:

> **0.5%–8%**

Cooldown:

> **≤ 15 minutes**

Maximum:

> **must be ≥ threshold**

## Owner configurable

- enabled / paused state,
- threshold,
- maximum,
- cooldown,
- slippage.

## No timelock

The documented contract does not impose a timelock on these SwapBack configuration changes.

This distinction belongs in every transparency-oriented description.

---

# SwapBack in one view

## Funding

Created by:

- BUY Liquidity fee,
- BUY Treasury fee,
- SELL Liquidity fee,
- SELL Treasury fee.

## Initial trigger conditions

- trading enabled,
- SwapBack enabled,
- not already swapping,
- current transaction is SELL,
- cooldown elapsed,
- contract balance ≥ threshold.

## Initial parameters

**Threshold:** 200M SOLUM

**Maximum:** 1B SOLUM

**Cooldown:** 60 seconds

**Slippage:** 3%

## Processing

- select bounded token amount,
- scale Liquidity and Treasury proportionally,
- retain half of selected Liquidity SOLUM,
- swap remaining selected SOLUM to ETH,
- split ETH between Liquidity and Treasury,
- add SOLUM + ETH liquidity,
- send LP tokens to current owner,
- send Treasury ETH to current Treasury.

## Authority

Owner can:

- pause/resume SwapBack,
- change threshold,
- change maximum,
- change cooldown,
- change slippage,

subject to contract bounds.

No timelock applies to these configuration operations in this implementation.

---

# Follow SwapBack

### Return to Tokenomics

→ **[Tokenomics](/smart-contract/tokenomics/)**

### Understand the fees that fund SwapBack

→ **[Fees](/smart-contract/tokenomics/fees/)**

### Understand Liquidity, Treasury, and LP custody

→ **[Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**

### Understand the SELL trigger context

→ **[Launch](/smart-contract/tokenomics/launch/)**

### Understand owner configuration authority

→ **[Permissions](/smart-contract/tokenomics/permissions/)**

### Understand security implications

→ **[Security](/smart-contract/security/)**

### Inspect exact implementation

→ **[Repository](/repository/)**

---

# Follow every unit

SwapBack begins with something simple.

Fees have accumulated.

The contract holds SOLUM.

But transparency requires us to continue following that value.

Which bucket does it belong to?

How much is selected?

How much remains SOLUM?

How much is sold?

How much ETH arrives?

How much ETH supports liquidity?

How much reaches Treasury?

Who receives the LP tokens?

What parameters governed the operation?

Who could change those parameters?

Those questions turn:

> **automatic liquidity**

from a marketing phrase into an inspectable mechanism.

And they turn:

> **Treasury funding**

from a percentage on a website into a traceable economic pipeline.

That is what Tokenomics should do.

Not tell the user that money goes somewhere useful.

Show exactly:

> **where it came from,**
>
> **how it moved,**
>
> **what transformed it,**
>
> **where it arrived,**
>
> **and who still has authority over the process.**

---

→ **[Return to Tokenomics](/smart-contract/tokenomics/)**  
→ **[Return to Launch](/smart-contract/tokenomics/launch/)**  
→ **[Continue to Permissions](/smart-contract/tokenomics/permissions/)**
