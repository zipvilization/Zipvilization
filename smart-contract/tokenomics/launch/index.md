---
layout: default
title: Launch
parent: Tokenomics
grand_parent: Smart Contract
nav_order: 6
description: >
  Launch documents the exact activation and early-access mechanics of Solum:
  deployment, pre-trading restrictions, owner-controlled trading activation,
  the first 60-minute whitelist window, the 48-hour BUY protection period,
  the 60-minute per-wallet BUY cooldown, and the contract rules that remain
  active after launch protections expire.
permalink: /smart-contract/tokenomics/launch/
---

# Launch

Solum does not begin public trading at deployment.

Deployment creates the token and its initial state.

Public trading begins later through an explicit contract action.

From that moment, Solum enters a temporary launch regime designed to constrain the earliest BUY activity.

The sequence is exact:

**Deployment**

↓

**Pre-Trading**

↓

**Trading Enabled**

↓

**First 60 Minutes**

↓

**Minute 60 to Hour 48**

↓

**Post-Launch Rules**

These stages must not be confused.

> **Deployment is not Launch.**
>
> **Launch is not one instantaneous event.**
>
> **The first 48 hours contain their own contract rules.**

---

# Canonical Launch Snapshot

| Parameter | Contract rule |
|:----------|:--------------|
| Trading enabled at deployment | No |
| Trading activation authority | Owner |
| Activation function | `enableTrading()` |
| Trading activation count | Once |
| Launch timestamp | Set when trading is first enabled |
| Whitelist window | First 60 minutes after `launchTime` |
| Whitelist applies to | BUY only |
| BUY cooldown | 60 minutes per receiving wallet |
| Cooldown duration | First 48 hours after `launchTime` |
| Public BUY begins | After first 60 minutes |
| Special BUY rules end | 48 hours after `launchTime` |
| SELL subject to launch whitelist | No |
| TRANSFER subject to launch whitelist | No |
| SELL subject to launch BUY cooldown | No |
| TRANSFER subject to launch BUY cooldown | No |
| MAX_TX during Launch | Still independently applicable |
| Max Wallet during Launch | Still independently applicable |
| Fees during Launch | Still independently applicable |

This table describes the contract mechanism.

Other launch operations or off-chain procedures should not be inferred unless separately documented.

---

# Deployment comes first

When the contract is deployed:

- Solum exists,
- the initial Supply exists,
- the deployer receives the initial Supply,
- Router, Pair, and Treasury are configured,
- initial exemptions exist,
- Max Wallet's deployment-based clock begins,
- but public trading is not yet enabled.

The initial state is:

> **tradingEnabled = false**

This matters because deployment and market opening can occur at different times.

→ **[Explore Supply & Units](/smart-contract/tokenomics/supply-and-units/)**

---

# Deployment time

The contract records a deployment timestamp.

That timestamp is important for:

> **Max Wallet growth**

The initial 30B SOLUM Max Wallet remains fixed for 180 days from deployment.

This clock starts independently of public trading.

Therefore:

> **deploymentTime ≠ launchTime**

These timestamps have different functions.

→ **[Explore Limits](/smart-contract/tokenomics/limits/)**

---

# Pre-Trading

Before trading is enabled, ordinary token movement is restricted.

The contract requires:

> **sender is Fee Exempt**

or:

> **receiver is Fee Exempt**

for a transfer to proceed while `tradingEnabled == false`.

Therefore pre-trading is not equivalent to:

> **all transfers are impossible.**

Privileged/exempt operational transfers remain possible.

This distinction should remain explicit.

---

# Pre-Trading rule

The contract effectively applies:

> **If trading is OFF, at least one side of the transfer must be Fee Exempt.**

The initially Fee Exempt addresses are:

- deployer,
- contract itself,
- Treasury.

The owner can modify Fee Exempt state.

Therefore pre-launch movement capability depends partly on current exemption configuration.

→ **[Explore Permissions](/smart-contract/tokenomics/permissions/)**

---

# Pre-Trading does not create launchTime

Transfers that occur under the pre-trading exemption mechanism do not themselves begin the public launch clock.

`launchTime` is set by:

> **enableTrading()**

Therefore the launch windows are anchored to explicit trading activation.

Not to:

- deployment,
- first transfer,
- first liquidity action,
- first Holder,
- or first transaction visible on-chain.

The contract gives us a precise launch reference.

---

# enableTrading()

Public trading is activated by the owner through:

> **enableTrading()**

The function requires trading not to have already been enabled.

When executed successfully:

- `tradingEnabled` becomes true,
- `launchTime` is set if it is still zero,
- `LaunchStarted` is emitted,
- `TradingEnabled` is emitted.

The function cannot be used repeatedly to restart the launch period.

---

# Launch can only begin once

`enableTrading()` requires:

> **tradingEnabled == false**

Once enabled, the documented contract contains no mechanism in this function to turn ordinary trading back off and then restart Launch.

Also, `launchTime` is only set if it is zero.

Therefore:

> **the launch clock is intended to be established once.**

The first-hour whitelist and 48-hour BUY regime cannot simply be reset through repeated calls to `enableTrading()`.

---

# launchTime

At the moment trading is enabled:

> **launchTime = block.timestamp**

This timestamp becomes the reference for both special launch windows.

From `launchTime`:

**0–60 minutes**

Whitelist BUY phase.

**0–48 hours**

BUY cooldown phase.

After 48 hours:

special Launch BUY rules expire.

---

# Phase A — First 60 Minutes

For the first:

> **60 minutes after launchTime**

BUY transactions face two special conditions.

### Whitelist

The receiving wallet must be:

> **isWhitelist[to] == true**

### BUY cooldown

The receiving wallet can complete at most one BUY per:

> **60 minutes**

subject to the exact `lastBuyTime` logic.

Therefore Phase A is:

> **Whitelist-only BUY access + per-wallet BUY cooldown**

---

# The whitelist applies only to BUY

This is critical.

The whitelist gate is evaluated only when:

> **from == Pair**

That is the contract definition of BUY.

The whitelist does not create a universal restriction on:

- SELL,
- ordinary wallet-to-wallet TRANSFER.

Therefore it would be incorrect to describe the first hour as:

> **Only whitelisted wallets can transact.**

The accurate statement is:

> **Only whitelisted receiving wallets can BUY during the first 60 minutes.**

---

# The whitelist recipient

For a BUY:

- `from` is the Pair,
- `to` is the buying wallet.

The whitelist check evaluates:

> **isWhitelist[to]**

Therefore whitelist eligibility belongs to the receiving BUY address.

It is not a whitelist of sellers.

It is not a whitelist of transactions generally.

It is a BUY-access list for the first hour.

---

# Whitelist administration

The owner can manage whitelist state through functions for:

- one address,
- batches of addresses.

An address can be marked:

> **allowed**

or:

> **not allowed**

The contract emits a whitelist event when this state changes.

Therefore the whitelist is not hard-coded permanently into the contract at deployment.

It is owner-administered state.

→ **[Explore Permissions](/smart-contract/tokenomics/permissions/)**

---

# Whitelist and Founding Colonists

This technical mechanism gives Zipvilization a natural place to implement preferential founding access.

At blockchain level:

> **Whitelist**

At Zipvilization level, where canonically established:

> **Founding Colonist launch access**

But the distinction must remain explicit.

The Solidity contract does not contain the term:

> **Founding Colonist**

It contains whitelist state.

The Atlas provides the world interpretation.

Therefore:

> **Whitelist is the mechanism.**
>
> **Founding Colonist is the canonical human meaning we assign to eligible early support where explicitly defined.**

→ **[Explore Founding Colonists](/founding-colonists/)**

---

# Whitelist does not grant Solum

Being whitelisted does not:

- transfer SOLUM,
- reserve a guaranteed balance,
- create Territory,
- bypass all transaction limits,
- bypass all fees,
- create Zips,
- or create maturity.

It grants the technical ability to satisfy the first-hour whitelist condition for a BUY.

Every other applicable contract rule remains separate.

> **Eligibility is access.**
>
> **Eligibility is not ownership.**

---

# Whitelist is not Fee Exempt

This distinction is essential.

`isWhitelist`

and:

`isFeeExempt`

are different mappings.

A whitelisted address is not automatically Fee Exempt.

Therefore an eligible first-hour buyer can still pay the ordinary BUY fee unless another independent exemption applies.

Under the initial BUY fee:

> **1%**

is allocated between:

- Liquidity,
- Treasury.

→ **[Explore Fees](/smart-contract/tokenomics/fees/)**

---

# Whitelist is not Limit Exempt

Likewise:

`isWhitelist`

and:

`isLimitExempt`

are separate.

A whitelisted wallet does not automatically bypass:

- MAX_TX,
- Max Wallet.

Therefore a first-hour BUY may satisfy the whitelist condition and still fail a limit check.

> **Founding access does not mean unlimited access.**

This is one of the strongest contract-level protections around preferential launch participation.

---

# BUY cooldown

Throughout the first:

> **48 hours after launchTime**

BUY transactions are subject to a per-receiving-wallet cooldown.

The cooldown is:

> **60 minutes**

The relevant state is:

> **lastBuyTime[to]**

For a BUY, the contract checks the receiving wallet's previous recorded BUY time.

---

# First BUY

If:

> **lastBuyTime[to] == 0**

the wallet has no previously recorded launch-period BUY time.

The cooldown comparison is not required against an earlier purchase.

After the BUY passes the launch checks:

> **lastBuyTime[to] = block.timestamp**

That timestamp becomes the reference for the next BUY during the active launch period.

---

# Subsequent BUY

If the receiving wallet has already completed a BUY during the launch-rule period, the next BUY requires:

> **current block timestamp ≥ lastBuyTime + 60 minutes**

If less than 60 minutes have elapsed:

the BUY reverts with the cooldown condition.

Therefore:

> **one BUY per wallet per 60-minute interval**

is the useful human description during the active launch regime.

---

# Cooldown is per receiving wallet

The cooldown is recorded against:

> **to**

the BUY recipient.

It is not:

- global,
- Pair-wide,
- per transaction sender,
- or per Human identity.

Therefore different receiving wallets maintain independent cooldown state.

This is an address-level protection.

It does not prove one Human per wallet.

---

# Cooldown does not prevent multiple wallets

A person may potentially control multiple addresses.

The contract does not provide a unique-human identity layer.

Therefore the launch cooldown constrains:

> **wallet-level BUY frequency**

not:

> **person-level BUY frequency.**

This is an important limitation of the mechanism.

We should document it rather than overstate its effect.

---

# Phase B — Minute 60 to Hour 48

Once the first 60 minutes have elapsed:

> **the whitelist requirement ends.**

Public BUY access becomes possible.

But the 60-minute per-wallet BUY cooldown remains active until the complete 48-hour launch period ends.

Therefore Phase B is:

> **Public BUY access + per-wallet 60-minute BUY cooldown**

This phase lasts from the end of the whitelist window until the end of the 48-hour BUY-rules window.

---

# Exact boundary of the whitelist window

The whitelist helper returns active while:

> **block.timestamp < launchTime + 60 minutes**

Therefore at or after the exact 60-minute boundary:

the whitelist gate is no longer active.

This is a strict timestamp condition.

An exact technical implementation should use contract time rather than rounded wall-clock descriptions.

---

# Exact boundary of the 48-hour period

The launch BUY rules remain active while:

> **block.timestamp < launchTime + 48 hours**

At or after the exact 48-hour boundary:

the special BUY launch logic is no longer active.

That means:

- no launch whitelist check,
- no launch BUY cooldown check,
- no new `lastBuyTime` update through that launch block.

Other contract rules continue independently.

---

# Phase C — After 48 Hours

After the 48-hour launch period ends, ordinary BUY activity no longer uses the special launch whitelist/cooldown logic.

But this does not mean:

> **all restrictions disappear.**

The following can still matter:

- current BUY fee,
- MAX_TX,
- current Max Wallet,
- Fee Exempt state,
- Limit Exempt state,
- balance,
- allowance where applicable,
- Pair configuration,
- SwapBack behavior,
- and ordinary ERC-20 requirements.

Launch protections expire.

The contract does not become ruleless.

---

# SELL during the first 48 hours

SELL is defined as:

> **to == Pair**

The special launch block is conditional on:

> **isBuy**

Therefore SELL is not subject to:

- first-hour whitelist,
- launch BUY cooldown.

It remains subject to other applicable contract mechanics.

Under the initial non-exempt configuration, that includes the SELL fee:

> **10%**

with its corresponding Burn, Reflection, Liquidity, and Treasury allocations.

---

# TRANSFER during the first 48 hours

Ordinary wallet-to-wallet TRANSFER is also outside the special BUY launch logic.

Therefore TRANSFER is not subject to:

- first-hour whitelist,
- launch BUY cooldown.

It remains subject to other applicable mechanics such as:

- MAX_TX,
- Max Wallet on the receiving side,
- fees,
- exemptions.

Under the initial non-exempt configuration, the TRANSFER fee is:

> **5%**

---

# Launch protections are BUY-specific by design

This distinction should appear everywhere we describe Launch.

Incorrect:

> **There is a 48-hour transaction cooldown.**

Correct:

> **There is a 60-minute per-wallet BUY cooldown during the first 48 hours after trading is enabled.**

Incorrect:

> **Only whitelisted wallets can use Solum for the first hour.**

Correct:

> **Only whitelisted receiving wallets can BUY from the Pair during the first 60 minutes.**

Precision matters.

---

# Launch and MAX_TX

The launch whitelist does not override MAX_TX.

For ordinary non-exempt limit paths:

> **MAX_TX = 10,000,000,000 SOLUM**

A whitelisted BUY above the applicable MAX_TX condition can still fail.

Therefore first-hour preferential access remains bounded by transaction-size rules unless exemption state changes that result.

→ **[Explore Limits](/smart-contract/tokenomics/limits/)**

---

# Launch and Max Wallet

Likewise, whitelist eligibility does not override Max Wallet.

The initial Max Wallet is:

> **30,000,000,000 SOLUM**

subject to the deployment-time progression described in Limits.

The receiving BUY wallet can still fail Max Wallet if:

> **current balance + gross incoming amount**

exceeds the current limit under applicable conditions.

---

# Launch and deployment timing

Because Max Wallet's 180-day period starts at deployment rather than `launchTime`, the Max Wallet that exists at Launch depends on how much time passed between:

> **deployment**

and:

> **enableTrading().**

If Launch occurs shortly after deployment:

Max Wallet will still be 30B.

If Launch were delayed beyond the initial growth period:

the time-derived Max Wallet could already be higher.

The contract does not reset Max Wallet progression when trading begins.

This is important for exact launch preparation.

---

# Launch and fees

The launch mechanism does not define special BUY fee percentages.

BUY fees follow the ordinary current BUY-fee state.

Initially:

> **BUY fee = 1%**

with:

- 0.5% Liquidity,
- 0.5% Treasury.

Therefore first-hour whitelisted access does not imply:

> **fee-free buying.**

Fee exemption is a separate contract state.

---

# Launch and Burn

The initial BUY fee contains:

> **0% Burn**

Therefore first-hour and first-48-hour BUY activity does not directly produce Burn through the BUY fee.

SELL and TRANSFER remain different.

A participant buying during Launch and later selling or transferring may interact with Burn according to the current applicable fees.

---

# Launch and Reflection

Initial BUY also contains:

> **0% Reflection**

Therefore BUY cooldown is not a Reflection-distribution mechanism.

The cooldown constrains frequency.

The fee architecture determines economic allocation.

Again, separate mechanisms.

---

# Launch and SwapBack

SwapBack requires:

> **tradingEnabled == true**

among its conditions.

Therefore SwapBack cannot execute through its normal trigger path before trading is enabled.

Once trading is active, qualifying SELL activity can potentially trigger SwapBack when all other SwapBack conditions are satisfied.

Launch BUY rules do not disable SwapBack globally.

→ **[Explore SwapBack](/smart-contract/tokenomics/swapback/)**

---

# Trading activation is owner-controlled

The owner decides when to execute:

> **enableTrading()**

This is a real administrative authority.

The contract does not automatically begin public trading at a predetermined timestamp.

Therefore before Launch, the owner controls the activation moment.

Once activated, however, the launch timing rules derive deterministically from `launchTime`.

> **Human authority selects the start.**
>
> **Contract logic governs the timed launch phases afterward.**

---

# The owner cannot call enableTrading twice

Once trading is enabled:

the function's guard prevents another successful activation.

This limits one important administrative power.

The owner selects the launch moment once.

The owner does not have an ordinary mechanism in this function to repeatedly restart the whitelist phase.

That distinction strengthens predictability after activation.

---

# The whitelist remains stored after its window

The mapping:

> **isWhitelist**

does not need to be automatically erased when the first 60 minutes end.

The important point is that the whitelist gate stops being consulted after the whitelist window expires.

Therefore an address may remain marked `true` in the mapping while no longer receiving any launch whitelist advantage.

> **Stored eligibility state and active whitelist effect are different concepts.**

---

# lastBuyTime can remain stored after 48 hours

Likewise, historical `lastBuyTime` values can remain in contract storage.

After the 48-hour launch period:

the special launch logic stops consulting them for BUY cooldown enforcement.

Therefore a stored timestamp does not imply that the cooldown remains active forever.

State must be interpreted together with the rule that uses it.

---

# Launch and Fair Access

Launch is one component of Fair Access.

The contract combines several independent protections:

**First 60 minutes**

preferential whitelist access.

**First 48 hours**

per-wallet BUY frequency limitation.

**MAX_TX**

transaction-size constraint.

**Max Wallet**

concentration constraint.

Together they create resistance to immediate capture.

But they do not guarantee equal distribution.

→ **[Explore Fair Access](/smart-contract/fair-access/)**

---

# Launch does not solve Sybil behavior

Whitelist and cooldown operate on addresses.

MAX_TX and Max Wallet also operate primarily through addresses and exemption state.

The contract does not prove that:

> **one address = one person**

Therefore launch protections should be described as:

> **address-level constraints**

not:

> **guaranteed unique-human allocation.**

This limitation should remain visible.

---

# Founding Colonists

The first-hour whitelist is especially important to the Founding Colonist architecture.

Before Launch, people may support Zipvilization while public colonization is not technically available.

The whitelist provides a contract mechanism through which selected addresses can receive first-hour BUY access.

The conceptual sequence is:

**Early support**

↓

**Founding Colonist recognition**

↓

**address included in launch whitelist under the canonical process**

↓

**Trading begins**

↓

**first-hour preferential BUY opportunity**

↓

**actual blockchain acquisition if a valid BUY succeeds**

↓

**Holder**

↓

**Colonist interpretation**

Recognition does not create the final blockchain state.

The successful transaction does.

→ **[Explore Founding Colonists](/founding-colonists/)**

---

# Preferential opportunity has a hard temporal boundary

The first-hour whitelist advantage ends after:

> **60 minutes**

from `launchTime`.

The contract does not give whitelisted wallets preferential BUY access forever.

After the whitelist window:

public BUY access is permitted under the remaining applicable rules.

This gives Founding access an objectively bounded on-chain window.

> **Preference has a beginning.**
>
> **Preference has an end.**

---

# The contract does not limit whitelist size

An important transparency point:

the Solidity mechanism allows the owner to add individual addresses or batches to the whitelist.

The contract itself does not, from this mechanism alone, impose a fixed numerical maximum number of whitelisted addresses.

Therefore if Zipvilization defines:

> **a limited number of Founding Colonist places**

that numerical limit must come from another explicit canonical or operational rule unless separately enforced elsewhere.

We should not claim that Solidity itself enforces a founding-seat maximum if it does not.

This distinction is crucial.

---

# The contract does enforce the time limit

Unlike the number of whitelist entries, the preferential time window is directly enforced by contract logic:

> **60 minutes after launchTime**

for whitelist-only BUY access.

Therefore we can say precisely:

> **The first-hour preference is on-chain time-bounded.**

Any participant-count limitation needs its own source of authority.

---

# Launch preparation and transparency

Before enabling trading, a transparent launch process should allow participants to verify relevant initial state such as:

- contract address,
- network,
- Pair,
- Router,
- Treasury,
- current fees,
- MAX_TX,
- current Max Wallet,
- whitelist status where appropriate,
- Fee Exempt addresses,
- Limit Exempt addresses,
- SwapBack configuration,
- and current owner.

The contract provides many of these states publicly.

Publication and tooling can make them easier to inspect.

---

# Launch cannot be understood from price alone

Token Launch is not simply:

> **the moment SOLUM gets a market price.**

Contractually, Launch is the activation of trading and the beginning of a defined timed rule set.

Price discovery may occur around that event.

But price is a market outcome.

The launch mechanism is defined by:

- `enableTrading()`,
- `launchTime`,
- whitelist window,
- cooldown,
- fees,
- limits,
- exemptions.

This documentation concerns the mechanism.

---

# Launch and the World

Inside Zipvilization, Launch marks something larger.

Before Launch:

the finite substrate exists technically.

But ordinary public colonization has not begun.

At Launch:

participants can begin acquiring SOLUM through public market interaction under the contract rules.

That creates the conditions for:

- Holders,
- Colonist interpretation,
- controlled territorial substrate,
- Territory,
- future biological development.

The Smart Contract does not itself create civilization at `launchTime`.

It opens the technical door.

---

# Genesis and Launch are related but not identical concepts

Zipvilization may use:

> **Genesis**

as a broader conceptual description of the world's beginning.

The contract uses:

> **launchTime**

for a precise timestamp established when trading is enabled.

An AI should not automatically assume every conceptual Genesis milestone occurs in the exact same block as `launchTime` unless the canonical architecture explicitly says so.

Technical and world chronology should be connected deliberately.

---

# Launch state should be observable

SolumTools can eventually expose:

- trading enabled status,
- launch timestamp,
- current launch phase,
- whether whitelist gate remains active,
- whether BUY cooldown remains active,
- an address's whitelist status,
- last BUY timestamp,
- next eligible BUY time during the active period,
- current MAX_TX,
- current Max Wallet.

This can turn a relatively complex launch rule set into a simple user experience.

→ **[Explore SolumTools](/world/solumtools/)**

---

# A Human should see a simple answer

During Launch, a user should eventually be able to ask:

> **Can I BUY now?**

A good interface can answer using contract state.

For example:

**First hour**

- Whitelisted: Yes / No
- Cooldown ready: Yes / No
- Maximum transaction: current applicable value
- Wallet capacity: current applicable value
- Current BUY fee: current value

After the first hour:

- Whitelist no longer required
- Cooldown status remains relevant until hour 48

After hour 48:

- Launch BUY restrictions ended

The underlying mechanics can be complex.

The UX does not need to be.

---

# Artificial Intelligence rules for Launch

When answering a Launch question, AI should determine:

### 1. Was trading enabled?

If not, public Launch has not started.

### 2. What is `launchTime`?

Do not substitute deployment time.

### 3. How much time has elapsed since `launchTime`?

This determines Launch phase.

### 4. Is the transaction actually a BUY?

Whitelist and launch cooldown are BUY-only.

### 5. During the first hour, is the receiver whitelisted?

Use current contract state.

### 6. During the first 48 hours, when was the receiver's last BUY?

Use `lastBuyTime`.

### 7. Do MAX_TX and Max Wallet permit the gross amount?

Launch eligibility does not override Limits.

### 8. Does Fee Exempt or Limit Exempt state alter ordinary processing?

Permissions are separate.

### 9. What is the current BUY fee?

Initial 1% may have been reduced later.

This sequence produces a contract-grounded answer.

---

# What AI must not say

AI should not say:

> **Launch begins at deployment.**

Incorrect.

It begins when trading is enabled.

It should not say:

> **The whitelist lasts 48 hours.**

Incorrect.

Whitelist-only BUY access lasts 60 minutes.

It should not say:

> **Only whitelisted wallets can transact during the first hour.**

Incorrect.

The whitelist rule applies to BUY recipients.

It should not say:

> **There is one transaction per hour for 48 hours.**

Incorrect.

The cooldown applies to BUY per receiving wallet.

It should not say:

> **Founding Colonists are automatically Fee Exempt or Limit Exempt.**

Not established by whitelist membership.

It should not say:

> **The contract itself limits the number of Founding Colonists.**

Not through the whitelist mechanism shown here.

It should not say:

> **After 48 hours all limits disappear.**

Incorrect.

Only the special Launch BUY rules expire.

---

# Launch phases in one view

## Phase 0 — Deployment / Pre-Trading

**Trading:** OFF

Ordinary movement requires:

> sender or receiver Fee Exempt.

`launchTime` has not yet begun.

Max Wallet's deployment-based clock is already running.

---

## Phase 1 — First 60 Minutes

Begins when:

> **enableTrading() succeeds**

Conditions for BUY include:

- recipient must be whitelisted,
- 60-minute per-wallet BUY cooldown,
- MAX_TX where applicable,
- Max Wallet where applicable,
- current fee behavior,
- ordinary contract requirements.

SELL and TRANSFER are not subject to the whitelist/cooldown block.

---

## Phase 2 — Minute 60 to Hour 48

BUY becomes public.

Whitelist no longer required.

BUY still has:

> **60-minute per-wallet cooldown**

plus ordinary applicable rules.

---

## Phase 3 — After 48 Hours

Special Launch BUY rules expire.

No launch whitelist gate.

No launch BUY cooldown.

Ordinary contract architecture remains:

- fees,
- MAX_TX,
- Max Wallet,
- exemptions,
- SwapBack,
- and other active rules.

---

# Follow Launch

### Return to Tokenomics

→ **[Tokenomics](/smart-contract/tokenomics/)**

### Understand the Supply that exists before Launch

→ **[Supply & Units](/smart-contract/tokenomics/supply-and-units/)**

### Understand BUY economics

→ **[Fees](/smart-contract/tokenomics/fees/)**

### Understand transaction and wallet limits

→ **[Limits](/smart-contract/tokenomics/limits/)**

### Understand fee and limit exemptions

→ **[Permissions](/smart-contract/tokenomics/permissions/)**

### Understand automated fee processing after trading begins

→ **[SwapBack](/smart-contract/tokenomics/swapback/)**

### Understand Fair Access

→ **[Fair Access](/smart-contract/fair-access/)**

### Understand Founding access

→ **[Founding Colonists](/founding-colonists/)**

### Inspect implementation

→ **[Repository](/repository/)**

---

# The first hour

Before Launch, Solum exists.

The finite world exists.

But ordinary public participation has not started.

Then one transaction changes the state:

> **enableTrading()**

A timestamp is written.

The clock begins.

For 60 minutes, BUY access belongs only to whitelisted wallets.

Even they cannot BUY continuously.

The same receiving wallet must wait an hour before another BUY.

After 60 minutes, the gate opens.

Everyone can BUY under the ordinary applicable conditions.

But the cooldown remains.

For another 47 hours, the contract continues slowing repeated BUY accumulation wallet by wallet.

Then, at 48 hours, the special launch machinery steps away.

No reset.

No second Genesis.

No permanent whitelist privilege.

The world keeps the distribution produced during those first hours and moves forward from there.

That is the launch architecture.

> **The owner chooses when the door opens.**
>
> **The contract controls the first 48 hours after it does.**
>
> **Then history takes over.**

---

→ **[Return to Tokenomics](/smart-contract/tokenomics/)**  
→ **[Return to Limits](/smart-contract/tokenomics/limits/)**  
→ **[Continue to SwapBack](/smart-contract/tokenomics/swapback/)**
