---
layout: default
title: Limits
parent: Tokenomics
grand_parent: Smart Contract
nav_order: 5
description: >
  Limits documents Solum's anti-concentration mechanics: the fixed 10 billion
  SOLUM MAX_TX, the initial 30 billion SOLUM Max Wallet, its 180-day protection
  period, 10% compounded weekly growth, exemption rules, and the exact contract
  conditions under which these limits are enforced.
permalink: /smart-contract/tokenomics/limits/
---

# Limits

Solum is finite.

The contract therefore places explicit boundaries on how much SOLUM can move and how much can accumulate under ordinary conditions.

There are two primary mechanisms:

> **MAX_TX**

and:

> **Max Wallet**

They solve different problems.

**MAX_TX** limits the size of an individual transaction.

**Max Wallet** limits the balance a receiving wallet can reach under the applicable contract conditions.

Together, they form part of the Fair Access architecture.

But they are not permanent equality rules.

They are technical constraints.

---

# Canonical snapshot

| Parameter | Contract rule |
|:----------|--------------:|
| MAX_TX | 10,000,000,000 SOLUM |
| MAX_TX relative to initial Supply | 0.01% |
| Initial Max Wallet | 30,000,000,000 SOLUM |
| Initial Max Wallet relative to initial Supply | 0.03% |
| Initial Max Wallet period | 180 days from deployment |
| Growth after initial period | +10% per complete week, compounded |
| Growth calculation | Automatic |
| Growth authority | Contract time logic |
| Growth cutoff | More than 520 complete weeks after delay |
| State after cutoff | Effectively non-restrictive |
| Limit exemptions | Configurable by owner |

These are contract rules.

They do not depend on visual Territory or narrative interpretation.

---

# MAX_TX

The contract defines:

> **MAX_TX = 10,000,000,000 SOLUM**

or:

> **10 billion SOLUM**

The value is declared as a contract constant.

The documented contract contains no setter for changing it.

Therefore:

> **MAX_TX is fixed in this implementation.**

Relative to the original 100 trillion SOLUM Supply:

> **MAX_TX = 0.01% of initial Supply**

---

# What MAX_TX limits

MAX_TX answers:

> **How much SOLUM can this transaction move under ordinary limit conditions?**

The contract checks the gross transaction amount.

The relevant rule is:

> **transaction amount ≤ 10 billion SOLUM**

when neither sender nor receiver is Limit Exempt.

The check happens before fee allocation.

Therefore MAX_TX applies to:

> **gross transaction amount**

not:

> **net amount after fees.**

---

# MAX_TX example

Consider an ordinary transaction of:

> **9,000,000,000 SOLUM**

where neither side is Limit Exempt.

It is below:

> **10,000,000,000 SOLUM**

and therefore satisfies MAX_TX.

Now consider:

> **10,000,000,001 SOLUM**

Under the same non-exempt conditions, the transaction exceeds MAX_TX and fails the MAX_TX check.

The fee that might otherwise apply does not rescue the transaction.

The contract checks the gross amount.

---

# MAX_TX applies across transaction types

The MAX_TX check occurs before the contract classifies ordinary fee behavior as BUY, SELL, or TRANSFER.

Therefore, where neither side is Limit Exempt, MAX_TX can constrain:

- BUY,
- SELL,
- TRANSFER.

Its function is independent of the applicable fee schedule.

This is important.

> **Transaction type determines economic fee behavior.**
>
> **MAX_TX constrains transaction size.**

---

# Limit exemption changes MAX_TX behavior

MAX_TX is not enforced when either:

> **sender is Limit Exempt**

or:

> **receiver is Limit Exempt**

The relevant contract condition requires both sides to be non-exempt before enforcing MAX_TX.

Therefore an accurate answer to:

> **Can this address move more than 10B SOLUM?**

cannot be answered from MAX_TX alone.

Current exemption state also matters.

→ **[Explore Permissions](/smart-contract/tokenomics/permissions/)**

---

# Initial Limit Exempt addresses

The contract initially marks the following addresses as Limit Exempt:

- deployer,
- contract itself,
- Treasury,
- Router,
- Pair.

The owner can later modify Limit Exempt status for addresses.

Therefore the initial list is not necessarily the current list forever.

A live analysis should read current state.

---

# Max Wallet

Max Wallet solves a different problem.

Instead of limiting the size of one transaction, it constrains the balance of the receiving wallet under its applicable conditions.

The initial value is:

> **30,000,000,000 SOLUM**

or:

> **30 billion SOLUM**

Relative to the initial Supply:

> **0.03%**

Unlike MAX_TX, this value does not remain fixed forever.

---

# The first 180 days

For the first:

> **180 days after contract deployment**

Max Wallet remains:

> **30 billion SOLUM**

This period is calculated from:

> **deployment time**

not:

> **trading launch time.**

That distinction matters.

The 180-day clock begins when the contract is deployed.

It does not wait for `enableTrading()`.

---

# Deployment time is not Launch time

Solum uses different clocks for different mechanisms.

**Max Wallet growth**

uses:

> deployment time.

**Launch protection**

uses:

> launchTime, set when trading is enabled.

Therefore:

> **180 days after deployment**

must not be confused with:

> **180 days after Token Launch.**

If trading begins some time after deployment, the remaining fixed-Max-Wallet period after launch will be correspondingly shorter.

This is a contract fact.

---

# Max Wallet growth

After the initial 180-day delay, Max Wallet begins growing automatically.

The growth factor is:

> **110,000 / 100,000**

which corresponds to:

> **1.10**

Therefore every complete week increases the previous limit by:

> **10%**

and the increase is compounded.

Conceptually:

> **Max Wallet(n) = 30B × 1.10ⁿ**

where `n` is the number of complete weeks elapsed after the initial 180-day delay.

The actual Solidity calculation uses integer arithmetic.

---

# Complete weeks only

The growth does not accrue continuously.

The contract calculates:

> **complete weeks elapsed**

after the 180-day delay.

Therefore the limit changes in weekly steps.

During a partial week, the current Max Wallet remains at the value corresponding to the previous complete week.

Conceptually:

**Day 180**

30.00B

↓

**one complete additional week**

33.00B

↓

**another complete week**

36.30B

and so on.

---

# Initial Max Wallet progression

The first values are:

| Complete weeks after day 180 | Max Wallet |
|-----------------------------:|-----------:|
| 0 | 30.000B SOLUM |
| 1 | 33.000B SOLUM |
| 2 | 36.300B SOLUM |
| 3 | 39.930B SOLUM |
| 4 | 43.923B SOLUM |
| 5 | 48.3153B SOLUM |
| 6 | 53.14683B SOLUM |

Each new value is based on the previous value.

This is compound growth.

Not linear growth.

---

# Compound, not +3B per week

This distinction is important.

The contract does not add:

> **3 billion SOLUM every week**

forever.

Instead it multiplies the previous limit by:

> **1.10**

Therefore the weekly absolute increase itself grows.

For example:

Week 0 → Week 1:

> +3.00B

Week 1 → Week 2:

> +3.30B

Week 2 → Week 3:

> +3.63B

The percentage is constant.

The absolute increase is not.

---

# The contract calculates the progression automatically

Max Wallet growth does not require the owner to execute weekly updates.

The current value is derived whenever the contract calls its Max Wallet calculation.

The inputs are:

- deployment time,
- 180-day delay,
- complete weeks elapsed,
- fixed 10% weekly multiplier.

Therefore:

> **Max Wallet relaxation is time-driven, not owner-driven.**

This is an important distinction from configurable permissions elsewhere in the contract.

---

# Owner cannot set Max Wallet directly

The documented contract contains no ordinary setter for assigning an arbitrary Max Wallet value.

The growth formula determines the current limit.

The owner can still affect whether a specific address is subject to the limit through:

> **Limit Exempt status**

but does not directly choose the global time-derived Max Wallet number.

Therefore we should separate:

**global Max Wallet formula**

from:

**address exemption authority.**

---

# More than 520 weeks

The contract includes a long-term cutoff to avoid an excessive loop far in the future.

After the 180-day growth delay, it calculates complete weeks elapsed.

If:

> **weeksElapsed > 520**

the function returns:

> **maximum uint256 value**

instead of continuing compound calculation.

In practical SOLUM terms, that makes Max Wallet effectively non-restrictive.

---

# The 520-week boundary precisely

The contract condition is:

> **greater than 520 weeks**

not:

> **greater than or equal to 520 weeks.**

Therefore:

- at exactly 520 complete weeks after the 180-day delay, the contract still computes the compounded Max Wallet;
- once the elapsed complete-week count becomes 521 or greater, it returns the maximum `uint256` value.

This distinction matters for exact implementation documentation.

---

# Why the cutoff exists technically

The contract comment explains the cutoff as protection against:

> **pathological gas far in the future**

because the Max Wallet function compounds the value through a loop for each elapsed week.

Instead of allowing that loop to grow indefinitely, the contract eventually returns an effectively unlimited value.

Therefore the long-term disappearance of the restriction is partly a computational design choice encoded directly into the contract.

---

# Max Wallet check

For a receiving address subject to the rule, the contract calculates:

> **current recipient balance + gross transaction amount**

and requires the result to remain below or equal to the current Max Wallet.

This is a very important implementation detail.

The formula is conceptually:

> **New Balance Check = balanceOf(receiver) + gross transaction amount**

The contract does not use:

> **balanceOf(receiver) + net amount after fees**

for this check.

---

# Gross amount makes the check conservative

Suppose:

- current wallet balance = 29.5B SOLUM,
- current Max Wallet = 30B SOLUM,
- incoming gross transaction = 0.6B SOLUM,
- transaction would incur a fee.

The contract checks:

> **29.5B + 0.6B = 30.1B**

That exceeds Max Wallet.

The transaction fails the wallet-limit check.

It does not matter that the recipient might have received less than 0.6B after fees.

The gross amount is used.

---

# Max Wallet applies on receive

The wallet-limit rule concerns the receiving side.

It does not directly say:

> **a wallet cannot send if its existing balance exceeds Max Wallet.**

Instead, it checks whether a relevant receiving operation would push the destination above the current limit according to the gross amount calculation.

This distinction matters once Max Wallet changes over time or exemption status changes.

---

# Pair and Router are explicitly ignored for wallet-limit receive checks

The contract's wallet-limit logic does not apply the Max Wallet receive check when the recipient is:

- Pair,
- Router.

It also does not apply when the recipient is Limit Exempt.

This is separate from the MAX_TX logic.

Therefore Max Wallet and MAX_TX have similar goals but different exemption conditions in execution.

---

# Selling is not blocked by Pair Max Wallet

Because the Pair is excluded from the Max Wallet receive check, a SELL is not prevented merely because sending SOLUM to the Pair would make the Pair's balance exceed an ordinary wallet limit.

This is necessary for market operation.

The Pair remains separately Limit Exempt initially as well.

---

# Max Wallet can constrain BUY

During an ordinary BUY:

- Pair sends SOLUM,
- user receives SOLUM.

If the receiving user is not Limit Exempt, the Max Wallet rule can apply.

Therefore a BUY that satisfies:

- whitelist rules,
- cooldown,
- MAX_TX,

can still fail if the gross incoming amount would push the recipient above current Max Wallet.

Launch protection and Max Wallet are separate layers.

→ **[Explore Launch](/smart-contract/tokenomics/launch/)**

---

# Max Wallet can constrain TRANSFER

During a wallet-to-wallet TRANSFER:

the receiving wallet is subject to Max Wallet where the applicable exemption conditions do not remove the check.

Therefore direct redistribution can also fail if the destination would exceed current Max Wallet.

Again, the check uses the gross transaction amount.

---

# MAX_TX and Max Wallet can apply simultaneously

Consider an ordinary non-exempt BUY.

The transaction may need to satisfy both:

> **Gross transaction amount ≤ MAX_TX**

and:

> **Recipient current balance + gross transaction amount ≤ current Max Wallet**

These conditions answer different questions.

A transaction can satisfy one and fail the other.

---

# Example: passes MAX_TX, fails Max Wallet

Suppose:

- MAX_TX = 10B,
- current Max Wallet = 30B,
- recipient balance = 25B,
- gross BUY = 8B.

MAX_TX:

> **8B ≤ 10B**

Pass.

Max Wallet:

> **25B + 8B = 33B**

Fail.

Therefore the transaction cannot proceed under ordinary limit conditions.

---

# Example: passes Max Wallet, fails MAX_TX

Suppose:

- MAX_TX = 10B,
- current Max Wallet = 30B,
- recipient balance = 0,
- gross BUY = 11B.

Max Wallet:

> **0 + 11B ≤ 30B**

would fit.

MAX_TX:

> **11B > 10B**

fails.

The transaction cannot proceed.

---

# Limits and fees are independent

A fee does not change the gross amount used for MAX_TX.

A fee also does not reduce the gross amount used by the Max Wallet check.

Therefore the correct conceptual sequence is:

**Gross transaction requested**

↓

**applicable limit checks**

↓

**transaction classification and other rules**

↓

**fee processing**

↓

**resulting balances and allocations**

The exact Solidity execution order remains authoritative.

---

# Limits and Reflection

Max Wallet uses:

> `balanceOf(receiver)`

for the receiver's current balance.

Because `balanceOf()` already reflects the current Reflection rate, Reflection can indirectly influence how close a wallet is to its Max Wallet threshold.

This is important.

A wallet can experience effective balance growth through Reflection even without receiving an ordinary direct transfer.

Therefore its remaining room under Max Wallet can change.

→ **[Explore Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

---

# Reflection does not exempt a wallet from limits

A balance increasing through Reflection does not alter whether the wallet is Limit Exempt.

Exemption is explicit contract state.

Balance and permission are separate.

If a later incoming transaction is evaluated, the contract uses the current reflected `balanceOf()` plus the gross incoming amount.

---

# A wallet could already be above the current limit

Because balances can change through Reflection, because exemptions can change, and because the limit itself evolves over time, unusual states can theoretically exist.

The Max Wallet check governs relevant incoming transfers.

It is not a generic function that continuously forces every balance below the limit.

Therefore:

> **Max Wallet is a transaction constraint, not an automatic balance confiscation mechanism.**

This distinction matters for accurate AI reasoning.

---

# Limit Exempt

The owner can mark an address:

> **Limit Exempt**

or remove that status.

Limit Exempt affects the anti-whale enforcement paths.

It does not inherently make the address Fee Exempt.

The two mappings are separate.

→ **[Explore Permissions](/smart-contract/tokenomics/permissions/)**

---

# Exemption authority matters

The global limits can be strict while individual addresses are exempt.

Therefore transparency requires both pieces of information:

> **What are the limits?**

and:

> **Who is exempt from them?**

Publishing MAX_TX and Max Wallet without publishing or exposing current exemptions would provide an incomplete picture of concentration controls.

---

# Fair Access is not just two numbers

MAX_TX and Max Wallet are central to Fair Access.

But Fair Access also includes:

- launch whitelist,
- BUY cooldown,
- pre-trading restrictions,
- exemptions,
- and the temporal relaxation of Max Wallet.

The complete system therefore protects distribution through several interacting constraints.

→ **[Explore Fair Access](/smart-contract/fair-access/)**

---

# The protection is intentionally asymmetric over time

At deployment:

> **Max Wallet = 30B SOLUM**

and remains there for 180 days.

Later:

it grows automatically.

Eventually:

it becomes effectively non-restrictive.

MAX_TX, however, remains fixed at:

> **10B SOLUM**

for ordinary non-exempt paths.

This creates two different long-term behaviors.

**Max Wallet**

relaxes with time.

**MAX_TX**

does not.

---

# Why this matters economically

At the beginning, one ordinary non-exempt wallet cannot receive enough SOLUM to exceed:

> **30B SOLUM**

under the wallet check.

And one ordinary non-exempt transaction cannot move more than:

> **10B SOLUM**

under MAX_TX.

That means filling the initial Max Wallet from zero would require at least several permitted operations rather than one transaction, subject to all other applicable rules.

During Launch, BUY cooldown adds another temporal constraint.

The early distribution process therefore combines:

**transaction size**

+

**wallet concentration**

+

**time**

rather than relying on one anti-whale rule alone.

---

# Limits do not guarantee one Human per wallet

This is important.

Blockchain limits operate on addresses.

They do not prove unique Human identity.

One person may control multiple wallets.

Several people may coordinate.

Smart contracts may interact.

Therefore MAX_TX and Max Wallet constrain:

> **address-level behavior**

not:

> **guaranteed person-level ownership.**

Fair Access reduces some concentration paths.

It does not solve Sybil identity by itself.

---

# Limits do not guarantee decentralization

The same principle follows.

A 0.03% initial Max Wallet does not guarantee that the world becomes broadly distributed.

Participants may use multiple addresses.

Markets may consolidate later.

Exemptions exist.

Large structures are canonically possible.

Therefore the correct claim is:

> **The contract imposes explicit anti-concentration constraints.**

Not:

> **The contract guarantees decentralization.**

Metrics must tell us what distribution actually becomes.

→ **[Explore Metrics](/metrics/)**

---

# Large Territories remain possible

The existence of anti-whale limits does not mean Zipvilization rejects large territorial structures.

Canonical Territory includes:

- Farm,
- City,
- State,
- Kingdom.

The contract protects access conditions.

The world allows growth.

Those are compatible.

A large Territory emerging through valid accumulated participation and time is different from unrestricted early capture.

→ **[Explore Territories](/world/territories/)**

---

# Limits do not create maturity

Acquiring more SOLUM can increase territorial capacity.

But the contract limits concern token movement and balances.

They do not determine:

- Zip generation,
- biological cycles,
- maturity,
- historical age,
- political authority.

Therefore:

> **Max Wallet is not a maturity rule.**

And:

> **MAX_TX is not a territorial-development rule.**

They belong to Tokenomics.

---

# Limits and Launch

The first 48 hours introduce additional BUY-specific rules.

During Launch, a BUY may need to satisfy:

- trading enabled,
- whitelist during the first hour,
- BUY cooldown during the first 48 hours,
- MAX_TX,
- Max Wallet,
- balance and transfer conditions,
- fee rules.

A participant who satisfies the whitelist requirement can still fail another limit.

Founding access does not bypass the whole contract unless explicit exemption state causes a specific rule not to apply.

→ **[Explore Launch](/smart-contract/tokenomics/launch/)**

---

# Founding Colonists and limits

The technical whitelist gives eligible addresses early BUY access during the first hour.

It does not inherently grant:

- unlimited transaction size,
- unlimited wallet capacity,
- fee exemption,
- limit exemption,
- or accelerated maturity.

Those would require separate contract state.

Therefore:

> **Whitelist eligibility ≠ Limit Exempt**

and:

> **Founding recognition ≠ unlimited access**

This distinction protects the integrity of the founding mechanism.

→ **[Explore Founding Colonists](/founding-colonists/)**

---

# Limits and current Supply

MAX_TX and initial Max Wallet are defined as absolute SOLUM quantities.

Their percentages of:

> **0.01%**

and:

> **0.03%**

are percentages of the original 100T Supply.

Because Burn can reduce current `totalSupply()`, the same absolute limits can represent a slightly larger percentage of current Supply over time.

Therefore an AI should distinguish:

> **percentage of original Supply**

from:

> **percentage of current Supply.**

The contract limits themselves remain denominated in SOLUM.

---

# Max Wallet can eventually exceed current Supply

Because Max Wallet compounds automatically and eventually becomes effectively unlimited, it is not capped at current token Supply.

That is not a logical problem.

A limit larger than all possible balances simply ceases to constrain practical behavior.

The function represents an upper bound.

It does not require the bound itself to remain economically reachable.

---

# MAX_TX remains meaningful even when Max Wallet disappears

When Max Wallet eventually becomes effectively non-restrictive, MAX_TX remains:

> **10B SOLUM**

for ordinary transactions where neither side is Limit Exempt.

Therefore the two mechanisms do not disappear together.

Long-term ordinary transaction-size constraints remain unless another canonical deployment or architecture changes the underlying contract reality.

---

# Limits and Security

Anti-whale mechanisms create their own security questions.

Important issues include:

- who can create exemptions,
- whether exemptions are visible,
- whether multiple wallets bypass intended concentration protection,
- whether the Pair and Router are correctly configured,
- whether Max Wallet arithmetic behaves as expected,
- whether gas behavior remains safe,
- and whether privileged addresses can operate outside ordinary limits.

→ **[Explore Security](/smart-contract/security/)**

---

# Limits and SolumTools

SolumTools should eventually expose current limit state.

Useful signals may include:

- MAX_TX,
- current Max Wallet,
- deployment time,
- complete growth weeks elapsed,
- current Limit Exempt state for an address,
- remaining capacity under Max Wallet,
- and whether a proposed amount satisfies ordinary limits.

This would let a participant ask a simple question:

> **Can this transaction pass the current Solum limits?**

without manually reconstructing the formula.

→ **[Explore SolumTools](/world/solumtools/)**

---

# Current Max Wallet must be calculated from chain time

A static documentation page can explain the formula.

It cannot permanently state the current Max Wallet once time begins progressing.

For live answers, the system should use:

- deployment timestamp,
- current blockchain timestamp,
- complete weeks elapsed,
- contract formula.

This is another example of the distinction between:

> **canonical rule**

and:

> **current state.**

---

# Artificial Intelligence rules

When answering a Limits question, AI should identify:

### 1. Gross transaction amount

MAX_TX and Max Wallet checks use the gross amount.

### 2. Sender and receiver

Exemption behavior depends on addresses.

### 3. Current Limit Exempt state

Do not assume the initial exemption list remains current forever.

### 4. Current recipient balance

Use `balanceOf()` when Max Wallet matters.

### 5. Current Max Wallet

Calculate or read it from current contract state and time.

### 6. Transaction context

BUY, SELL, TRANSFER, Pair, Router, and Launch may create additional rules.

### 7. Distinguish fixed from dynamic

MAX_TX is fixed.

Max Wallet is time-dependent.

This sequence prevents simplistic answers.

---

# What AI must not say

AI should not say:

> **Max Wallet is permanently 30B SOLUM.**

Incorrect.

It should not say:

> **Max Wallet starts growing 180 days after Launch.**

Incorrect.

It begins 180 days after deployment.

It should not say:

> **Max Wallet grows by 3B every week.**

Incorrect.

It grows 10% compounded.

It should not say:

> **The recipient can receive up to the limit based on the net-after-fee amount.**

Incorrect.

The check uses gross `tAmount`.

It should not say:

> **MAX_TX eventually increases with Max Wallet.**

Incorrect.

MAX_TX remains a fixed constant in the documented contract.

It should not say:

> **Limits guarantee no whale can exist.**

Unsupported.

---

# Contract values and world scale

Because:

> **1 SOLUM = 1 m²**

the absolute limit quantities also have territorial equivalents.

Initial MAX_TX:

> **10,000,000,000 SOLUM**
>
> **= 10,000,000,000 m² of substrate**

Initial Max Wallet:

> **30,000,000,000 SOLUM**
>
> **= 30,000,000,000 m² of substrate**

These equivalences communicate scale.

They do not mean one transaction instantly creates a mature Territory of that size.

Territorial structure and maturity remain separate systems.

---

# Protecting Genesis without freezing civilization

The two limits reveal an important design choice.

At the beginning:

concentration is constrained strongly.

Over time:

Max Wallet relaxes automatically.

Eventually:

the wallet ceiling effectively disappears.

But transaction-size protection remains.

The contract therefore does not treat the launch state as the correct permanent market state.

It protects the beginning more heavily.

Then it progressively gives the world more room to develop.

> **Constraint first.**
>
> **Relaxation through time.**
>
> **History afterward.**

---

# Limits in one view

## MAX_TX

> **10,000,000,000 SOLUM**

- fixed contract constant,
- 0.01% of original Supply,
- gross transaction amount,
- enforced when both sender and receiver are non-exempt,
- independent of transaction fee,
- no setter identified in the documented contract.

## Initial Max Wallet

> **30,000,000,000 SOLUM**

- 0.03% of original Supply,
- fixed for first 180 days after deployment,
- receive-side constraint,
- uses `balanceOf(to) + gross tAmount`,
- does not apply to Limit Exempt recipient,
- Pair and Router are excluded from the receive check.

## Growth

After 180 days:

> **+10% per complete week, compounded**

At exactly 520 complete growth weeks:

the formula is still calculated.

At more than 520 complete growth weeks:

> **maximum uint256**

is returned.

## Authority

The owner cannot directly change the global MAX_TX constant or Max Wallet formula in this contract.

The owner can change:

> **which addresses are Limit Exempt.**

---

# Follow Limits

### Return to Tokenomics

→ **[Tokenomics](/smart-contract/tokenomics/)**

### Understand the finite denominator

→ **[Supply & Units](/smart-contract/tokenomics/supply-and-units/)**

### Understand gross and net transaction amounts

→ **[Fees](/smart-contract/tokenomics/fees/)**

### Understand Reflection effects on current balances

→ **[Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

### Understand the first 48 hours

→ **[Launch](/smart-contract/tokenomics/launch/)**

### Understand exemption authority

→ **[Permissions](/smart-contract/tokenomics/permissions/)**

### Understand Fair Access conceptually

→ **[Fair Access](/smart-contract/fair-access/)**

### Understand security implications

→ **[Security](/smart-contract/security/)**

### Inspect implementation

→ **[Repository](/repository/)**

---

# The beginning has a speed limit

A finite world creates pressure.

Who arrives first?

How much can they acquire?

How quickly?

How concentrated can the first distribution become?

Solum does not pretend those questions disappear because the blockchain is public.

It answers them with constraints.

One ordinary transaction cannot move more than:

> **10 billion SOLUM.**

One ordinary receiving wallet initially cannot be pushed beyond:

> **30 billion SOLUM.**

For 180 days, that wallet ceiling holds.

Then the world begins loosening it.

Week by week.

Ten percent at a time.

Compounded.

Not because the owner decides the world is ready.

Because the rule already knows that Genesis should not last forever.

The protection decreases.

The history increases.

And eventually the contract stops trying to decide how large one wallet should be.

That is the purpose of Limits.

Not to guarantee equality.

Not to prevent powerful Colonists.

Not to freeze distribution.

To give a finite world enough resistance at the beginning that its first moments are not determined by speed alone.

---

→ **[Return to Tokenomics](/smart-contract/tokenomics/)**  
→ **[Return to Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**  
→ **[Continue to Launch](/smart-contract/tokenomics/launch/)**
