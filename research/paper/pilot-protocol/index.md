---
layout: default
title: Pilot Protocol
parent: Paper
nav_order: 5
description: >
  Execution protocol for the controlled pilot studying project-state
  reconstruction, local transformation and conservation across AI replacement.
permalink: /research/paper/pilot-protocol/
---

# Pilot Protocol

The pilot tests whether the proposed experimental design can produce interpretable observations.

It is not intended to establish the research hypothesis.

The protocol separates three evaluated stages:

**Reconstruction → Local Transformation → Conservation**

and introduces agent replacement without conversational continuity.

---

# 1. Pre-Execution Freeze

Before any evaluated agent accesses the project, freeze:

- reference project state;
- evaluated property set;
- supporting evidence;
- required relationships;
- relevant epistemic states;
- intentionally unresolved state;
- transformation sequence;
- authorized change set for each transformation;
- expected local outcome for each transformation;
- evaluation rules;
- experimental condition assignments.

The frozen material becomes the reference for the pilot.

Any later correction must follow the post-freeze procedure defined in Ground Truth Construction.

---

# 2. Initialize Project State

Each run begins from the same reference state:

\[
P_0
\]

The persistent artifacts presented to the agent are determined by the assigned experimental condition.

Ground truth annotations are not exposed unless they are themselves part of the project artifacts available under that condition.

The agent must not receive evaluator-only information.

---

# 3. Agent Exposure

The first evaluated agent receives:

- the persistent project artifacts assigned to its condition;
- the tools and access mechanisms defined for that condition;
- the instructions required for the reconstruction stage.

No prior conversational state is provided.

The exact model, configuration, available tools and accessible artifacts must be recorded.

---

# 4. Reconstruction Stage

Before modifying the project, the agent is asked to reconstruct the operationally relevant project state required by the protocol.

The reconstruction output is recorded without allowing project modification.

It is then evaluated against the frozen reference properties applicable to RQ1.

This produces a reconstruction observation independent of subsequent task performance.

The reconstruction output must not be manually corrected before the transformation stage.

---

# 5. Transformation Stage

The agent receives transformation \(T_1\).

The task specifies its local objective but does not expose evaluator-only annotations or hidden ground truth.

The agent performs the task using only the information and capabilities available under its experimental condition.

The resulting project state is:

\[
P_0 \xrightarrow{T_1} P_1
\]

All persistent changes produced by the agent are retained for evaluation.

---

# 6. Local Task Evaluation

The transformation is evaluated against the predefined local success criteria.

This evaluation answers RQ2.

Local task success must be determined independently from conservation.

A task is not classified as locally successful merely because the resulting project remains coherent.

Likewise, conservation failure does not automatically imply local task failure.

---

# 7. Conservation Evaluation

The resulting project state is evaluated against the relevant properties outside the authorized change set.

This evaluation answers RQ3.

The evaluator determines whether valid project meaning was preserved and records any applicable failure categories defined in the Research Questions methodology.

Conservation evaluation must not redefine the authorized scope after observing the result.

---

# 8. Persist Resulting State

If the protocol continues the trajectory, the resulting valid experimental state becomes the persistent input for the next stage according to the predefined procedure.

The study must distinguish between:

**agent-produced state**

and

**evaluator-corrected state**.

Evaluator corrections must not be silently inserted into a continuing trajectory.

If a failure makes continuation uninterpretable, the predefined protocol must determine whether the trajectory:

- continues with the produced state;
- branches from the last valid state;
- is stopped;
- or is repeated under a documented correction.

This rule must be fixed before outcome analysis.

---

# 9. Agent Replacement

At a predefined replacement point, the current agent is removed.

The replacement agent receives no conversational state from its predecessor.

It receives only:

- the persistent project artifacts allowed by the experimental condition;
- the tools and access mechanisms assigned to that condition;
- the instructions required by the next protocol stage.

The replacement agent then performs a new reconstruction before receiving the next transformation.

Conceptually:

\[
AI_A
\rightarrow
P_1
\rightarrow
AI_B
\]

not:

\[
AI_A
\rightarrow
Conversation
\rightarrow
AI_B
\]

The persistent project is the continuity mechanism under study.

---

# 10. Repeat

The sequence can then repeat:

\[
P_t
\rightarrow
Reconstruction
\rightarrow
T_{t+1}
\rightarrow
P_{t+1}
\rightarrow
Evaluation
\rightarrow
Replacement
\]

The number and location of replacement events must be fixed for a given pilot design before execution.

They should not be increased or reduced in response to observed performance.

---

# 11. Preserve Raw Outputs

The pilot must retain the original experimental record required for later audit.

This includes, where technically available:

- model inputs;
- model outputs;
- tool interactions;
- persistent artifacts before and after each transformation;
- reconstruction outputs;
- condition assignment;
- model and configuration metadata;
- evaluation records;
- protocol deviations.

Raw experimental outputs must remain distinguishable from later annotations and analysis.

---

# 12. Protocol Deviations

Any deviation from the frozen protocol must be recorded.

A deviation record should identify:

- what changed;
- when it changed;
- why it changed;
- which runs were affected;
- whether those runs remain interpretable.

A protocol deviation must not be hidden because it appears methodologically harmless.

---

# 13. Pilot Evaluation

The pilot is evaluated primarily as a test of experimental viability.

It should determine whether:

- reconstruction can be evaluated reliably;
- local task success can be separated from conservation;
- authorization boundaries are sufficiently clear;
- conservation failures can be identified consistently;
- replacement can occur without unintended information transfer;
- conditions remain meaningfully comparable;
- the task is neither trivial nor systematically impossible;
- the resulting records are sufficient for independent audit.

The pilot does not need to support the research hypothesis to succeed methodologically.

---

# 14. Pilot Outcomes

The pilot may produce several valid methodological outcomes.

It may show that the protocol is viable.

It may reveal that ground truth is too ambiguous.

It may reveal that the experimental conditions are not sufficiently isolated.

It may reveal that tasks are too easy or too difficult.

It may reveal that reconstruction or conservation cannot yet be evaluated reliably.

These are findings about the experimental design.

They must not be converted into substantive conclusions about AI behavior without an appropriate study.

---

# 15. No Confirmatory Interpretation

Pilot observations may be used to improve the protocol.

They must not be presented as confirmatory evidence from a study whose design was modified in response to those same observations.

If the pilot leads to material changes in:

- task construction;
- ground truth;
- condition definitions;
- evaluation rules;
- failure taxonomy;
- replacement procedure;

the revised design must be frozen before confirmatory data are collected.

---

# Execution Sequence

The controlled pilot follows this order:

\[
\boxed{
Freeze
\rightarrow
Initialize
\rightarrow
Expose
\rightarrow
Reconstruct
\rightarrow
Evaluate\ Reconstruction
\rightarrow
Transform
\rightarrow
Evaluate\ Local\ Success
\rightarrow
Evaluate\ Conservation
\rightarrow
Persist
\rightarrow
Replace
\rightarrow
Repeat
}
\]

No later stage may retroactively redefine the evaluation criteria of an earlier stage.

---

# Methodological Gate

The pilot protocol is ready for execution only when:

1. the experimental unit exists;
2. ground truth is frozen;
3. conditions are frozen;
4. transformation order is fixed;
5. replacement points are fixed;
6. continuation rules after failure are fixed;
7. evaluation procedures are executable;
8. raw experimental records can be preserved.

The next step is not execution.

It is to define the **evaluation framework** required to convert reconstruction, task and conservation observations into reproducible measurements without introducing arbitrary aggregate scores.
