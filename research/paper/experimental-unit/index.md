---
layout: default
title: Experimental Unit Design
parent: Paper
nav_order: 3
description: >
  Design principles for controlled project instances and transformations used
  to study reconstruction, local task success and project conservation.
permalink: /research/paper/experimental-unit/
---

# Experimental Unit Design

The first experiment requires a project that is complex enough to support meaningful dependencies and change, but controlled enough to establish reliable ground truth.

The experimental unit is not an isolated prompt.

It is a **persistent project state subjected to a sequence of authorized transformations**.

---

# 1. Controlled Project First

The initial experiment should use a controlled project constructed specifically for the study.

It should not begin with Zipvilization itself.

A controlled project allows the study to define in advance:

- complete reference properties;
- authoritative sources;
- relationships and dependencies;
- epistemic states;
- authorized changes;
- expected local outcomes;
- intentionally unresolved elements.

This reduces ambiguity when determining whether a transformation succeeded or degraded project state.

A controlled project is not intended to establish real-world generalizability.

Its purpose is experimental control.

---

# 2. Required Complexity

The project must contain enough structure for conservation failures to be possible.

At minimum, it should include multiple interacting properties rather than independent facts.

The experimental state should contain examples of:

- stable properties;
- modifiable properties;
- dependencies;
- cross-document relationships;
- decisions with relevant rationale;
- properties with different epistemic status;
- explicitly unresolved elements.

Not every task should interact with every property type.

Complexity should be introduced only when it serves an experimental distinction.

---

# 3. Distribution Across Artifacts

Project state should not exist as a single answer sheet presented directly to the model.

Relevant information should be distributed across realistic project artifacts.

This is necessary because reconstruction is part of the phenomenon being studied.

However, distribution must not make required information inaccessible.

A failure caused by unavailable evidence is not equivalent to a failure to reconstruct available project state.

The experiment must therefore distinguish:

**information unavailable**

from

**information available but not correctly reconstructed or preserved**.

---

# 4. Transformation Sequence

An experimental trajectory consists of an ordered sequence:

\[
P_0
\xrightarrow{T_1}
P_1
\xrightarrow{T_2}
P_2
\ldots
\xrightarrow{T_n}
P_n
\]

Each transformation must have a defined local objective and an authorized change set.

Later tasks may depend on valid state produced by earlier tasks.

This creates a genuine project trajectory rather than a collection of independent prompts.

---

# 5. Local Validity

Each transformation should be independently capable of local success.

Tasks must not require the agent to violate ground truth in order to satisfy their explicit requirements.

Otherwise local success and conservation would be structurally incompatible.

The experiment is intended to test whether degradation occurs despite the existence of a valid conserving solution.

---

# 6. Conservation Pressure

Some transformations should create genuine pressure on persistent project state.

This pressure must arise from the task and project structure, not from intentionally misleading instructions.

Examples may include:

- modifying one concept that participates in several relationships;
- reorganizing material distributed across artifacts;
- extending a partially defined subsystem;
- reconciling new requirements with existing decisions;
- improving an incomplete but valid component;
- operating near an explicitly unresolved boundary.

The experiment should not depend on trick questions.

A conservation failure should remain meaningful even when the local task itself is reasonable.

---

# 7. Open State

At least some project dimensions should remain intentionally unresolved.

Their ground truth is not a hidden future answer.

Their ground truth is that **no authorized final decision currently exists**.

A valid transformation may preserve that openness or add information without closing it.

It may close the issue only when the corresponding task explicitly authorizes that decision.

This allows the experiment to distinguish incomplete information from deliberately open project state.

---

# 8. Agent Replacement

Where replacement is part of the experimental condition, a new agent must not receive the prior agent's conversational state.

The new agent receives only the persistent artifacts permitted by that condition.

The project persists.

The previous agent does not.

This isolates reconstruction from conversational continuity.

Model identity and replacement policy must be recorded for each experimental run.

---

# 9. Independence of Evaluation

The experimental project must be designed so that evaluators can determine:

- what state existed before a transformation;
- what the task authorized;
- what successful local completion required;
- what properties were expected to remain valid;
- what state existed afterward.

If those questions cannot be answered with sufficient reliability, the instance is not suitable for the benchmark.

---

# 10. Avoiding Triviality

The experiment should avoid instances where conservation can be achieved merely by copying unchanged text.

It should also avoid requiring unnecessary rewriting.

A useful instance creates a situation in which the agent must reason across project state while still having a valid path to local task completion.

The difficulty should come from **project relationships and transformation**, not from obscurity.

---

# 11. Avoiding Artificial Failure

The benchmark must not be designed primarily to make agents fail.

In particular, it should avoid:

- contradictory ground truth;
- inaccessible required information;
- ambiguous authorization boundaries;
- deliberately deceptive instructions;
- arbitrary hidden rules;
- evaluator-only assumptions not represented in the project artifacts.

Failure is informative only when the agent had a reasonable opportunity to succeed.

---

# 12. Pilot Before Benchmark

The first controlled project should be treated as a pilot.

Its purpose is to test whether:

- ground truth can be annotated reliably;
- authorization boundaries are understandable;
- reconstruction can be evaluated independently;
- local task success can be evaluated independently;
- conservation failures can be classified consistently;
- the tasks produce meaningful variation rather than universal success or universal failure.

Pilot results must not be presented as general evidence for the research hypothesis.

They determine whether the experimental design itself is viable.

---

# 13. Role of Zipvilization

Zipvilization should not serve as the sole initial experimental unit.

Its value is different.

It provides a longitudinal real-world case from which the research problem emerged and may later provide material for evaluating whether findings from controlled projects transfer to a substantially larger, historically evolved project.

Any later use of Zipvilization requires a separate audit of whether its historical states, sources and transformations can support reproducible ground truth.

The existence of extensive project history does not by itself establish that it is suitable experimental data.

---

# Methodological Gate

An experimental project is ready for pilot execution only when:

1. its reference state has been frozen;
2. every evaluated property has supporting evidence;
3. every transformation has a predefined authorized change set;
4. local success criteria are predefined;
5. relevant conservation properties are identifiable;
6. unresolved state is explicit where used;
7. required information is accessible to the tested condition;
8. evaluators can assess outcomes without inventing missing rules.

Only after a controlled pilot passes these conditions should the study define experimental conditions for comparing different forms of persistent project representation.
