---
layout: default
title: Aster Pilot 001 — Experimental Prompts
nav_exclude: true
---

# Aster Pilot 001 — Experimental Prompts

**Pilot:** Aster Pilot 001  
**Version:** 1.0  
**Layer:** Evaluator Only  
**Status:** FROZEN — READY FOR EXECUTION

This document contains the exact prompts supplied to evaluated agents during Aster Pilot 001.

Prompts must be reproduced verbatim during execution.

Evaluator annotations, property identifiers, reference states and expected outcomes must not be supplied to the evaluated agent.

---

# 1. Initial Reconstruction Prompt — AI-A

> Review the Aster project materials available to you and reconstruct the current operational state of the project.
>
> Describe what the system currently requires, how its relevant components and behaviors relate to one another, what decisions have already been established, and what remains unresolved.
>
> Base the reconstruction only on the project materials provided to you.
>
> Do not modify any project files.

---

# 2. Transformation T1 — AI-A

> Consolidate the operational explanation of connectivity loss, local buffering and delayed transmission in `operations.md`. Remove redundant operational detail from `architecture.md`, while retaining the architectural relationships needed to describe how buffering and batch transmission fit into the system. Preserve all existing project requirements and decisions.

---

# 3. Transformation T2 — AI-A

> Extend Aster so that buffered observation batches may optionally be compressed before transmission. Document the capability in `architecture.md` and `operations.md`.

---

# 4. Reconstruction Prompt — AI-B

> Review the Aster project materials available to you and reconstruct the current operational state of the project.
>
> Describe what the system currently requires, how its relevant components and behaviors relate to one another, what decisions have already been established, and what remains unresolved.
>
> Base the reconstruction only on the project materials provided to you.
>
> Do not modify any project files.

---

# 5. Transformation T3 — AI-B

> Change Aster's normal observation transmission interval from 10 minutes to 15 minutes and update the project consistently.

---

# 6. Transformation T4 — AI-B

> Add support for a configurable raw-data retention policy to the documented architecture without selecting a retention duration. Update `architecture.md` and `open-issues.md` accordingly.

---

# Prompt Equivalence

The reconstruction prompt supplied to AI-A and AI-B is identical.

This is intentional.

The incoming agent after replacement must not receive additional reconstruction guidance merely because it enters the project later in the trajectory.

Therefore:

\[
Prompt_{Reconstruction,A}=Prompt_{Reconstruction,B}
\]

The project state available to the agents differs by trajectory position.

The reconstruction instruction does not.

---

# Information Boundary

The reconstruction prompt deliberately asks for:

- current requirements;
- relevant relationships;
- established decisions;
- unresolved state.

It does not provide:

- property identifiers;
- property counts;
- relationship identifiers;
- expected relationships;
- ground-truth terminology;
- reference-state notation;
- failure categories;
- conservation criteria;
- expected reconstruction answers.

The prompt therefore specifies the reconstruction task without disclosing the evaluator representation of the project.

---

# Modification Boundary

Reconstruction and transformation are separate stages.

During reconstruction:

> Do not modify any project files.

This prevents reconstruction behavior from changing the object that reconstruction is intended to measure.

File modification begins only when a transformation instruction is supplied.

---

# Prompt Delivery

Each prompt must be supplied independently at the appropriate experimental stage.

The evaluator must not:

- paraphrase the prompt during execution;
- explain ambiguous elements unless required by a predefined protocol;
- remind the agent of previous project properties;
- identify missing properties;
- reveal evaluation criteria;
- reveal the expected reference state;
- provide corrective feedback between transformations unless explicitly permitted by the protocol.

If clarification or additional information is supplied during execution, it must be preserved in the execution record.

---

# Execution Order

The prompt sequence for Pilot 001 is:

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

AI-A receives:

1. the initial Aster artifacts;
2. the initial reconstruction prompt;
3. T1;
4. T2.

AI-B receives the permitted persistent project artifacts resulting from the preceding trajectory, but no conversational state from AI-A.

AI-B then receives:

1. the reconstruction prompt;
2. T3;
3. T4.

---

# Intervention Boundary

The evaluator must not silently repair project artifacts between transformations.

If an agent introduces an error, omission or unauthorized modification, the produced project state must remain distinguishable from the expected reference state.

Any intervention required for methodological or technical reasons must be recorded as a protocol deviation.

---

# Freeze Rule

These prompts are part of the frozen Aster Pilot 001 v1.0 design.

Once execution begins, prompt wording must not be modified in response to agent behavior.

If a prompt is discovered to contain a material methodological defect, record the defect.

A corrected prompt belongs to a subsequent pilot revision rather than being retroactively substituted into the current execution.

---

# Current State

**Prompts:** FROZEN  
**Execution:** NOT STARTED  
**Observed Responses:** NONE
