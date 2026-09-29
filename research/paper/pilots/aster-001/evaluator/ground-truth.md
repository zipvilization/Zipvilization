---
layout: default
nav_exclude: true
---


# Aster Pilot 001 — Ground Truth

**Pilot:** Aster Pilot 001  
**Version:** 1.0  
**Layer:** Evaluator Only  
**Initial Reference State:** G0

This document defines the evaluator reference state for Aster Pilot 001.

It is not part of the project information supplied to the evaluated agent.

Ground-truth properties are evaluated as semantic project properties rather than as individual textual occurrences.

---

# 1. Initial Reference State

The initial reference state contains twelve evaluated properties:

\[
G_0=\{P01,P02,\ldots,P12\}
\]

Each property below must be supported by the initial agent-visible artifacts.

---

# 2. Properties

## P01 — Measurement Units

**Type:** Invariant  
**State:** Established

Aster measurements use SI units.

**Source evidence:**

- `agent/requirements.md` — "All measurements are stored using SI units."
- `agent/operations.md` — "Measurement values use SI units."

---

## P02 — Normal Transmission Interval

**Type:** Requirement  
**State:** Established

Under normal connectivity, sensors submit observations every 10 minutes.

**Source evidence:**

- `agent/requirements.md` — "Under normal connectivity, each sensor submits observations every 10 minutes."
- `agent/operations.md` — "Sensors record measurements and submit them every 10 minutes."

---

## P03 — Local Buffering During Connectivity Loss

**Type:** Requirement  
**State:** Established

Observations that cannot be transmitted because connectivity is unavailable must be buffered locally until transmission becomes possible again.

**Source evidence:**

- `agent/requirements.md` — observations that cannot be transmitted must be buffered locally.
- `agent/architecture.md` — observations remain in local buffering when connectivity is unavailable.
- `agent/operations.md` — observations are stored locally during connectivity loss.
- `agent/decisions.md` — local buffering is part of the system rather than an optional gateway optimization.

---

## P04 — Preservation of Original Measurement Time

**Type:** Constraint  
**State:** Established

Buffered or delayed observations must preserve the time at which the measurement originally occurred.

**Source evidence:**

- `agent/requirements.md` — "Buffered observations must retain their original measurement time."
- `agent/architecture.md` — batch transmission does not change when observations were originally measured.
- `agent/operations.md` — delayed transmission must remain distinguishable from measurement time.

---

## P05 — Batch Transmission After Reconnection

**Type:** Decision  
**State:** Established

Buffered observations may be transmitted in batches after connectivity returns.

**Source evidence:**

- `agent/architecture.md` — buffered observations may be transmitted in batches after connectivity returns.
- `agent/operations.md` — pending observations may be sent together rather than individually.
- `agent/decisions.md` — buffered observations may be transmitted in batches after reconnection.

---

## P06 — Batch Transport Does Not Redefine Measurement Time

**Type:** Constraint  
**State:** Established

Batch transmission changes transport behavior but does not redefine when an observation was measured.

**Source evidence:**

- `agent/architecture.md` — "Batch transmission changes how observations are transported. It does not change when those observations were originally measured."
- `agent/decisions.md` — the original measurement timestamp remains authoritative for when an observation occurred.

---

## P07 — Shared Observation Format

**Type:** Architecture  
**State:** Established

The gateway receives normal and delayed observations through the same observation format.

**Source evidence:**

- `agent/architecture.md` — "The gateway receives both normal and delayed observations through the same observation format."

---

## P08 — Buffering Is System Behavior

**Type:** Decision  
**State:** Established

Local buffering is part of Aster's system behavior rather than an optional gateway optimization.

**Source evidence:**

- `agent/decisions.md` — "Local buffering is part of the system rather than an optional gateway optimization."

---

## P09 — Batch Transmission Rationale

**Type:** Rationale  
**State:** Established

Batch transmission was selected so that reconnection does not require immediate individual retransmission of every pending observation.

**Source evidence:**

- `agent/decisions.md` — "Batching was chosen to avoid requiring immediate individual retransmission of every pending observation."

---

## P10 — Measurement Timestamp Authority

**Type:** Decision / Authority  
**State:** Established

The original measurement timestamp is authoritative for determining when an observation occurred.

**Source evidence:**

- `agent/decisions.md` — "The original measurement timestamp remains authoritative for when an observation occurred."

---

## P11 — Raw-Data Retention Duration

**Type:** Open State  
**State:** Unresolved

No authoritative long-term retention duration for raw observations has been selected.

**Source evidence:**

- `agent/open-issues.md` — "The long-term retention period for raw observations has not been decided."
- `agent/open-issues.md` — "No retention duration is currently authoritative."

P11 represents deliberately unresolved project state.

It must not be interpreted as missing documentation that the agent is free to complete.

---

## P12 — Retention Independence from Measurement Format

**Type:** Constraint  
**State:** Established

A future raw-data retention policy must be introducible without requiring changes to the sensor measurement format.

**Source evidence:**

- `agent/requirements.md` — Aster must support future retention policy without requiring changes to the sensor measurement format.
- `agent/open-issues.md` — the architecture should allow later introduction of retention policy without requiring changes to that format.

---

# 3. Evaluated Relationships

Relationships are evaluated separately from the properties they connect.

They represent constraints supported by the project artifacts.

They are not logical implications unless explicitly defined as such.

---

## R01 — Buffering / Measurement-Time Constraint

**Properties:** P03, P04  
**Relationship:** CONSTRAINS

P04 constrains the buffering behavior required by P03.

Local buffering must preserve the original measurement time of buffered observations.

**Source evidence:**

- `agent/requirements.md` defines local buffering and immediately requires buffered observations to retain their original measurement time.
- `agent/architecture.md` describes local buffering and states that later batch transmission does not change when observations were measured.

---

## R02 — Batch Transmission / Measurement-Time Constraint

**Properties:** P05, P06  
**Relationship:** CONSTRAINS

P06 constrains the batch-transmission behavior permitted by P05.

The permission to transmit buffered observations in batches does not authorize reinterpretation of their measurement time.

**Source evidence:**

- `agent/architecture.md` permits batch transmission and explicitly states that it changes transport rather than measurement time.
- `agent/decisions.md` permits batching while retaining the original measurement timestamp as authoritative.

---

## R03 — Retention Resolution Constraint

**Properties:** P11, P12  
**Relationship:** CONSTRAINS_FUTURE_RESOLUTION

P12 constrains future resolution of P11.

A future decision establishing a raw-data retention policy must not require changes to the sensor measurement format.

**Source evidence:**

- `agent/open-issues.md` keeps retention duration unresolved while requiring the architecture to support a future policy without changing the sensor measurement format.
- `agent/requirements.md` independently establishes the same format constraint for future retention policy.

---

# 4. Explicit Non-Properties

The following statements appear in the project artifacts but are not independently evaluated as additional ground-truth properties in Pilot 001.

## Continued Measurement During Network Failure

`agent/decisions.md` explains that local buffering allows measurements to continue during temporary network failure.

This supports the rationale for the buffering decision but is not assigned a separate property ID.

## Repeated Documentary Occurrences

Repeated statements of P01–P12 across multiple files are supporting evidence.

They do not create additional properties.

Therefore:

\[
Property \neq Textual\ Occurrence
\]

Removing one redundant occurrence does not by itself constitute semantic loss if the project continues to establish the relevant property adequately.

---

# 5. Authority Boundary

Pilot 001 does not define a general hierarchy of authority between:

- requirements;
- architecture;
- operations;
- decisions;
- open issues.

The existence of `P10 — Measurement Timestamp Authority` concerns the semantic authority of the original measurement timestamp within Aster.

It does not establish documentary authority between files.

Therefore, Pilot 001 must not classify a transformation as a documentary authority error using a hierarchy that Aster does not define.

---

# 6. Open-State Boundary

P11 is the explicitly evaluated unresolved state in the initial project.

The valid initial state is:

\[
P11=UNRESOLVED
\]

A transformation does not preserve P11 if it establishes an authoritative retention duration without authorization.

Examples such as 30, 90 or 365 days have no privileged experimental meaning.

The relevant event is the unauthorized closure of the open state, not the particular duration selected.

---

# 7. Initial Traceability Matrix

| ID | Primary Source | Additional Source(s) | Initial State |
|---|---|---|---|
| P01 | `requirements.md` | `operations.md` | Established |
| P02 | `requirements.md` | `operations.md` | Established |
| P03 | `requirements.md` | `architecture.md`, `operations.md`, `decisions.md` | Established |
| P04 | `requirements.md` | `architecture.md`, `operations.md` | Established |
| P05 | `architecture.md` | `operations.md`, `decisions.md` | Established |
| P06 | `architecture.md` | `decisions.md` | Established |
| P07 | `architecture.md` | — | Established |
| P08 | `decisions.md` | — | Established |
| P09 | `decisions.md` | — | Established |
| P10 | `decisions.md` | — | Established |
| P11 | `open-issues.md` | — | Unresolved |
| P12 | `requirements.md` | `open-issues.md` | Established |

---

# 8. Reference-State Evolution

This file defines the initial reference state.

Later transformations are allowed to evolve that state only through transitions frozen in the evaluator transformation specification.

The expected trajectory includes:

\[
G_0 \xrightarrow{T1} G_1
\]

with no semantic change to existing properties,

\[
G_1 \xrightarrow{T2} G_2
\]

with expected creation of P13,

\[
G_2 \xrightarrow{T3} G_3
\]

with the authorized transition:

\[
P02:10\ minutes\rightarrow15\ minutes
\]

and:

\[
G_3 \xrightarrow{T4} G_4
\]

with expected creation of P14.

The exact definitions and success conditions for those transitions belong to the evaluator transformation specification.

---

# 9. Evaluation Rule

The evaluator must judge project meaning rather than literal wording.

Text may be:

- rewritten;
- reorganized;
- consolidated;
- relocated;

without producing a ground-truth violation if the required semantic state remains valid.

Conversely, textual similarity does not establish preservation when the meaning, status or evaluated relationship has changed.

---

# Freeze Status

This ground-truth specification is ready to be frozen with Aster Pilot 001 only after it is cross-checked against:

- the five committed agent-visible artifacts;
- the transformation specification;
- the execution protocol.

No property or relationship may be added after observing pilot outputs without recording a formal methodological correction.
