---
layout: default
title: Aster Pilot 001 — Run 001
nav_exclude: true
---

# Aster Pilot 001 — Run 001

**Pilot:** Aster Pilot 001  
**Pilot Version:** 1.0  
**Run:** 001  
**Status:** PREPARED — NOT STARTED

This directory contains the working project state used during Run 001.

It is separate from the frozen source artifacts of Aster Pilot 001.

---

# Execution Project

The working project is located in:

```text
project/
```

Before execution begins, it must contain an exact copy of the five frozen initial agent-visible artifacts:

```text
project/
├── requirements.md
├── architecture.md
├── operations.md
├── decisions.md
└── open-issues.md
```

These files constitute the initial produced state for the run.

At initialization:

\[
Produced\ State_0 = G_0
\]

with respect to the evaluated properties and relationships.

---

# Frozen Source Boundary

The files in:

```text
../../agent/
```

are frozen experimental source artifacts.

They must not be modified during Run 001.

The files in:

```text
../../evaluator/
```

are evaluator-only material.

They must not be supplied to the evaluated agent.

Only the working files under:

```text
project/
```

may evolve during the experimental trajectory.

---

# Initialization Rule

Before AI-A receives the project, the five working artifacts must be verified against the frozen source artifacts.

Initialization requires:

\[
Working\ Artifact_i = Frozen\ Artifact_i
\]

for every initial agent-visible artifact.

The comparison should be exact at initialization.

Any difference discovered before execution must be corrected before the run starts.

Any difference discovered after execution begins must be recorded rather than silently corrected.

---

# Execution Sequence

Run 001 follows the frozen sequence:

\[
Reconstruction_A
\rightarrow
T1
\rightarrow
T2
\rightarrow
Replacement
\rightarrow
Reconstruction_B
\rightarrow
T3
\rightarrow
T4
\]

AI-A begins from the initialized working project.

AI-B later receives the permitted persistent working project state produced by the preceding trajectory.

AI-B receives no conversational state from AI-A.

---

# State Preservation

A snapshot of the working project must be preserved at each required experimental boundary:

```text
S0 — Initial state
S1 — After T1
S2 — After T2
S3 — After T3
S4 — After T4
```

These are observed project states.

They must not be treated automatically as reference states.

Therefore:

\[
S_t \neq G_t
\]

unless evaluation establishes the relevant equivalence.

---

# Error Propagation

The working project must not be silently corrected between transformations.

If AI-A introduces an unauthorized change during T1 or T2, that change remains part of the produced trajectory unless the frozen protocol explicitly authorizes an intervention.

AI-B therefore receives the persistent state actually produced by the preceding trajectory.

This allows the pilot to observe whether project-state errors:

- persist;
- disappear;
- compound;
- interact with later transformations.

No such behavior is assumed in advance.

---

# Evidence Boundary

Run 001 must preserve separately:

- project snapshots;
- raw reconstruction responses;
- raw transformation responses;
- model and execution configuration;
- replacement event;
- protocol deviations;
- evaluator observations.

Experimental evidence must not be reconstructed retrospectively from memory when a raw record can be preserved directly.

---

# Current State

**Run directory:** CREATED  
**Working project:** NOT YET VERIFIED  
**AI-A:** NOT STARTED  
**T1:** NOT STARTED  
**T2:** NOT STARTED  
**AI-B:** NOT STARTED  
**T3:** NOT STARTED  
**T4:** NOT STARTED  
**Evaluation:** NOT STARTED
