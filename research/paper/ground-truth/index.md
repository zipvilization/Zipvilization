---
layout: default
title: Ground Truth Construction
parent: Paper
nav_order: 2
description: >
  Method for constructing and freezing reference project states,
  authorized transitions and expected outcomes before experimental execution.
permalink: /research/paper/ground-truth/
---

# Ground Truth Construction

Ground truth must exist before model outputs are evaluated.

In a longitudinal project, however, ground truth is not necessarily a single immutable project state.

A valid transformation may create, modify or retire project properties.

The experiment therefore distinguishes:

**initial ground truth**

from

**authorized ground-truth evolution**.

What is frozen before execution is not the requirement that the project remain unchanged.

It is the reference state together with the rules defining which transitions are valid.

---

# 1. Initial Reference State

Before execution, construct an initial reference state:

\[
G_0
\]

`G₀` contains a finite set of operationally relevant project properties required for the experiment.

A property may include, where relevant:

- semantic content;
- type;
- epistemic status;
- authority;
- relationships;
- historical or provenance information.

Only information necessary for evaluation should be included.

Ground truth is not intended to reproduce every aspect of the project.

---

# 2. Stable Property Identity

Each evaluated property receives a stable identifier:

\[
p_1,p_2,\ldots,p_n
\]

The identifier refers to the project property rather than to a particular sentence or file occurrence.

A property may therefore survive:

- rewriting;
- relocation;
- consolidation;
- decomposition of redundant text;

provided its required semantic state remains valid.

This establishes:

\[
Property \neq Textual\ Occurrence
\]

---

# 3. Source Traceability

Every initial ground-truth property must be supported by evidence available in the experimental project.

The evaluator records the authoritative experimental source supporting each property.

This establishes a distinction between:

\[
Source \neq Property
\]

A source may support multiple properties.

A property may also be supported by multiple sources.

Redundant occurrences do not create additional ground-truth properties unless they establish distinct semantic requirements.

---

# 4. Relationships

Relationships are represented separately from the properties they connect.

This establishes:

\[
Source \neq Property \neq Relationship
\]

A relationship must not be introduced merely because two properties appear related to the evaluator.

It must be supported by the experimental project or explicitly established as part of the frozen experimental design.

Relationship types should describe what the evidence supports.

Association must not be silently converted into logical implication.

---

# 5. Epistemic State

Where relevant to the experiment, a property may have an epistemic state such as:

- established;
- derived;
- experimental;
- unresolved.

The exact vocabulary used in a study must be fixed before execution.

An unresolved property is not missing information.

If the project explicitly preserves a decision as unresolved, resolving it without authorization constitutes a project-state change.

---

# 6. Authorized Change Set

For each transformation \(T_t\), define before execution the project properties whose semantic state may change:

\[
A_t
\]

The authorized set may include operations such as:

- create;
- modify;
- retire;
- change status.

Authorization refers to semantic project state, not merely permission to edit a file.

A transformation may modify extensive text while authorizing no semantic change to existing properties.

---

# 7. Expected Transition

For every authorized semantic change, define the minimum expected transition before execution.

Examples include:

\[
p_i:a \rightarrow b
\]

for modification,

\[
\varnothing \rightarrow p_j
\]

for creation,

or another explicitly defined state transition.

The expected transition specifies the semantic conditions required for local task success.

It does not prescribe the wording the agent must produce unless wording itself is part of the experimental task.

---

# 8. Versioned Ground Truth

After a valid authorized transformation, the applicable reference state may change.

The experiment therefore represents a sequence:

\[
G_0 \rightarrow G_1 \rightarrow G_2 \rightarrow \ldots \rightarrow G_n
\]

where each valid transition is determined by the previous reference state and the transformation authorized before execution.

Conceptually:

\[
G_{t+1}=Transition(G_t,T_t)
\]

This notation does not assume a particular computational implementation.

Its purpose is to make explicit that project evolution can be valid.

---

# 9. Conservation Across Change

Conservation does not mean preserving `G₀` indefinitely.

For transformation \(T_t\), properties authorized to change are evaluated according to their expected transition.

Relevant valid properties outside the authorized change set must retain their required semantic state.

Therefore:

\[
Conservation \neq Immutability
\]

A correct authorized change is not degradation.

Failure to perform an authorized change is not automatically a conservation failure.

These outcomes belong to different evaluation dimensions.

---

# 10. Expected Local Outcome

Each transformation must have predefined minimum semantic conditions for local success.

These conditions determine whether the authorized transformation was completed correctly.

This allows the experiment to distinguish:

- successful transformation with conservation;
- successful transformation with conservation failure;
- unsuccessful transformation with conservation;
- unsuccessful transformation with conservation failure.

Local success and conservation must not be inferred from each other.

---

# 11. Produced State Versus Reference State

The state produced by an agent after transformation is not automatically the next ground truth.

The experiment must distinguish:

\[
Produced\ State
\]

from

\[
Expected\ Reference\ State
\]

If an agent introduces an unauthorized error, that error may persist in the experimental trajectory depending on the predefined continuation protocol.

Its persistence does not make the error ground truth.

This distinction is necessary when studying accumulated degradation.

---

# 12. Freeze Before Execution

Before an evaluated run begins, freeze:

- initial reference state;
- property identifiers;
- property types where used;
- epistemic states where used;
- source evidence;
- evaluated relationships;
- authorized change set for each predefined transformation;
- expected semantic transitions;
- expected local outcomes;
- evaluation rules.

The experiment may therefore contain evolving reference states without allowing those states to be retrospectively invented after observing model behavior.

---

# 13. Post-Freeze Corrections

A genuine error discovered in the frozen ground truth must not be silently corrected.

Record:

- the original annotation;
- the reason it was incorrect;
- the corrected annotation;
- when the error was discovered;
- which experimental runs were affected;
- how those runs will be treated.

Where possible, the treatment of ground-truth errors should itself be defined before execution.

A correction to experimental ground truth is a methodological event, not an invisible edit.

---

# 14. Evaluator Separation

Where feasible, evaluators should assess model outputs without knowing:

- the experimental condition;
- the expected research outcome;
- which representation is hypothesized to perform better.

Evaluators may access the frozen reference information required to make the assigned judgment.

They must not add requirements from their own interpretation of what the project should have been.

---

# 15. Evaluator Disagreement

Disagreement between evaluators must be recorded.

It must not be resolved informally in favor of the interpretation that better supports the research hypothesis.

The eventual study must define in advance:

- independent annotation procedure;
- adjudication procedure;
- treatment of unresolved disagreement;
- agreement reporting.

No particular agreement statistic is assumed until the annotation structure is finalized.

---

# 16. Ground-Truth Boundary

Ground truth establishes correctness within the experimental project and task.

It does not establish:

- a universal ontology of project state;
- a universal taxonomy of project properties;
- that only one valid project future exists;
- that every project should represent knowledge in the same way.

An experimental project may intentionally contain open state.

In that case, ground truth can specify:

> what must remain valid

without specifying:

> what the project must ultimately become.

---

# 17. Traceability Requirement

For every evaluated judgment, it should be possible to reconstruct the chain:

\[
Source
\rightarrow
Property/Relationship
\rightarrow
Reference\ State
\rightarrow
Transformation
\rightarrow
Authorized\ Transition
\rightarrow
Evaluation
\]

If that chain cannot be established, the judgment requires methodological review.

---

# Methodological Gate

A project instance is not ready for experimental use until:

1. its initial reference state is frozen;
2. every evaluated property has traceable support;
3. evaluated relationships are independently justified;
4. epistemic states required by the experiment are explicit;
5. authorized changes are defined for each transformation;
6. expected transitions are defined before model output;
7. local success criteria are frozen;
8. valid project evolution can be distinguished from conservation failure;
9. produced agent state can be distinguished from reference state;
10. evaluators do not need to invent missing project rules.

Only after these conditions are satisfied can a project trajectory be treated as an experimental unit.
