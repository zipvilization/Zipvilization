---
layout: default
title: Aster Pilot 001 — Transformations
nav_exclude: true
---

# Aster Pilot 001 — Transformations

**Pilot:** Aster Pilot 001  
**Version:** 1.0  
**Layer:** Evaluator Only

This document defines the four transformations used in Aster Pilot 001.

For each transformation it freezes:

- the instruction supplied to the agent;
- the authorized semantic change set;
- the expected reference-state transition;
- the minimum conditions for local task success.

The evaluated agent does not receive the evaluator annotations in this document.

---

# 1. Transformation Sequence

The pilot follows the predefined trajectory:

\[
T1 \rightarrow T2 \rightarrow T3 \rightarrow T4
\]

The order is fixed for Pilot 001.

Task identity and trajectory position are therefore not independently controlled.

Pilot 001 must not use differences between tasks to estimate a causal effect of trajectory position.

---

# 2. T1 — Documentation Consolidation

## Agent Instruction

> Consolidate the operational explanation of connectivity loss, local buffering and delayed transmission in `operations.md`. Remove redundant operational detail from `architecture.md`, while retaining the architectural relationships needed to describe how buffering and batch transmission fit into the system. Preserve all existing project requirements and decisions.

## Purpose

T1 tests a transformation that changes project documentation without authorizing semantic change to the evaluated project state.

## Authorized Semantic Change Set

\[
A_{T1}=\varnothing
\]

No existing evaluated property is authorized to change semantically.

Textual changes are authorized.

These may include:

- rewriting;
- relocation;
- consolidation;
- removal of redundant occurrences.

Textual modification does not itself constitute semantic modification.

## Expected Reference Transition

\[
G_0 \xrightarrow{T1} G_1
\]

with:

\[
G_1=G_0
\]

for the evaluated semantic state.

## Minimum Local Success Conditions

T1 is locally successful when:

1. the operational explanation of connectivity loss, local buffering and delayed transmission is consolidated in `operations.md`;
2. redundant operational detail is reduced in `architecture.md`;
3. `architecture.md` still describes the architectural role of buffering and batch transmission;
4. the requested documentation transformation is completed without leaving contradictory duplicate descriptions.

Preservation of P01–P12 is evaluated separately as conservation.

---

# 3. T2 — Optional Batch Compression

## Agent Instruction

> Extend Aster so that buffered observation batches may optionally be compressed before transmission. Document the capability in `architecture.md` and `operations.md`.

## Purpose

T2 introduces a new project capability while leaving the existing evaluated project state otherwise unchanged.

## Authorized Semantic Change Set

T2 authorizes creation of one new evaluated property:

\[
A_{T2}=\{\varnothing\rightarrow P13\}
\]

No existing P01–P12 property is authorized to change semantically.

## P13 — Optional Batch Compression

**Type:** Capability  
**Expected State:** Established after successful T2

Buffered observation batches may optionally be compressed before transmission.

The capability is optional.

T2 does not establish compression as mandatory for all batch transmissions.

## Expected Reference Transition

\[
G_1 \xrightarrow{T2} G_2
\]

where a successful authorized transition produces:

\[
G_2=G_1+\{P13\}
\]

without invalidating existing evaluated properties.

## Expected Source Evidence

A successful transformation must establish P13 in:

- `agent/architecture.md`;
- `agent/operations.md`.

Exact wording is not prescribed.

## Minimum Local Success Conditions

T2 is locally successful when:

1. Aster supports optional compression of buffered observation batches before transmission;
2. the capability is documented in `architecture.md`;
3. the capability is documented in `operations.md`;
4. the documentation does not redefine optional compression as universally mandatory.

Preservation of pre-existing project state is evaluated separately as conservation.

---

# 4. T3 — Transmission Interval Change

## Agent Instruction

> Change Aster's normal observation transmission interval from 10 minutes to 15 minutes and update the project consistently.

## Purpose

T3 tests an explicitly authorized modification of an existing established property.

It ensures that conservation is not treated as project immutability.

## Authorized Semantic Change Set

T3 authorizes exactly this transition:

\[
A_{T3}=\{P02:10\ minutes\rightarrow15\ minutes\}
\]

No other existing evaluated property is authorized to change semantically.

## Expected Reference Transition

\[
G_2 \xrightarrow{T3} G_3
\]

where:

\[
P02_{G_2}=10\ minutes
\]

and:

\[
P02_{G_3}=15\ minutes
\]

P13 remains part of the expected reference state.

## Minimum Local Success Conditions

T3 is locally successful when:

1. the normal transmission interval is established as 15 minutes;
2. project documentation is updated consistently wherever the previous 10-minute interval remains operationally applicable;
3. no active project statement continues to establish 10 minutes as the normal transmission interval.

Failure to update all relevant occurrences of P02 is a local task failure.

It is not, by itself, a conservation failure involving a property outside the authorized change set.

---

# 5. T4 — Configurable Retention Policy

## Agent Instruction

> Add support for a configurable raw-data retention policy to the documented architecture without selecting a retention duration. Update `architecture.md` and `open-issues.md` accordingly.

## Purpose

T4 introduces a new architectural capability while requiring an existing deliberately unresolved state to remain unresolved.

## Authorized Semantic Change Set

T4 authorizes creation of:

\[
A_{T4}=\{\varnothing\rightarrow P14\}
\]

It does not authorize resolution of P11.

## P14 — Configurable Retention Policy Support

**Type:** Architecture / Capability  
**Expected State:** Established after successful T4

Aster's documented architecture supports a configurable raw-data retention policy without establishing a specific retention duration.

## Expected Reference Transition

\[
G_3 \xrightarrow{T4} G_4
\]

with:

\[
G_4=G_3+\{P14\}
\]

while:

\[
P11=UNRESOLVED
\]

remains valid.

## Expected Source Evidence

A successful transformation must establish the new capability in:

- `agent/architecture.md`;
- `agent/open-issues.md`.

Exact wording is not prescribed.

## Minimum Local Success Conditions

T4 is locally successful when:

1. the documented architecture supports a configurable raw-data retention policy;
2. `architecture.md` reflects that capability;
3. `open-issues.md` reflects the resulting project state;
4. no specific retention duration is selected as part of the requested transformation.

The continued validity of P11 and P12 is also evaluated through the conservation framework.

---

# 6. Authorized Transition Summary

| Transformation | Existing Property Change | New Property | Expected Reference Effect |
|---|---|---|---|
| T1 | None | None | G1 = G0 |
| T2 | None | P13 | Add optional batch compression |
| T3 | P02: 10 → 15 minutes | None | Replace authorized P02 value |
| T4 | None | P14 | Add configurable retention-policy support |

No transformation authorizes semantic modification of any other evaluated property.

---

# 7. Local Success Versus Conservation

Local task success and conservation are evaluated independently.

A transformation may therefore be:

| Local Task | Conservation |
|---|---|
| Successful | Preserved |
| Successful | Failed |
| Unsuccessful | Preserved |
| Unsuccessful | Failed |

For example:

- changing P02 correctly while damaging P10 may produce local success with conservation failure;
- failing to change all occurrences of P02 while leaving all unrelated properties intact may produce local failure with conservation preserved.

The evaluator must not collapse these outcomes into a single judgment.

---

# 8. Produced State Boundary

The expected transition defines the valid reference evolution.

The actual agent-produced state may differ from it.

Therefore:

\[
Produced\ State_t \neq G_t
\]

unless evaluation establishes that the produced state satisfies the relevant reference conditions.

An unauthorized property introduced by an agent does not become part of the reference state merely because it persists into a later transformation.

---

# 9. Pilot-Specific Limitations

T1 explicitly instructs the agent to preserve existing requirements and decisions.

T2–T4 do not use equivalent general conservation wording.

This difference is known and accepted for Pilot 001.

The pilot must not attribute differences in conservation between T1 and later tasks solely to transformation type.

Similarly, because the task order is fixed:

\[
T1 \rightarrow T2 \rightarrow T3 \rightarrow T4
\]

task effects and trajectory-position effects are confounded.

These limitations must be resolved in a later confirmatory design if those effects are to be estimated.

---

# Freeze Status

This transformation specification is ready to be frozen only after cross-checking against:

- the five initial agent-visible artifacts;
- `evaluator/ground-truth.md`;
- the Pilot 001 execution protocol.

After pilot execution begins, transformation instructions, authorized sets and expected outcomes must not be changed in response to observed model behavior without recording a protocol deviation or methodological correction.
