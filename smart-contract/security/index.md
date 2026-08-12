---
layout: default
title: Security
parent: Smart Contract
nav_order: 8
description: >
  Security documents the trust boundaries, privileged roles, mutable parameters,
  irreversible operations, attack surfaces, and verification requirements of
  the Solum Smart Contract architecture.
permalink: /smart-contract/security/
---

# Security

Security is not a label.

It is not:

> **This contract is safe.**

It is a set of questions.

What can change?

Who can change it?

What cannot change?

What operations are irreversible?

What privileges exist?

What assumptions does the architecture depend on?

What can fail?

What can be abused?

What can be verified?

That is how this section approaches Security.

> **Do not claim security.**
>
> **Document the conditions under which the system can be trusted.**

---

# First: define the trust boundary

A Smart Contract does not exist in isolation.

Its behavior can depend on several layers:

- deployed bytecode,
- inherited contracts,
- privileged roles,
- owner or administrative authority,
- external contracts,
- Pool configuration,
- Tax parameters,
- transaction limits,
- wallet limits,
- launch conditions,
- network infrastructure,
- indexers,
- interfaces,
- and Human operational decisions.

Security begins by identifying which of those layers can affect the system.

A contract may be technically correct while an operational dependency remains dangerous.

Therefore:

> **Security includes code.**
>
> **Security also includes authority and dependencies.**

---

# What must be documented

For every privileged or sensitive mechanism, the technical documentation should eventually answer:

- Who can call it?
- Under what conditions?
- What state can it modify?
- What value range is permitted?
- Is the change reversible?
- Is the action observable?
- Is there a delay or timelock?
- Can authority be transferred?
- Can authority be renounced?
- Can the mechanism be disabled?
- What happens if the privileged key is compromised?

These are not secondary implementation details.

They define the trust model.

---

# Ownership and administrative authority

If the contract contains an owner or another privileged role, that authority must be explicit.

The documentation should identify what the role can actually do.

For example, where applicable:

- modify Tax parameters,
- change exemptions,
- modify transaction limits,
- modify wallet limits,
- change Pool-related parameters,
- activate or deactivate launch restrictions,
- manage eligibility,
- transfer ownership,
- renounce ownership,
- or perform other privileged operations.

We should not summarize all of that as:

> **Owner exists.**

The important question is:

> **What power does ownership carry?**

---

# Privileged does not mean malicious

Administrative authority is not automatically a flaw.

Some systems require controlled configuration during launch or early development.

The security question is not whether privilege exists.

It is whether privilege is:

- necessary,
- bounded,
- visible,
- understandable,
- and progressively reducible where appropriate.

A privileged role becomes dangerous when its powers are unclear or effectively unlimited.

> **Authority should be documented before it is trusted.**

---

# Mutable and immutable

Every important contract property should eventually fall into one of two categories.

## Immutable

A property that cannot be changed after the relevant deployment or initialization.

## Mutable

A property that can change under defined authority and constraints.

This distinction should be explicit for foundational properties such as:

- Supply,
- minting capability,
- Tax parameters,
- Pool mechanics,
- Burn behavior,
- MAX_TX,
- Max Wallet,
- exemptions,
- ownership,
- and launch configuration.

If a property is described as fixed while the deployed contract can modify it, documentation is wrong.

If a property is mutable but presented as permanent, trust is being misrepresented.

---

# Supply security

Supply is one of the deepest security boundaries in Solum.

The canonical architecture establishes:

> **100,000,000,000,000 Solum**

with no ongoing inflationary minting.

That makes one technical question especially important:

> **Can any deployed mechanism create additional Solum?**

The answer must be verifiable from the implementation.

If no minting capability exists after deployment, that should be demonstrated technically.

If some mint-related function exists but is permanently inaccessible, that should also be explicit.

The finite world depends on this boundary.

→ **[Explore Supply](/smart-contract/supply/)**

---

# Burn security

Burn is irreversible.

That makes both correctness and authorization important.

Security questions include:

- Who can Burn?
- Can a Holder Burn only their own Solum?
- Can another authority Burn someone else's Solum?
- Is the Burn amount validated correctly?
- Is the Burn state observable?
- Can Burned Solum ever be restored?
- Does the implementation match the intended supply accounting?

Because Burn becomes Permanent Nature inside Zipvilization, an implementation error would not be merely cosmetic.

It could change the permanent geography of the world.

→ **[Explore Burn](/smart-contract/burn/)**

---

# Pool security

The Pool contains Solum with a special role in the architecture.

That makes its control especially sensitive.

The relevant questions include:

- Who controls the Pool?
- What can release Solum from it?
- Can Solum return to it?
- What limits govern distribution?
- Can Pool Solum be transferred arbitrarily?
- Are launch rules enforced at the Pool boundary?
- Can privileged addresses bypass those rules?
- Is Pool activity publicly observable?

Inside Zipvilization, the Pool is Dormant Land.

Technically, however, it remains a balance and control problem.

→ **[Explore Pool](/smart-contract/pool/)**

---

# Tax security

Tax parameters can strongly affect economic behavior.

Security therefore requires more than calculating the rate correctly.

We need to know:

- who can change the Tax,
- the permitted range,
- whether destination can change,
- whether exemptions exist,
- whether privileged addresses bypass Tax,
- whether Tax can reach extreme values,
- and whether changes are publicly observable.

A small permission can become a large economic authority.

> **Executable economics is part of the attack surface.**

→ **[Explore Taxes](/smart-contract/taxes/)**

---

# Fair Access security

Fair Access mechanisms introduce additional state and authority.

MAX_TX and Max Wallet can protect early distribution.

They can also create failure modes.

Questions include:

- Can they be bypassed?
- Can they accidentally block legitimate transfers?
- Are exempt addresses able to accumulate without limits?
- Can multiple-wallet strategies defeat their purpose?
- Can limits be changed arbitrarily?
- Can they be set to unusable values?
- Are their activation and deactivation conditions correct?

A protection mechanism can itself become a source of risk.

→ **[Explore Fair Access](/smart-contract/fair-access/)**

---

# Exemptions are part of the trust model

Exempt addresses deserve special attention.

An exemption may be technically necessary for:

- Pool operations,
- deployment,
- liquidity,
- system contracts,
- launch infrastructure,
- or another explicitly defined function.

But exemptions can also bypass important protections.

Therefore every exemption category should be explainable.

We should be able to answer:

> **Why does this address need different rules?**

and:

> **What can it do that ordinary Holders cannot?**

Hidden exemptions create hidden authority.

---

# Launch security

Token Launch is one of the highest-risk operational periods.

Before launch, most state is controlled and predictable.

At launch:

- participants enter,
- transactions accelerate,
- bots may act,
- liquidity changes,
- Fair Access becomes active,
- eligible addresses may receive special access,
- and mistakes become economically consequential.

Launch security should therefore examine:

- initialization order,
- eligibility configuration,
- Pool distribution,
- Tax state,
- MAX_TX,
- Max Wallet,
- exemptions,
- ownership,
- and transition from restricted to broader participation.

> **Genesis is not the moment to discover that launch assumptions were wrong.**

---

# Founding Colonist access

Preferential access creates another sensitive boundary.

Security must ensure that the technical eligibility mechanism corresponds to the intended list and period.

Questions include:

- How are eligible addresses stored?
- Who can add or remove them?
- When does the window open?
- When does it close?
- Can eligibility be reused later?
- Are limits still applied?
- Can non-eligible addresses bypass the restriction?
- Can eligible addresses exceed their intended access?

Historical recognition should not depend on an insecure implementation.

→ **[Explore Founding Colonists](/founding-colonists/)**

---

# Reentrancy and external calls

If contract execution interacts with external contracts, the resulting attack surface must be evaluated.

Relevant risks can include:

- reentrancy,
- unexpected callback behavior,
- malicious receiver contracts,
- external dependency failure,
- or assumptions about token behavior.

The exact relevance depends on the implementation.

The important principle is:

> **Every external interaction expands the trust boundary.**

Where no external call exists, that should not be invented as a risk.

Where one exists, it should be reviewed explicitly.

---

# Arithmetic

Modern Solidity provides strong default overflow and underflow protections in standard arithmetic contexts.

That does not eliminate mathematical risk.

A formula can still be wrong.

Percentage calculations can truncate.

Rounding can create edge cases.

Units can be confused.

Basis points can be interpreted incorrectly.

Large values can create unintended results.

Therefore contract mathematics should be verified against the intended model.

Especially for:

- Taxes,
- limits,
- supply accounting,
- Pool distribution,
- and percentage-based state.

> **Safe arithmetic syntax does not guarantee correct economics.**

---

# Precision and rounding

Solum is a fungible token.

The implementation may use token decimals.

Zipvilization also establishes:

> **1 Solum = 1 m²**

Those two facts require careful separation.

Token precision at blockchain level must not accidentally create inconsistent territorial interpretation.

Documentation should distinguish:

- atomic token units,
- whole Solum,
- token decimals,
- and canonical territorial units.

Artificial Intelligence and interfaces should use the same definitions.

A unit mismatch can become a world-state error.

---

# ERC-20 behavior

Standard compatibility reduces unnecessary complexity.

It does not automatically remove risk.

The implementation should be checked for any behavior that differs from ordinary ERC-20 expectations.

That may include custom:

- transfer logic,
- Tax handling,
- wallet restrictions,
- transaction restrictions,
- Burn behavior,
- exemptions,
- or launch conditions.

Any deviation from standard behavior should be deliberate and documented.

> **Standard interface does not imply standard economics.**

---

# Allowances

Where ERC-20 allowance mechanics are supported, approval-based transfers introduce their own trust model.

Users may authorize third parties to spend Solum.

That creates risks unrelated to Zipvilization-specific logic.

Interfaces should avoid encouraging unnecessarily broad approvals.

Users should be able to understand that:

> **approval is authority to move tokens under ERC-20 rules.**

World interpretation does not remove that blockchain reality.

---

# Front-end security is separate

A secure contract can still be used through an insecure interface.

A malicious or compromised website could:

- present the wrong contract,
- request dangerous approvals,
- alter displayed values,
- redirect users,
- or misrepresent transaction intent.

Therefore users should eventually be able to verify important identifiers independently.

The website is an interface.

It is not the blockchain.

> **SolumView can be wrong.**
>
> **A website can be compromised.**
>
> **Canonical chain state remains the reference.**

---

# Contract address matters

Once deployed, the canonical contract address becomes one of the most important identifiers in the project.

It should be presented clearly and consistently through trusted project sources.

Users should not need to search social media comments to determine which contract is real.

Artificial Intelligence should also verify the canonical address rather than infer one from untrusted context.

A technically correct explanation pointing to the wrong contract is still dangerous.

---

# Network matters

The same address can mean different things on different networks.

Therefore contract identity requires both:

> **network**

and

> **contract address.**

The canonical deployment should make both explicit.

Interfaces, documentation, SolumTools, and AI should preserve that pair.

Network ambiguity is a security problem.

---

# Verified source

Where supported by the deployment environment, source verification should allow participants to compare deployed bytecode with published source.

This improves inspectability.

But verified source is not the same as audited source.

And audited source is not the same as risk-free source.

Each term should mean exactly what it says.

> **Verified means verifiable source correspondence.**
>
> **It does not mean secure by declaration.**

---

# Audit

A professional security review can provide important evidence.

If an audit occurs, documentation should eventually distinguish:

- auditor,
- version reviewed,
- commit or code state,
- scope,
- findings,
- fixes,
- unresolved issues,
- and whether deployed code corresponds to the reviewed version.

An audit report for an old implementation should not be presented as proof for a different deployment.

Security evidence needs provenance.

---

# Testing

Testing should cover normal behavior and edge behavior.

Relevant areas may include:

- transfers,
- zero-value operations,
- maximum values,
- MAX_TX boundaries,
- Max Wallet boundaries,
- Taxes,
- exemptions,
- Pool interactions,
- Burn,
- launch restrictions,
- ownership changes,
- and invalid calls.

Tests should demonstrate expected behavior.

They are not a substitute for reasoning about unexpected behavior.

---

# Invariants

Some of the strongest security properties can be expressed as invariants.

Examples may include:

> **No unauthorized minting.**

> **Burned Solum cannot return to active supply.**

> **Balances reconcile after valid transfers.**

> **Tax calculations preserve accounting.**

> **Pool movement follows authorized rules.**

> **Active limits cannot be bypassed through ordinary contract paths where the rules intend them to apply.**

The exact invariant set belongs to the technical specification.

But the method is important.

A security claim becomes stronger when it can be written as something that must always remain true.

---

# Canonical Rules and Security

Canonical Rules provide a useful bridge between conceptual architecture and technical verification.

If Zipvilization depends on:

> **1 Solum = 1 m²**

the relevant supply and unit interpretation must remain coherent.

If Burn means Permanent Nature, Burn must actually be irreversible.

If Supply is finite, unauthorized minting must be impossible.

If Fair Access relies on limits, those limits must execute as documented.

Security protects the technical assumptions that the rest of the world treats as foundations.

→ **[Explore Canonical Rules](/smart-contract/canonical-rules/)**

---

# Security and SolumWorld

SolumWorld trusts certain blockchain facts as inputs.

That means incorrect contract behavior can propagate upward.

If Supply changes unexpectedly, world substrate changes.

If Burn is reversible, Permanent Nature is not actually permanent.

If Pool state can be manipulated unexpectedly, Dormant Land becomes unreliable.

If balances are wrong, Territory derivation becomes wrong.

The higher layers cannot repair broken blockchain truth through interpretation.

> **World integrity begins below the world.**

→ **[Explore SolumWorld](/world/solumworld/)**

---

# Security and Artificial Intelligence

Artificial Intelligence must be careful with security claims.

It should distinguish:

- designed behavior,
- verified source,
- tested behavior,
- audited behavior,
- deployed behavior,
- and inferred safety.

It should not say:

> **The contract is secure.**

merely because the architecture looks reasonable.

More accurate statements are:

> **This mechanism is designed to...**

> **The source shows...**

> **The deployed state currently reports...**

> **This version was reviewed by...**

> **This risk remains...**

Security language should preserve evidence.

→ **[Explore Artificial Intelligence](/trinomial/artificial-intelligence/)**

---

# Security and the Repository

The Repository is where security claims become inspectable in greater depth.

It should eventually provide access to relevant:

- contract source,
- tests,
- deployment notes,
- interfaces,
- configuration,
- security assumptions,
- audit material,
- and version history.

The Atlas explains what to inspect.

The Repository provides the technical material.

→ **[Open the Repository](/repository/)**

---

# Security and versioning

Security conclusions apply to specific code.

If the contract changes, the security state may change.

If configuration changes, risk may change.

If ownership changes, trust assumptions may change.

If a Chapter introduces a new contract, the attack surface changes.

Therefore security documentation should eventually become version-aware.

> **Secure according to which version?**

is a better question than:

> **Is it secure?**

---

# Security and upgradeability

If a deployed contract is upgradeable, the upgrade mechanism becomes one of the largest trust boundaries in the entire system.

If it is not upgradeable, that immutability creates different tradeoffs.

Therefore the architecture should state clearly whether the relevant contracts are:

- immutable,
- upgradeable,
- replaceable through migration,
- or governed through another explicit mechanism.

Never leave this to assumption.

An immutable bug and an upgradeable administrator are different risks.

---

# Migration

A future technical migration may become necessary.

Network conditions can change.

Infrastructure can become obsolete.

A better architecture may emerge.

Migration security would need to preserve:

- balances,
- supply integrity,
- Burn history,
- Pool state,
- canonical identifiers,
- and other relevant state.

A migration should not become an opportunity to silently rewrite the world.

Horizonte provides the conceptual constraint.

Technical security provides the execution constraint.

→ **[Explore Horizonte](/trinomial/horizonte/)**

---

# Emergency controls

If emergency controls exist, they must be documented.

Examples could include:

- pausing,
- restricted modes,
- emergency withdrawals,
- administrative recovery,
- or other intervention mechanisms.

Their existence creates authority.

Their absence creates another kind of risk.

Neither design should be hidden.

The correct question is:

> **What emergency powers actually exist?**

Not:

> **Does the project have good intentions?**

---

# Centralization risk

Some degree of early administrative control may exist.

Security documentation should describe it without euphemism.

Potential centralization vectors include:

- owner privileges,
- configurable Taxes,
- exemptions,
- Pool control,
- launch eligibility,
- wallet-limit authority,
- or upgrade authority.

These do not automatically invalidate the system.

But they matter.

Metrics and future governance may eventually show whether those powers decrease.

Transparency is more useful than pretending they never existed.

---

# Key compromise

A privileged key can become a critical point of failure.

Where privileged authority exists, operational security matters.

Potential mitigations can include:

- multisignature control,
- hardware signing,
- restricted permissions,
- timelocks,
- staged authority reduction,
- or eventual renunciation where appropriate.

The exact architecture should follow the implementation.

The important principle is:

> **A secure function controlled by an insecure key is not a secure system.**

---

# Security and decentralization

Decentralization is not binary.

A system can have:

- decentralized token ownership,
- centralized administrative configuration,
- immutable Supply,
- configurable Taxes,
- public state,
- and centralized front-end infrastructure

all at the same time.

Security documentation should describe the actual structure.

Not compress it into a single label.

> **Describe authority.**
>
> **Do not market decentralization.**

---

# Security and Chapters

Every new Chapter can expand the attack surface.

A production system introduces new state.

An economy introduces new flows.

Governance introduces authority.

Alliances introduce relationships.

Cross-contract interaction introduces dependencies.

Therefore Chapters should not only ask:

> What new possibility does this create?

They should also ask:

> **What new trust assumption does this create?**

→ **[Explore the Chapters](/chapters/)**

---

# Security and Metrics

Some security-relevant state can also become publicly measurable.

Potential examples include:

- current ownership,
- active Tax parameters,
- MAX_TX,
- Max Wallet,
- exemption state,
- Pool balances,
- Burn totals,
- and contract configuration.

Metrics should not turn these into a simplistic security score.

But visibility reduces hidden assumptions.

→ **[Explore Metrics](/metrics/)**

---

# Security is not finished at deployment

Deployment is not the end of security.

After deployment:

- state changes,
- ownership can change where permitted,
- integrations appear,
- market behavior creates new pressures,
- users discover edge cases,
- infrastructure evolves,
- and new Chapters can expand the system.

Security therefore has a historical dimension.

The contract may not change.

Its environment does.

---

# Disclosure

If a vulnerability is discovered, responsible handling matters.

The project should eventually define a clear path for security reporting.

The exact process belongs to operational documentation.

The principle is simple:

> **Make it easier to report a vulnerability than to ignore one.**

Security benefits from external scrutiny.

---

# What Security should never say

This section should avoid claims such as:

> **100% secure**

> **unhackable**

> **risk-free**

> **fully decentralized**

unless those words have an extremely precise and defensible technical meaning.

Software can fail.

Operational systems can fail.

Users can make mistakes.

External dependencies can fail.

Security documentation becomes more credible when it states limits openly.

---

# Security in one view

## Contract security

Understand:

- code behavior,
- permissions,
- mutability,
- arithmetic,
- external interactions,
- limits,
- Supply,
- Pool,
- Burn,
- Taxes,
- and launch logic.

## Operational security

Understand:

- privileged keys,
- deployment,
- configuration,
- ownership,
- front-end integrity,
- network identity,
- and migration risks.

## Verification

Prefer:

- source,
- tests,
- deployed state,
- explicit authority,
- reproducible behavior,
- and independent review.

## Boundary

> **Security is not a promise.**
>
> **It is an architecture that can be inspected, tested, challenged, and improved.**

---

# Follow Security

### What is the underlying asset?

→ **[Solum Token](/smart-contract/solum-token/)**

### What Supply assumptions must be protected?

→ **[Supply](/smart-contract/supply/)**

### How do economic mechanisms interact?

→ **[Tokenomics](/smart-contract/tokenomics/)**

### What controls dormant Solum?

→ **[Pool](/smart-contract/pool/)**

### What operation is irreversible?

→ **[Burn](/smart-contract/burn/)**

### What economic parameters matter?

→ **[Taxes](/smart-contract/taxes/)**

### What concentration mechanisms need enforcement?

→ **[Fair Access](/smart-contract/fair-access/)**

### Which foundational relationships should remain explicit?

→ **[Canonical Rules](/smart-contract/canonical-rules/)**

### What world depends on these technical facts?

→ **[SolumWorld](/world/solumworld/)**

### Where is the implementation?

→ **[Repository](/repository/)**

---

# Trust what can be checked

Zipvilization asks participants to accept unusual interpretations.

A token becomes land.

A Pool becomes Dormant Land.

Burn becomes Permanent Nature.

Blocks become biological time.

Zips become population.

Those ideas can be ambitious.

The technical foundation should not require the same kind of faith.

A Supply can be checked.

A balance can be checked.

A Burn can be checked.

A permission can be checked.

A Tax calculation can be checked.

A limit can be checked.

A contract address can be checked.

A source can be inspected.

A test can be reproduced.

That contrast is healthy.

The experiment can be imaginative.

The foundation should be verifiable.

> **Do not ask people to believe what the blockchain can prove.**

---

→ **[Return to Smart Contract](/smart-contract/)**  
→ **[Return to Fair Access](/smart-contract/fair-access/)**  
→ **[Continue to Canonical Rules](/smart-contract/canonical-rules/)**
