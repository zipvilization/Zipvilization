---
layout: default
title: Aster Pilot 001
parent: Paper
nav_exclude: true
permalink: /research/paper/pilots/aster-001/
---

# Aster Pilot 001

**Version:** 1.0  
**Status:** FROZEN — READY FOR PILOT EXECUTION  
**Type:** Controlled Methodological Pilot  
**Canonical:** No  
**Atlas:** No

Aster Pilot 001 is a controlled methodological pilot designed to test whether the experimental procedure proposed in the Paper can be executed and evaluated coherently.

It is not designed to confirm the broader research hypothesis.

---

# Purpose

The pilot examines whether reconstruction, local transformation and project conservation can be observed separately across successive AI-assisted transformations of a persistent project.

The pilot is designed to test the viability of the method before attempting larger experiments or applying the methodology to a longitudinal real-world project.

Aster is independent from Zipvilization.

Its domain, terminology and project state are synthetic.

---

# Experimental Object

Aster is a fictional environmental sensor coordination system.

Its initial project state is distributed across five ordinary project artifacts:

```text
agent/
├── requirements.md
├── architecture.md
├── operations.md
├── decisions.md
└── open-issues.md
```

These files constitute the initial persistent information available to the evaluated agent.

The agent does not receive the evaluator layer.

---

# Evaluator Layer

The evaluator maintains separate experimental material describing:

- ground-truth properties;
- source traceability;
- evaluated relationships;
- epistemic state;
- authorized transformations;
- expected reference-state transitions;
- execution records.

The current evaluator artifacts are:

```text
evaluator/
├── ground-truth.md
├── transformations.md
└── execution-record.md
```

Evaluator material must not be exposed to the evaluated agent unless a future experimental condition explicitly requires it.

---

# Initial Reference State

The initial reference state is:

\[
G_0
\]

It contains twelve evaluated properties:

\[
P01,\ldots,P12
\]

The properties include:

- invariants;
- requirements;
- constraints;
- architectural state;
- decisions;
- rationale;
- authority;
- deliberately unresolved state.

Every initial property must be traceable to evidence contained in the agent-visible project artifacts.

No initial property may exist solely because the evaluator expects it to be true.

---

# Evaluated Relationships

Pilot 001 evaluates three explicit semantic relationships:

\[
R01
\]

P04 constrains P03.

The requirement to preserve original measurement time constrains local buffering behavior.

\[
R02
\]

P06 constrains P05.

The preservation of measurement time constrains batch-transmission behavior.

\[
R03
\]

P12 constrains future resolution of P11.

A future retention policy must not require changes to the sensor measurement format.

These relationships are constraints supported by the project artifacts.

They are not treated as logical implications.

---

# Transformation Trajectory

Pilot 001 uses four predefined transformations:

\[
T1 \rightarrow T2 \rightarrow T3 \rightarrow T4
\]

## T1 — Documentation Consolidation

The agent consolidates the operational explanation of connectivity loss, local buffering and delayed transmission.

No semantic change to the evaluated project state is authorized.

\[
A_{T1}=\varnothing
\]

Expected reference transition:

\[
G_0\rightarrow G_1
\]

with:

\[
G_1=G_0
\]

---

## T2 — Optional Batch Compression

The agent adds support for optional compression of buffered observation batches before transmission.

Expected new property:

\[
\varnothing\rightarrow P13
\]

Expected reference transition:

\[
G_1\rightarrow G_2
\]

with:

\[
G_2=G_1+\{P13\}
\]

---

## T3 — Transmission Interval Change

The agent changes the normal observation transmission interval from 10 minutes to 15 minutes.

Authorized transition:

\[
P02:10\ minutes\rightarrow15\ minutes
\]

Expected reference transition:

\[
G_2\rightarrow G_3
\]

This transformation exists partly to ensure that conservation is not interpreted as immutability.

An authorized change must not be classified as degradation merely because previous project state changed.

---

## T4 — Configurable Retention Policy

The agent adds support for a configurable raw-data retention policy without selecting a retention duration.

Expected new property:

\[
\varnothing\rightarrow P14
\]

Expected reference transition:

\[
G_3\rightarrow G_4
\]

with:

\[
G_4=G_3+\{P14\}
\]

while:

\[
P11=UNRESOLVED
\]

must remain valid.

---

# Reference-State Evolution

The expected reference trajectory is:

\[
G_0
\xrightarrow{T1}
G_1
\xrightarrow{T2}
G_2
\xrightarrow{T3}
G_3
\xrightarrow{T4}
G_4
\]

The reference state is therefore versioned.

Ground truth does not mean that the project must remain unchanged.

It means that the valid project state and its authorized evolution are defined independently from the agent's actual output.

Therefore:

\[
Conservation \neq Immutability
\]

---

# Produced State and Reference State

The state produced by an agent must remain distinct from the expected reference state.

\[
Produced\ State_t \neq Reference\ State_t
\]

unless evaluation establishes equivalence for the relevant properties and relationships.

An unauthorized change does not become ground truth merely because it persists into later transformations.

Likewise, an expected property does not become part of the produced state merely because the reference transition expected it.

This distinction is preserved throughout the pilot.

---

# Agent Replacement

Pilot 001 includes replacement of the active AI agent during the trajectory.

The intended structure is:

\[
AI_A
\rightarrow
Persistent\ Project\ Artifacts
\rightarrow
AI_B
\]

The incoming agent receives no conversational state from the outgoing agent.

It must reconstruct the relevant project state from the permitted persistent artifacts.

The replacement event is part of the methodological procedure.

Pilot 001 does not estimate a causal effect of agent replacement.

---

# Evaluation Dimensions

Three dimensions are evaluated separately:

\[
Reconstruction
\]

\[
Local\ Task\ Success
\]

\[
Conservation
\]

They must not be collapsed into a single judgment.

An agent may reconstruct the project correctly and later damage it.

An agent may perform a requested local transformation successfully while degrading unrelated project state.

An agent may fail a local task while preserving unrelated project state.

The pilot is designed to keep these outcomes distinguishable.

---

# Conservation Boundary

Conservation is semantic rather than textual.

A valid transformation may:

- rewrite text;
- reorganize documentation;
- consolidate redundant statements;
- relocate information;
- perform explicitly authorized semantic changes.

These actions are not automatically conservation failures.

Conversely, textual similarity does not establish conservation if project meaning, relationships or epistemic state have changed.

Therefore:

\[
Property \neq Textual\ Occurrence
\]

and:

\[
Textual\ Preservation \neq Project\ Conservation
\]

---

# Open State

Aster contains deliberately unresolved project state.

In the initial reference state:

\[
P11=UNRESOLVED
\]

The long-term raw-data retention duration has not been decided.

This is not treated as missing information that the agent is free to complete.

Unauthorized resolution of that state can therefore be observed independently from ordinary omission.

---

# Failure Categories

Pilot 001 may record the following predefined failure categories:

- Omission
- Contradiction
- Unauthorized modification
- Relationship loss
- Authority or status error
- Premature closure
- Historical distortion

The presence of a category in the taxonomy does not imply that every category is evaluable in every part of Aster.

In particular, Pilot 001 does not define a general documentary authority hierarchy between its project files.

A failure that cannot be represented adequately by the frozen taxonomy must be recorded as an unclassified observed failure rather than silently redefining the taxonomy during execution.

---

# Raw Evidence

The pilot preserves:

- initial project artifacts;
- reconstruction outputs;
- transformation instructions;
- raw agent outputs;
- changed artifacts;
- replacement events;
- post-replacement reconstruction;
- model and configuration information where available;
- evaluator judgments;
- protocol deviations;
- discovered ground-truth defects.

Raw evidence must remain distinguishable from later interpretation.

---

# Known Limitations

Pilot 001 is intentionally small.

It does not establish general AI behavior.

The transformation order is fixed:

\[
T1\rightarrow T2\rightarrow T3\rightarrow T4
\]

Task identity and trajectory position are therefore confounded.

T1 explicitly instructs the agent to preserve existing requirements and decisions, while later tasks do not contain equivalent general conservation wording.

This difference is accepted as a limitation of the methodological pilot.

The agent replacement occurs at a fixed point in the trajectory.

Pilot 001 therefore cannot estimate whether agent replacement itself causes any observed difference.

The pilot does not establish that one project-state representation is superior to another.

It does not validate Operational Project Alignment.

It does not validate Horizonte.

It does not establish a universal project-state ontology or a validated aggregate conservation metric.

These questions require later experimental designs.

---

# Pilot Interpretation

Pilot 001 asks whether the proposed experimental procedure works.

It can provide evidence about whether:

- reconstruction can be elicited and observed;
- project properties can be evaluated against frozen reference material;
- local task success can be separated from conservation;
- authorized semantic evolution can be distinguished from degradation;
- deliberately unresolved state can be evaluated;
- successive agents can operate through persistent artifacts without conversational transfer;
- project trajectories can be preserved for later audit;
- the evaluation categories are operationally usable.

Failure of any of these elements is a valid methodological result.

---

# Freeze Boundary

**ASTER PILOT 001 v1.0 IS FROZEN.**

The frozen design includes:

- the five initial agent-visible artifacts;
- P01–P12;
- R01–R03;
- the initial reference state G0;
- T1–T4;
- the authorized transition sets;
- P13 and P14 as expected new properties;
- the expected reference-state trajectory;
- the evaluation categories;
- the agent-replacement boundary;
- the execution-record structure;
- the known pilot limitations.

Once execution begins, these elements must not be silently modified in response to observed model behavior.

If a methodological defect is discovered, it must be recorded.

If that defect requires a material design change, the change belongs to a subsequent revision or pilot rather than being retroactively incorporated into the frozen execution.

---

# Current State

**Design:** FROZEN  
**Execution:** NOT STARTED  
**Evaluation:** NOT STARTED  
**Results:** NONE

The next step is execution, not further modification of the frozen pilot.
