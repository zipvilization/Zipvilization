---
layout: default
title: Ground Truth Construction
parent: Paper
nav_order: 2
description: >
  Method for constructing and freezing the reference project state,
  authorized changes and expected outcomes before experimental execution.
permalink: /research/paper/ground-truth/
---

# Ground Truth Construction

The experiment requires a reference against which reconstruction, local task success and conservation can be evaluated.

That reference must exist **before model outputs are observed**.

Ground truth is therefore not an interpretation produced during evaluation.

It is part of the experimental design.

---

# 1. Reference Project State

Each experimental project begins from a reference state:

\[
P^*
\]

\(P^*\) contains a finite set of properties selected for experimental evaluation.

Each property must be identifiable independently of the wording used to represent it.

A property may include, where relevant:

- semantic content;
- property type;
- current status;
- authority;
- relationships to other properties;
- historical or provenance information required for interpretation.

Only information necessary to determine experimental correctness should be included in the reference annotation.

The reference state is not intended to reproduce every aspect of the project.

---

# 2. Property Identifiers

Each evaluated property receives a stable identifier before execution.

For example:

\[
p_1, p_2, \ldots, p_n
\]

The identifier remains stable even if the textual representation of the property changes.

This separates **property identity** from **surface wording**.

Evaluation therefore concerns semantic preservation rather than textual preservation.

---

# 3. Evidence for Ground Truth

A reference property must be supported by an authoritative experimental source.

The annotation must record where the property comes from.

A property must not be included merely because an evaluator considers it reasonable or desirable.

If the available source material does not establish a property sufficiently, it cannot be treated as ground truth.

Ambiguity in the source material must be recorded rather than silently resolved.

---

# 4. Epistemic State

Where epistemic status is experimentally relevant, it forms part of the reference property.

For example, a statement may be:

- established;
- derived;
- experimental;
- unresolved.

The exact experimental vocabulary must be defined before execution.

Correct evaluation therefore requires preserving not only propositional content but, where relevant, **what status that content has**.

An unresolved property is not equivalent to a missing property.

Its unresolved status may itself be part of the ground truth.

---

# 5. Relationships

Where a property's meaning depends on another property, the relevant relationship must be annotated explicitly.

The experiment must not assume that preservation of two isolated statements implies preservation of the relationship between them.

A relationship is included only when it is necessary to evaluate reconstruction or conservation.

---

# 6. Task-Specific Authorized Change Set

For every transformation \(T_t\), the authorized change set must be established before the model executes the task:

\[
A_t
\]

Each affected reference property is classified in advance as either:

**Authorized to change** — the task permits or requires semantic modification.

**Not authorized to change** — the task does not permit semantic redefinition.

Authorization concerns semantic state, not merely files or text locations.

Permission to edit a document does not imply permission to redefine every property represented within it.

---

# 7. Expected Local Outcome

Each task must also define the minimum semantic conditions required for successful local completion.

These conditions are established before execution.

This allows local task success to be evaluated independently from conservation.

A transformation may therefore:

- satisfy the local task and conserve the project;
- satisfy the local task and fail conservation;
- fail the local task while conserving unaffected state;
- fail both.

No one outcome is inferred automatically from another.

---

# 8. Pre-Execution Freeze

Before any evaluated model receives the experimental task, the following must be frozen:

1. reference project state;
2. property identifiers;
3. relevant property types and statuses;
4. required relationships;
5. source evidence;
6. authorized change set;
7. expected local outcome;
8. evaluation rules applicable to the task.

The frozen version must be retained unchanged for the evaluation of that experimental run.

---

# 9. Post-Freeze Changes

A ground-truth error may still be discovered after freezing.

Such an error must not be silently corrected.

Any post-freeze modification must be recorded with:

- the original annotation;
- the reason for modification;
- the revised annotation;
- the point at which the error was discovered;
- whether affected experimental runs must be excluded, repeated or re-evaluated.

The treatment of affected runs must follow a rule established before outcome analysis wherever possible.

---

# 10. Evaluator Separation

Where feasible, evaluation should be performed without revealing:

- which experimental condition produced the output;
- which model produced it;
- the expected research hypothesis.

This does not eliminate evaluator judgment.

It reduces avoidable sources of bias.

Cases requiring semantic judgment should be distinguishable from mechanically verifiable cases.

---

# 11. Disagreement

Evaluator disagreement must not be resolved by selecting the interpretation most favorable to the hypothesis.

Disagreements should be recorded.

Where multiple independent evaluators are used, the study must define in advance how disagreements are adjudicated and how agreement is reported.

No agreement statistic is selected at this stage.

Its suitability depends on the eventual annotation and evaluation design.

---

# 12. Boundary of Ground Truth

Ground truth establishes correctness **within the experimental project and task definition**.

It does not establish that the experimental taxonomy is universal.

It does not establish that every relevant property of a real project can be fully represented.

It does not establish that one valid future state exists.

In projects with an open terminal state, ground truth may define:

**what must remain valid**

without defining:

**what the project must ultimately become**.

This distinction is essential to the experiment.

---

# Methodological Gate

No benchmark instance is ready for execution until its ground truth and authorized change boundaries have been frozen.

The next methodological step is to determine **how experimental project instances and transformations are constructed without making the task trivial, ambiguous or dependent on knowledge unavailable to evaluators**.
