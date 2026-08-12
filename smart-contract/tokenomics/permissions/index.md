---
layout: default
title: Permissions
parent: Tokenomics
grand_parent: Smart Contract
nav_order: 8
description: >
  Permissions documents the administrative authority of the Solum Smart
  Contract: ownership, fee reductions, Treasury changes, whitelist management,
  Fee Exempt and Limit Exempt addresses, SwapBack configuration, trading
  activation, timelocks, immutable boundaries, and the distinction between
  contract authority and world governance.
permalink: /smart-contract/tokenomics/permissions/
---

# Permissions

A Smart Contract can be transparent and still contain administrative authority.

Those two facts are not contradictory.

The important question is:

> **What authority exists?**

Then:

> **Who holds it?**

Then:

> **What can that authority change?**

Then:

> **What can it never change?**

Solum makes these questions inspectable.

This page documents the permission architecture of the token contract.

No authority should be hidden.

No limitation should be exaggerated.

No administrative capability should be described as decentralized merely because it exists on-chain.

> **Transparency begins where authority becomes visible.**

---

# Canonical permission model

The primary administrative role is:

> **Owner**

The owner can perform a defined set of privileged operations.

Those operations do not all have the same protection.

Some are:

> **immediate**

Some require:

> **a timelock**

Some important contract properties are:

> **not owner-configurable at all**

Therefore Solum does not have one generic category called:

> **admin control**

It has a permission structure.

That structure should be analyzed operation by operation.

---

# Permission classes

For clarity, contract authority can be divided into four classes.

## Immediate owner authority

Actions that can be executed directly by the owner without a contract-enforced waiting period.

## Timelocked owner authority

Actions that require proposal, delay, and later confirmation.

## One-time authority

Actions available to the owner but structurally limited to a particular transition.

## Non-authority

Properties the owner cannot arbitrarily modify through the documented contract.

This classification is more informative than simply saying:

> **The contract is Ownable.**

---

# Permission snapshot

| Capability | Owner authority | Timelock |
|:-----------|:---------------:|:--------:|
| Enable trading | Yes | No |
| Restart Launch | No ordinary mechanism | — |
| Manage whitelist | Yes | No |
| Set Fee Exempt | Yes | No |
| Set Limit Exempt | Yes | No |
| Propose fee reduction | Yes | 24h before execution |
| Increase fees | No | — |
| Propose Treasury change | Yes | 48h before confirmation |
| Configure SwapBack threshold | Yes | No |
| Configure SwapBack maximum | Yes | No |
| Configure SwapBack cooldown | Yes | No |
| Configure SwapBack slippage | Yes | No |
| Pause / resume SwapBack | Yes | No |
| Change MAX_TX | No setter documented | — |
| Directly set Max Wallet | No | — |
| Change Max Wallet growth formula | No | — |
| Mint additional SOLUM | No | — |
| Restore Burned SOLUM | No | — |
| Increase total Supply through minting | No | — |
| Arbitrarily change Holder balances | No documented mechanism | — |
| Transfer ownership | Yes | No |
| Renounce ownership | No function documented | — |

This table is one of the most important summaries in Tokenomics.

But every row deserves context.

---

# Ownership

The Solum contract uses an owner role.

The owner is a blockchain address with privileged access to functions protected by the ownership mechanism.

Therefore:

> **Owner is an administrative authority.**

It is not automatically:

- the Human creator forever,
- Treasury,
- a DAO,
- a State,
- a Kingdom,
- Artificial Intelligence,
- Horizonte,
- or The Trinomial.

Those are different concepts.

The owner is the address currently recognized by the contract as owner.

---

# Current owner is state

The original deployer and the current owner may be the same address.

But they do not have to remain the same forever.

Ownership can be transferred.

Therefore documentation should distinguish:

> **original deployer**

from:

> **current owner**

For historical explanation, the deployer matters.

For current authority, the owner matters.

---

# Ownership can be transferred

The current owner can transfer ownership to another valid address through the ownership mechanism.

After a successful transfer:

> **the new address becomes owner**

and receives the contract authority associated with that role.

The previous owner ceases to possess owner-only authority through the ownership role.

This means the permission system is attached to:

> **the role**

not permanently to one Human.

---

# Ownership transfer has no timelock

The documented ownership-transfer mechanism does not impose the same:

- 24-hour delay used for fee reductions,
- 48-hour delay used for Treasury changes.

Therefore ownership transfer belongs to the immediate authority surface.

This is important because transferring ownership transfers substantial administrative capability.

> **Authority can move faster than some individual parameter changes.**

That is part of the actual trust model.

---

# Ownership transfer does not rewrite history

If ownership changes:

- previous transactions remain,
- previous Burns remain,
- previous Reflection remains,
- existing balances remain,
- deployment time remains,
- launchTime remains,
- historical events remain.

Ownership changes future administrative authority.

It does not restart Solum.

---

# Renouncing ownership

The documented contract does not expose an ordinary:

> `renounceOwnership()`

function.

Therefore we should not claim:

> **ownership can be renounced**

unless the deployed implementation actually contains another mechanism that produces that result.

This matters because many token contracts inherit a standard Ownable implementation containing renunciation.

Solum's documented authority model must be described from its actual implementation.

Not from assumptions about other tokens.

---

# Owner is not omnipotent

The existence of an owner does not mean:

> **the owner can change everything.**

Some important properties are outside ordinary owner authority.

For example, under the documented implementation the owner cannot simply:

- mint another 100T SOLUM,
- restore Burned SOLUM,
- increase fees,
- rewrite MAX_TX through a setter,
- manually assign an arbitrary global Max Wallet,
- reset Launch through repeated trading activation,
- rewrite historical blockchain state.

Therefore the correct model is:

> **bounded administrative authority**

not:

> **absolute control**

and not:

> **no control.**

---

# Trading activation

The owner controls the transition from:

> **Pre-Trading**

to:

> **Trading Enabled**

through:

`enableTrading()`

This is one of the most consequential owner actions.

Before it executes:

ordinary public movement is restricted according to the pre-trading rules.

When it executes:

- trading becomes enabled,
- `launchTime` is established,
- the launch protection windows begin.

→ **[Explore Launch](/smart-contract/tokenomics/launch/)**

---

# Trading activation is effectively one-time

Once trading is enabled, the owner cannot simply call the same function again to create a new Launch.

The contract guard prevents repeated activation.

Therefore the owner chooses:

> **when Launch begins**

but does not receive ordinary authority to repeatedly restart:

- the first-hour whitelist window,
- the 48-hour BUY cooldown period.

This is a meaningful limitation.

---

# Whitelist authority

The owner can manage:

> **Launch whitelist state**

for individual addresses and through the supported batch mechanism.

An address can be marked:

- allowed,
- not allowed.

This authority is immediate.

There is no contract-enforced timelock for whitelist changes.

---

# Whitelist authority matters before and during the first hour

The whitelist has direct economic relevance during:

> **the first 60 minutes after launchTime**

because only whitelisted receiving wallets can BUY during that period.

Therefore owner whitelist authority can affect who has preferential BUY access during that window.

This is a real launch privilege.

It should not be hidden behind narrative language.

---

# The contract does not enforce a whitelist population cap

The whitelist mechanism does not itself establish a maximum number of addresses that may be whitelisted.

Therefore:

> **the owner controls whitelist membership**

within the technical capabilities of the contract.

If Zipvilization defines a limited number of Founding Colonists, that numerical limitation must be established and audited through the relevant canonical mechanism.

It should not be falsely attributed to Solidity if Solidity does not enforce it.

→ **[Explore Founding Colonists](/founding-colonists/)**

---

# Whitelist is not permanent privilege

The owner may maintain whitelist state after the first hour.

But the launch logic stops using the whitelist gate after the 60-minute window expires.

Therefore:

> **stored whitelist status ≠ permanent market privilege**

The meaning of a permission depends on where the contract actually consults it.

---

# Fee Exempt

The owner can designate addresses as:

> **Fee Exempt**

or remove that designation.

Fee Exempt status affects whether ordinary transaction fees apply.

This is a significant economic permission.

It is separate from:

- whitelist,
- Limit Exempt,
- ownership.

---

# Initial Fee Exempt addresses

At deployment, the documented contract initially grants Fee Exempt status to:

- deployer,
- contract itself,
- Treasury.

These are initial states.

They should not automatically be presented as current states forever.

The owner can later modify exemption mappings.

---

# Fee Exempt and Pre-Trading

Fee Exempt has another important function.

Before trading is enabled, a transfer can proceed if:

> **sender is Fee Exempt**

or:

> **receiver is Fee Exempt**

Therefore Fee Exempt status is not merely:

> **a tax exemption.**

Before Launch it also participates in the pre-trading movement gate.

This makes Fee Exempt particularly sensitive before `enableTrading()`.

---

# Fee Exempt does not mean Limit Exempt

The two permissions are independent.

An address can theoretically be:

- Fee Exempt but not Limit Exempt,
- Limit Exempt but not Fee Exempt,
- both,
- neither.

Therefore an AI should never infer one mapping from the other.

> **Fee Exempt answers a fee question.**
>
> **Limit Exempt answers a limits question.**

---

# Limit Exempt

The owner can designate addresses as:

> **Limit Exempt**

or remove that designation.

Limit Exempt affects the anti-concentration mechanisms.

This includes relevant MAX_TX and Max Wallet paths.

It is therefore a powerful permission.

---

# Initial Limit Exempt addresses

The documented initial configuration marks:

- deployer,
- contract itself,
- Treasury,
- Router,
- Pair

as Limit Exempt.

Again:

> **initial state is not necessarily current state.**

Current exemption status should be read from blockchain state when precision matters.

---

# Limit Exempt and MAX_TX

MAX_TX is enforced when:

> **both sender and receiver are non-exempt.**

Therefore making either side Limit Exempt can remove the ordinary MAX_TX restriction for that transaction path.

This means:

> **MAX_TX = 10B**

does not imply:

> **no transaction can ever exceed 10B.**

The exemption architecture must always be considered.

→ **[Explore Limits](/smart-contract/tokenomics/limits/)**

---

# Limit Exempt and Max Wallet

The Max Wallet receive-side check does not apply to a Limit Exempt recipient.

Therefore an exempt address can receive under conditions that would otherwise exceed the ordinary Max Wallet ceiling.

This is intentional administrative flexibility.

But it is also part of the concentration trust model.

---

# Exemptions can materially change effective Tokenomics

Publishing only:

- fee percentages,
- MAX_TX,
- Max Wallet

would be incomplete.

The effective rules experienced by an address also depend on:

- Fee Exempt state,
- Limit Exempt state.

Therefore a transparent explorer should expose both.

> **Rules without exemptions are incomplete documentation.**

---

# Fee authority

The owner has authority over fees.

But that authority is deliberately asymmetric.

The owner can propose:

> **fee reductions**

The owner cannot use the documented mechanism to:

> **increase fees**

This is one of the most important boundaries in the contract.

---

# Initial fees

Initial total fees are:

| Transaction | Initial Fee |
|:------------|------------:|
| BUY | 1% |
| SELL | 10% |
| TRANSFER | 5% |

These are Genesis values.

They are not necessarily permanent values.

→ **[Explore Fees](/smart-contract/tokenomics/fees/)**

---

# Fees can only move downward

A proposed new fee must be:

> **lower than the current fee**

for the relevant transaction type.

Therefore the authority is:

> **reduce**

not:

> **arbitrarily redefine**

and not:

> **increase.**

This creates a one-directional economic path.

---

# Fee reduction requires two stages

Changing a fee is not immediate.

The process is:

**Propose lower fee**

↓

**wait at least 24 hours**

↓

**execute reduction**

The contract therefore separates:

> **intent**

from:

> **execution.**

---

# Fee timelock

The delay is:

> **24 hours**

During that period:

the existing fee remains active.

The proposal does not immediately change transaction economics.

Only successful execution after the required delay changes the active fee.

---

# The timelock creates observation time

The 24-hour interval allows observers to distinguish:

> **a proposed future change**

from:

> **current active state.**

This is important for:

- users,
- SolumTools,
- Artificial Intelligence,
- monitoring systems.

A proposal is not yet the current fee.

---

# Fee reduction is irreversible upward through this mechanism

Once a fee is reduced:

the owner cannot use the same mechanism to return it to a higher previous value.

For example, if SELL moves from:

> **10%**

to:

> **8%**

the documented reduction mechanism cannot later restore:

> **10%**

because 10% is not lower than the current 8%.

This makes each successful reduction economically meaningful.

---

# Zero fee

Because the mechanism is downward-only, a fee can potentially move toward:

> **0%**

subject to the actual setter conditions.

Once a fee reaches zero:

it cannot be increased again through the documented fee-reduction mechanism.

Therefore zero represents an endpoint for that fee path under this contract.

---

# Fee split follows the current total fee

Reducing a total fee also reduces the absolute size of its internal allocations according to the contract's structural proportions.

Therefore owner fee authority indirectly affects future:

- Burn,
- Reflection,
- Liquidity,
- Treasury

generation where those components exist for the relevant transaction type.

The owner does not independently set every component percentage through separate arbitrary sliders.

The total fee and its defined split determine them.

---

# Fee authority cannot mint

Reducing or changing transaction economics does not alter the fundamental Supply architecture.

The owner cannot use fee authority to create new SOLUM.

Therefore:

> **economic parameter authority ≠ monetary issuance authority**

This distinction is fundamental.

---

# Treasury authority

The owner can change the configured Treasury.

But unlike most immediate administrative operations, Treasury change is timelocked.

The process is:

**Propose new Treasury**

↓

**wait at least 48 hours**

↓

**Confirm Treasury**

Only after confirmation does the active Treasury change.

---

# Treasury timelock

The Treasury delay is:

> **48 hours**

This is twice the fee-reduction delay.

The longer interval reflects the significance of changing the destination of future Treasury ETH.

During the pending period:

the existing Treasury remains active.

---

# Proposal is not confirmation

An AI should distinguish:

> **pending Treasury**

from:

> **current Treasury**

The proposed address does not become the active destination merely because the proposal exists.

Only confirmation after the required delay changes the current Treasury.

This distinction is essential for live state interpretation.

---

# New Treasury receives exemptions

When a Treasury change is confirmed, the new Treasury is automatically marked:

> **Fee Exempt**

and:

> **Limit Exempt**

Therefore Treasury confirmation changes more than one piece of state.

It changes:

- Treasury destination,
- Fee Exempt state of new Treasury,
- Limit Exempt state of new Treasury.

---

# Old Treasury exemptions remain

The contract does not automatically remove the old Treasury's:

- Fee Exempt status,
- Limit Exempt status

when the new Treasury is confirmed.

Therefore a Treasury transition can leave the former Treasury with exemptions.

The owner would need to remove those separately if desired.

This is a critical transparency detail.

---

# Treasury change can affect accumulated fees

Treasury SOLUM can accumulate before SwapBack.

If Treasury changes before those accumulated tokens are processed:

the Treasury address current at SwapBack execution receives the resulting Treasury ETH.

Therefore owner Treasury authority can affect the destination of value accumulated before the Treasury transition.

→ **[Explore Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**

---

# SwapBack authority

The owner controls several SwapBack parameters.

These include:

- enabled / paused state,
- threshold,
- maximum processing amount,
- cooldown,
- slippage.

Unlike fee reduction and Treasury change:

> **SwapBack configuration has no contract-enforced timelock.**

This is one of the most important immediate authority surfaces.

---

# SwapBack can be paused

The owner can disable automated SwapBack processing.

While disabled:

- applicable fees can continue being collected,
- Liquidity and Treasury buckets can continue accumulating,
- automated processing does not trigger through the normal path.

The owner can later re-enable it.

This authority is immediate.

---

# SwapBack threshold

Initial:

> **200M SOLUM**

The owner can change the threshold.

The documented setter does not impose a positive minimum.

Therefore zero is not excluded by that explicit condition.

This can materially change processing eligibility.

---

# SwapBack maximum

Initial:

> **1B SOLUM**

The owner can change the maximum processing amount.

The contract requires:

> **maximum ≥ threshold**

No separate explicit upper bound is documented in the configuration rule.

Therefore the initial 1B is not immutable.

---

# SwapBack cooldown

Initial:

> **60 seconds**

Owner-configurable range:

> **0 to 15 minutes**

This changes how soon another SwapBack can become eligible after the previous execution.

It does not change transaction fees.

---

# SwapBack slippage

Initial:

> **3%**

Owner-configurable range:

> **0.5% to 8%**

This affects the minimum-output calculation where the Router quote is available.

It does not create an additional participant fee.

---

# SwapBack changes are observable

Configuration changes emit events.

Therefore the owner has immediate authority, but not invisible authority.

On-chain observers can inspect:

- current values,
- historical changes.

This distinction matters.

> **No timelock does not mean no trace.**

It means:

> **the contract does not force a waiting period before the change becomes active.**

---

# LP custody and owner authority

SwapBack-created LP tokens are sent to:

> **current owner**

Therefore ownership has an additional economic consequence beyond administrative function calls.

The owner can receive LP tokens generated through automated liquidity addition.

The contract does not automatically lock them.

This makes LP custody part of the ownership trust boundary.

---

# Ownership transfer changes future LP recipient

If ownership changes:

future LP tokens created through SwapBack go to the new current owner.

Therefore ownership transfer changes both:

- administrative authority,
- future LP custody destination.

This should be considered whenever ownership structure changes.

---

# What the owner cannot do: Mint

The contract has a finite initial Supply:

> **100,000,000,000,000 SOLUM**

There is no documented mint function that allows the owner to create additional SOLUM.

Therefore:

> **the owner cannot inflate Supply through minting.**

This is one of the strongest economic boundaries in the architecture.

→ **[Explore Supply & Units](/smart-contract/tokenomics/supply-and-units/)**

---

# No hidden inflation through owner authority

Reflection does not mint.

Liquidity processing does not mint.

Treasury processing does not mint.

Ownership transfer does not mint.

Whitelist changes do not mint.

Exemptions do not mint.

Fee reductions do not mint.

Therefore administrative activity does not create a second issuance channel.

> **Finite means finite at the issuance layer.**

---

# What the owner cannot do: restore Burned SOLUM

Burn permanently reduces the active Supply through the Burn mechanism.

The documented contract provides no owner function to reverse that Burn.

Therefore:

> **Burned SOLUM cannot be administratively restored.**

Inside Zipvilization:

> **Permanent Nature remains permanent.**

This is where technical irreversibility and world meaning align directly.

→ **[Explore Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

---

# What the owner cannot do: increase fees

The fee-management mechanism is reduction-only.

Therefore the owner cannot use it to transform:

> **1% BUY**

into:

> **2% BUY**

or:

> **10% SELL**

into:

> **15% SELL**

or restore a previously reduced fee.

This places a hard direction on fee governance.

---

# What the owner cannot do: change MAX_TX

MAX_TX is defined as:

> **10,000,000,000 SOLUM**

The documented contract does not provide a setter for changing this constant.

Therefore owner authority cannot simply increase or decrease MAX_TX.

The owner can, however, alter which addresses are Limit Exempt.

That distinction is essential.

> **The rule is fixed.**
>
> **Its exemption set is mutable.**

---

# What the owner cannot do: set arbitrary Max Wallet

Max Wallet follows the contract's time-derived formula.

Initial:

> **30B SOLUM**

for:

> **180 days after deployment**

then:

> **+10% per complete week, compounded**

The owner does not manually choose the global current Max Wallet value.

Again, however:

the owner controls Limit Exempt status.

Therefore:

> **formula fixed**

does not mean:

> **every address always subject to formula.**

---

# What the owner cannot do: accelerate Max Wallet time

The owner does not control `block.timestamp` through an administrative setter.

The Max Wallet progression derives from blockchain time and deployment time.

There is no owner function that simply declares:

> **ten weeks have passed**

or:

> **the 180-day period is over.**

Time progression belongs to the chain environment.

---

# What the owner cannot do: restart Launch

Once trading has been enabled and `launchTime` established, the owner cannot ordinarily reset the launch clock through the documented trading activation mechanism.

Therefore:

- first-hour whitelist preference,
- first-48-hour BUY cooldown

are historical phases.

They are not recurring owner-controlled campaigns.

---

# What the owner cannot do: create Zips

The owner role belongs to the token contract.

It does not give the owner authority to arbitrarily create:

- Zips,
- maturity,
- Farms,
- Cities,
- States,
- Kingdoms

outside the canonical world rules.

Token administration and world state are different layers.

→ **[Explore The World](/world/)**

---

# Contract authority is not world authority

This distinction is fundamental.

The owner can administer defined parts of the Solum Smart Contract.

That does not make the owner:

> **sovereign of Zipvilization.**

Zipvilization contains additional layers:

- canonical world rules,
- deterministic development,
- SolumWorld,
- SolumView,
- Chapters,
- future governance structures,
- The Trinomial.

A token owner role must not silently become authority over every layer.

---

# Blockchain and Zipvilization

Again, two perspectives exist.

At blockchain level:

> **Owner**

At Zipvilization level:

there is no automatic equivalent such as:

> **King**

or:

> **Emperor**

or:

> **Government**

That translation would be false.

The owner is a technical administrative role.

World political authority, where it later exists, must arise from the canonical systems that define it.

> **Technical control is not political legitimacy.**

---

# Owner and Human

The Human component of The Trinomial is also not synonymous with:

> **contract owner**

The Human role concerns:

- design,
- responsibility,
- ethical direction,
- creation.

The owner role concerns:

- a blockchain permission set.

They may initially be operationally connected.

Conceptually they must remain distinct.

→ **[Explore Human](/trinomial/human/)**

---

# Owner and Artificial Intelligence

Artificial Intelligence does not receive owner authority merely because it participates in The Trinomial.

Its canonical function is cognitive.

It can:

- read,
- reason,
- compare,
- explain,
- detect inconsistencies,
- navigate the Atlas,
- interpret public state.

That does not mean it should possess private-key authority or silently execute privileged contract operations.

> **Understanding authority is not possessing authority.**

→ **[Explore Artificial Intelligence](/trinomial/artificial-intelligence/)**

---

# Owner and Horizonte

Horizonte is not a contract permission.

It does not appear as an address with Solidity privileges merely because it belongs to The Trinomial.

Horizonte belongs to the conceptual architecture of Zipvilization.

The owner belongs to the Smart Contract architecture.

Their roles must not be collapsed.

→ **[Explore Horizonte](/trinomial/horizonte/)**

---

# Permission does not mean obligation

The fact that the owner can perform an action does not mean that action will occur.

For example:

the owner can reduce a fee.

That does not mean a fee reduction is scheduled.

The owner can change an exemption.

That does not mean it will.

The owner can transfer ownership.

That does not mean ownership transfer is planned.

Therefore documentation must distinguish:

> **capability**

from:

> **intention**

and:

> **current state**

from:

> **possible future state.**

---

# Capability is part of the trust model

At the same time, saying:

> **the owner has never used this function**

does not remove the authority while the function remains available.

Risk and trust analysis should consider:

> **what can currently be done**

not only:

> **what has already been done.**

This is why Permissions belongs inside Tokenomics.

---

# Timelock does not remove authority

A 24-hour or 48-hour delay does not make the corresponding action decentralized.

The owner still initiates the change.

The timelock adds:

- delay,
- visibility,
- reaction time.

Therefore:

> **Timelocked authority remains authority.**

This should be explicit.

---

# No timelock does not mean hidden

Likewise, an immediate operation can still be:

- public,
- emitted through events,
- inspectable,
- historically traceable.

The distinction is:

> **how quickly authority can become effective.**

Not whether the blockchain records it.

---

# Events are part of transparency

Administrative events can allow observers to reconstruct important changes.

Relevant categories include:

- ownership changes,
- whitelist updates,
- exemption updates,
- fee proposals,
- fee executions,
- Treasury proposals,
- Treasury confirmations,
- SwapBack configuration,
- SwapBack pause state,
- Launch activation.

Events therefore form part of the public history of authority.

---

# Current mappings matter

Some permissions are stored in mappings.

For example:

- whitelist,
- Fee Exempt,
- Limit Exempt.

Historical events can help reconstruct changes.

But when answering:

> **Is this address exempt now?**

the current contract state is authoritative.

History explains how we arrived there.

State tells us where we are.

---

# Permissions and SolumTools

SolumTools should make administrative state observable.

Potential signals include:

- current owner,
- current Treasury,
- pending Treasury proposal,
- Treasury execution eligibility time,
- current BUY fee,
- current SELL fee,
- current TRANSFER fee,
- pending fee proposals,
- fee execution eligibility times,
- whitelist status,
- Fee Exempt status,
- Limit Exempt status,
- SwapBack enabled state,
- threshold,
- maximum,
- cooldown,
- slippage,
- trading enabled state,
- launchTime.

This would make the trust surface readable without requiring direct Solidity inspection.

→ **[Explore SolumTools](/world/solumtools/)**

---

# Permissions and Metrics

Permissions themselves can also have history.

Useful public metrics or records may include:

- number of fee reductions,
- historical fee trajectory,
- Treasury changes,
- ownership transfers,
- exemption changes,
- SwapBack configuration changes.

But care is required.

A count alone does not explain significance.

For example:

> **one ownership transfer**

may matter more than hundreds of ordinary transactions.

Metrics should preserve context.

→ **[Explore Metrics](/metrics/)**

---

# Permissions and Repository

The Atlas explains what authority means.

The Repository provides the exact implementation.

For security-critical questions, both matter.

A Human may begin here.

An AI can continue deeper.

The correct hierarchy is:

**Atlas explanation**

↓

**canonical contract specification**

↓

**Solidity implementation**

↓

**deployed bytecode and live state**

The deeper the claim, the closer verification should move toward execution reality.

→ **[Open the Repository](/repository/)**

---

# Permission hierarchy

A useful way to understand Solum authority is:

## Immutable or structurally fixed

Examples:

- initial finite issuance architecture,
- absence of mint authority,
- MAX_TX constant,
- Max Wallet formula,
- downward-only fee direction,
- one-time Launch structure,
- irreversible Burn semantics.

## Timelocked

- fee reduction: 24 hours,
- Treasury change: 48 hours.

## Immediate owner authority

- whitelist,
- Fee Exempt,
- Limit Exempt,
- SwapBack configuration,
- SwapBack pause/resume,
- trading activation,
- ownership transfer.

This hierarchy is more meaningful than a binary label such as:

> **centralized / decentralized**

Real systems deserve more precise descriptions.

---

# Trust surface

The main continuing owner trust surface includes:

### Exemptions

The owner can alter who receives special fee or limit treatment.

### SwapBack

The owner can alter processing parameters and pause the mechanism.

### Treasury

The owner can initiate a delayed change of destination.

### Fees

The owner can initiate delayed reductions.

### Ownership

The owner can transfer the administrative role.

### LP custody

Current owner receives LP tokens generated by automated liquidity addition.

These capabilities should remain visible to every participant.

---

# Hard boundaries

Against that authority stand several hard constraints.

### No minting

The owner cannot create additional SOLUM through a mint function.

### No fee increases

Fees move downward only.

### Burn irreversibility

Burned SOLUM cannot be restored through owner authority.

### Fixed MAX_TX rule

The 10B constant has no documented setter.

### Automatic Max Wallet progression

The global formula is not manually assigned by owner.

### Launch cannot simply restart

The first Launch becomes blockchain history.

These boundaries are equally important.

---

# Why both sides matter

If we documented only owner powers, Solum would appear more mutable than it is.

If we documented only immutable constraints, Solum would appear more decentralized than it is.

Transparency requires both.

> **Authority without boundaries is misleading.**
>
> **Boundaries without authority are equally misleading.**

The complete contract is the relationship between them.

---

# Artificial Intelligence rules

When answering a question about authority, AI should first identify:

### What exact operation is being discussed?

Do not answer generic questions about “control” when a specific permission exists.

### Is the operation owner-controlled?

Verify the actual function.

### Is there a timelock?

Distinguish immediate from delayed authority.

### Is the change upward, downward, or unrestricted?

Fee authority is reduction-only.

### Does an exemption alter the apparent rule?

MAX_TX and Max Wallet require exemption context.

### Is the requested information historical or current?

Read current state for current authority.

### Is the claim about Smart Contract authority or world governance?

Do not merge the layers.

### Can the contract actually perform the claimed action?

Never infer functionality from common token patterns.

Use the actual Solum implementation.

---

# What AI must not say

AI should not say:

> **The owner can change anything.**

False.

It should not say:

> **The owner has no control after deployment.**

False.

It should not say:

> **Fees are immutable.**

Incomplete.

They can decrease.

It should not say:

> **Fees can be increased by the owner.**

False under the documented mechanism.

It should not say:

> **MAX_TX means no transaction can exceed 10B under any circumstances.**

False because Limit Exempt state matters.

It should not say:

> **Treasury can be changed instantly.**

False.

The change requires 48 hours.

It should not say:

> **SwapBack parameters require a timelock.**

False in this implementation.

It should not say:

> **LP tokens are locked by the contract.**

False.

It should not say:

> **The owner can mint more SOLUM.**

False.

It should not say:

> **The owner governs Zipvilization.**

Unsupported and conceptually incorrect.

---

# Permission matrix

| System | Owner can change? | Delay / Constraint |
|:-------|:-----------------:|:-------------------|
| Trading OFF → ON | Yes | One-time transition |
| launchTime after activation | No ordinary reset | Established at Launch |
| Whitelist | Yes | Immediate |
| Fee Exempt | Yes | Immediate |
| Limit Exempt | Yes | Immediate |
| BUY Fee | Down only | 24h |
| SELL Fee | Down only | 24h |
| TRANSFER Fee | Down only | 24h |
| Treasury | Yes | 48h |
| SwapBack enabled | Yes | Immediate |
| SwapBack threshold | Yes | Immediate |
| SwapBack maximum | Yes | Immediate; maximum ≥ threshold |
| SwapBack cooldown | Yes | Immediate; ≤15 min |
| SwapBack slippage | Yes | Immediate; 0.5%–8% |
| MAX_TX | No setter | Fixed at 10B SOLUM |
| Max Wallet initial value/formula | No setter | Time-derived |
| Mint Supply | No | No mint mechanism |
| Reverse Burn | No | Burn irreversible |
| Ownership | Transferable | Immediate |
| Renounce ownership | No documented function | — |

This matrix should be readable by both Humans and machines.

It is the practical map of contract authority.

---

# Permissions in one view

## Owner can immediately

- enable trading,
- manage whitelist,
- manage Fee Exempt,
- manage Limit Exempt,
- pause/resume SwapBack,
- configure SwapBack,
- transfer ownership.

## Owner can after delay

### 24 hours

Reduce:

- BUY fee,
- SELL fee,
- TRANSFER fee.

### 48 hours

Change:

- Treasury.

## Owner cannot through the documented contract

- mint additional SOLUM,
- increase fees,
- restore Burned SOLUM,
- arbitrarily change MAX_TX,
- manually assign global Max Wallet,
- restart Launch,
- rewrite historical state.

## Additional trust consideration

SwapBack-created LP tokens go to:

> **current owner**

and are not automatically locked by this contract.

---

# Follow Permissions

### Return to Tokenomics

→ **[Tokenomics](/smart-contract/tokenomics/)**

### Understand Supply boundaries

→ **[Supply & Units](/smart-contract/tokenomics/supply-and-units/)**

### Understand mutable and immutable fees

→ **[Fees](/smart-contract/tokenomics/fees/)**

### Understand irreversible Burn

→ **[Burn & Reflection](/smart-contract/tokenomics/burn-and-reflection/)**

### Understand Treasury and LP custody

→ **[Liquidity & Treasury](/smart-contract/tokenomics/liquidity-and-treasury/)**

### Understand exemptions and limits

→ **[Limits](/smart-contract/tokenomics/limits/)**

### Understand one-time Launch authority

→ **[Launch](/smart-contract/tokenomics/launch/)**

### Understand immediate SwapBack authority

→ **[SwapBack](/smart-contract/tokenomics/swapback/)**

### Understand the wider security model

→ **[Security](/smart-contract/security/)**

### Inspect exact implementation

→ **[Repository](/repository/)**

---

# Authority should be visible

Solum does not ask a participant to believe that nobody has power.

That would be false.

There is an owner.

The owner has permissions.

Some are immediate.

Some are delayed.

Some can materially affect economic execution.

And those powers must be visible.

But the opposite claim would also be false.

The owner cannot simply rewrite Solum.

The owner cannot mint another world.

The owner cannot restore Burned land.

The owner cannot raise transaction fees through the documented fee mechanism.

The owner cannot rewrite MAX_TX.

The owner cannot manually stop blockchain time and decide how quickly Max Wallet evolves.

The owner cannot erase the first Launch and begin history again.

So the important question is not:

> **Is there an owner?**

The important questions are:

> **What can the owner do?**

> **How quickly can the owner do it?**

> **What evidence does the blockchain leave?**

> **What can the owner never do?**

> **And where does technical authority end?**

Those questions give us something much more useful than a label.

They give us a trust model.

And a trust model can be inspected.

> **Do not hide authority.**
>
> **Do not exaggerate authority.**
>
> **Define it.**
>
> **Bound it.**
>
> **Expose it.**

---

→ **[Return to Tokenomics](/smart-contract/tokenomics/)**  
→ **[Return to SwapBack](/smart-contract/tokenomics/swapback/)**  
→ **[Continue to Economic Model](/smart-contract/tokenomics/economic-model/)**
