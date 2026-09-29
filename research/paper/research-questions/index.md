---
layout: default
title: Research Questions
parent: Paper
nav_order: 1
description: >
  Research questions and initial operational boundaries for studying
  reconstruction, local transformation and project conservation across
  successive AI-assisted transformations.
permalink: /research/paper/research-questions/
---

# Research Questions

The first study isolates three distinct questions:

**Reconstruction → Local Transformation → Conservation**

These questions are separated deliberately.

An AI agent may reconstruct a project correctly and still modify it incorrectly.

It may complete a local task successfully while degrading valid project state outside that task.

It may also preserve existing state simply because it failed to perform the requested transformation.

These outcomes must not be treated as equivalent.

---

# RQ1 — Reconstruction

> **To what extent can an independent AI agent reconstruct operationally relevant project state from persistent external project artifacts without access to the prior agent's conversational state?**

The purpose of RQ1 is to measure reconstruction before the agent is allowed to modify the project.

Reconstruction must be evaluated against reference properties established before the experiment.

It is not sufficient to ask whether the agent appears to understand the project.

---

# RQ2 — Local Transformation

> **After reconstruction, can the agent correctly perform a local transformation within its authorized scope?**

RQ2 measures whether the requested task itself is completed correctly.

This question is independent from conservation.

A system that preserves the project by failing to make required changes has not solved the problem.

---

# RQ3 — Conservation

> **When a local transformation is successfully completed, to what extent are valid project properties outside the authorized scope of that transformation preserved?**

RQ3 isolates the phenomenon that motivated *When Better Becomes Worse*.

Successful completion of the local task does not establish successful conservation of the project.

The two outcomes must be evaluated independently.

---

# Initial Unit of Analysis

For the first experiment, project state is treated operationally as a finite set of pre-annotated properties.

A property may represent:

- an invariant;
- a requirement or committed decision;
- a relationship or dependency;
- relevant rationale or provenance;
- an epistemic state;
- an explicitly open or unresolved state.

This is an experimental taxonomy, not a claim that these categories form a universal model of project state.

The taxonomy may be revised only through an explicit methodological decision, not retrospectively to fit experimental results.

---

# Authorized Change

For each transformation \(T_t\), the experiment must define its authorized change set before execution:

\[
A_t = \{p_i \mid T_t \text{ is authorized to modify } p_i\}
\]

Properties outside that scope form the relevant conservation set:

\[
U_t = P_t \setminus A_t
\]

The transformation is then evaluated in two different dimensions:

**Local task success** — whether the required changes within the authorized scope were performed correctly.

**Conservation** — whether valid project properties outside that scope retained their required semantic meaning.

Conservation does not require textual identity.

A property may be rewritten, moved or represented differently without being lost, provided its relevant meaning, status and relationships remain valid.

---

# Initial Failure Taxonomy

Potential conservation failures are classified initially as:

**Omission** — a valid property disappears.

**Contradiction** — the transformation introduces a statement incompatible with valid project state.

**Unauthorized modification** — a property outside the authorized scope changes semantically.

**Relationship loss** — relevant elements remain, but a required relationship between them is lost or altered.

**Authority or status error** — the authority or epistemic status of a property changes without authorization.

**Premature closure** — an explicitly open or unresolved state is converted into a decision without authorization.

**Historical distortion** — the transformation changes the valid meaning of an established historical state or event.

These categories are provisional experimental labels.

Additional categories should not be introduced unless observed failures cannot be represented adequately by the existing taxonomy.

---

# Methodological Boundary

No aggregate conservation metric is defined at this stage.

No weighting between property types is assumed.

No hypothesis about the superiority of a particular representation architecture is assumed.

No claim is made that degradation will occur.

Before experimental execution, the study must establish:

1. the reference project state;
2. the properties relevant to each task;
3. the authorized change set;
4. expected task outcomes;
5. evaluation rules for reconstruction and conservation.

These elements must be fixed before model outputs are evaluated.

The next methodological problem is therefore **ground truth construction**.
