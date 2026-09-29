---
layout: default
title: Experimental Conditions
parent: Paper
nav_order: 4
description: >
  Experimental conditions for isolating the effect of persistent project-state
  representation on reconstruction, local transformation and conservation.
permalink: /research/paper/experimental-conditions/
---

# Experimental Conditions

The experiment must isolate what changes between conditions.

A condition is scientifically useful only if differences in outcome can be attributed to a defined experimental manipulation with reasonable confidence.

The initial study therefore avoids comparing complete project-management systems or proprietary methodologies.

It compares controlled representations of the same underlying project state.

---

# 1. Experimental Variable

The primary manipulated variable is:

> **How operationally relevant project state is represented in the persistent artifacts available to the agent.**

The study does not initially manipulate:

- project ground truth;
- transformation objectives;
- authorized change sets;
- expected local outcomes.

These must remain equivalent across compared conditions.

---

# 2. Information Equivalence

A central methodological requirement is distinguishing:

**additional information**

from

**different representation of information**.

If one condition contains project knowledge unavailable in another, improved performance cannot be attributed solely to representation.

The study must therefore identify the propositions available in each condition before execution.

Where feasible, compared conditions should provide equivalent substantive information.

Any deliberate information difference must be treated as a separate experimental manipulation.

---

# 3. Baseline Condition

The baseline should provide the project information necessary to perform the experimental tasks without the representation feature being tested.

It must not be intentionally poor, confusing or incomplete.

A weak baseline would make comparative improvement difficult to interpret.

The baseline should represent a plausible way of maintaining project information without the experimental intervention.

Its exact form must be justified before execution.

---

# 4. Structured Condition

A structured condition may make project-state relationships explicit through organization or metadata.

Possible represented dimensions include:

- property identity;
- relationships and dependencies;
- source or provenance;
- authority;
- epistemic status;
- unresolved state.

Their inclusion is not assumed to improve performance.

Each dimension included in the experimental manipulation must be specified explicitly.

The study should not introduce several new dimensions simultaneously unless the intervention being tested is intentionally defined as their combination.

---

# 5. Representation Versus Explicit Knowledge

Some transformations that appear representational may actually add knowledge.

For example, placing two known properties next to each other changes organization.

Explicitly stating a previously unstated dependency between them adds a proposition.

These are different interventions.

The experiment must distinguish, where relevant:

**organization of existing information**

from

**explicit externalization of previously implicit project knowledge**.

Results from one must not be attributed automatically to the other.

---

# 6. Retrieval and Accessibility

Information equivalence is insufficient if one condition makes relevant information effectively inaccessible.

The study must record how agents can access persistent artifacts.

Differences in:

- available files;
- retrieval mechanisms;
- context limits;
- search capabilities;
- tool access;
- preprocessing;

may affect reconstruction independently of the representation under study.

Such differences must either be controlled or treated as experimental variables.

---

# 7. Conversational State

When agent replacement is tested, the incoming agent must not receive the previous agent's conversational state unless conversational continuity is itself an explicit experimental condition.

Persistent project artifacts and conversational memory must not be conflated.

This distinction is necessary to determine whether continuity resides in the project representation rather than in the previous interaction history.

---

# 8. Model Effects

Model identity is not the primary experimental variable.

Compared conditions should therefore use equivalent model configurations wherever possible.

If multiple models are later included, model identity becomes an additional factor rather than an uncontrolled difference.

A result observed with one model establishes evidence only for the tested conditions.

It does not establish model-independent behavior.

---

# 9. Condition Exposure

Each evaluated agent should receive only the artifacts and capabilities assigned to its condition.

Information from another condition must not leak into the run.

Where a trajectory includes agent replacement, the replacement agent inherits only the persistent project state permitted by that condition.

---

# 10. Candidate Comparison Structure

The first controlled comparison should remain minimal.

A defensible initial design may compare:

**Condition A — Baseline persistent representation**

A plausible persistent project representation containing the information required for the project and tasks, without the additional representation mechanism under investigation.

**Condition B — Experimental persistent representation**

The corresponding project information represented using the explicitly defined mechanism under investigation.

This two-condition structure is a starting point, not a final design.

Additional conditions should be introduced only when they answer a distinct research question or separate a confounding variable.

---

# 11. No OPA Condition

The initial experiment should not define a condition called **Operational Project Alignment**.

OPA is a conceptual hypothesis derived from prior Research.

Using it directly as an experimental treatment would combine multiple assumptions before their individual effects are understood.

The experiment should instead manipulate observable properties of project representation.

OPA may later be reconsidered in light of empirical results.

---

# 12. No Horizonte Condition

Horizonte is not an experimental condition in the initial study.

An intentionally open project dimension can be represented and tested without assuming Horizonte as its explanation.

This keeps the experiment capable of rejecting or replacing the conceptual interpretation developed in prior Research.

---

# 13. Comparison Outcomes

Conditions are compared independently on the phenomena defined by the Research Questions:

**Reconstruction**

**Local task success**

**Conservation**

A representation should not be considered beneficial merely because it improves one dimension.

For example, improved conservation accompanied by systematic failure to perform authorized changes would represent a trade-off, not unqualified improvement.

---

# 14. Cost and Efficiency

Differences in computational or interaction cost may become relevant when comparing conditions.

Potential factors include:

- input volume;
- retrieved context;
- number of tool operations;
- token use;
- execution time.

These variables should be recorded when technically reliable.

They are not substitutes for reconstruction, task success or conservation.

No efficiency metric is defined at this stage.

---

# 15. Experimental Neutrality

The experiment must permit the following outcomes:

- the experimental representation performs better;
- the baseline performs better;
- no meaningful difference is observed;
- effects differ between reconstruction, local success and conservation;
- observed differences depend on task or model.

The design must not define success as confirmation of the proposed representation.

---

# Methodological Gate

Experimental conditions are ready for pilot testing only when:

1. the manipulated variable is explicitly defined;
2. substantive information differences are documented;
3. access and retrieval differences are controlled or declared;
4. conversational continuity is separated from persistent project state;
5. model configuration is controlled or treated as a factor;
6. the baseline is plausible rather than intentionally weak;
7. each additional condition has an independent methodological purpose.

The next step is to define the **pilot protocol**: the exact sequence by which a project state is presented, reconstructed, transformed, replaced and evaluated.
