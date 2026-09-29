---
layout: default
title: Evaluation Framework
parent: Paper
nav_order: 6
description: >
  Evaluation framework for measuring reconstruction, local task success and
  conservation without collapsing distinct outcomes into a premature aggregate score.
permalink: /research/paper/evaluation-framework/
---

# Evaluation Framework

The evaluation framework measures three distinct outcomes:

**Reconstruction**

**Local Task Success**

**Conservation**

They must remain separately observable.

No single aggregate score is defined at this stage.

---

# 1. Evaluation Unit

The primary evaluation unit is a predefined project property within a specific experimental stage.

For each relevant property, evaluation asks whether its required meaning, status and relationships were correctly reconstructed or preserved.

The framework evaluates semantic state rather than textual identity.

---

# 2. Reconstruction Evaluation

Reconstruction is evaluated before project modification.

For each reference property relevant to RQ1, the agent's reconstruction is classified according to whether the required project state was recovered.

The initial categories are:

**Recovered** — the reconstruction preserves the required meaning.

**Partially recovered** — some required meaning is present, but relevant information is missing or incomplete.

**Incorrect** — the reconstruction conflicts with the reference state.

**Not recovered** — the relevant property is absent from the reconstruction.

Where relevant, evaluation must also consider whether:

- authority was reconstructed correctly;
- epistemic status was reconstructed correctly;
- required relationships were reconstructed correctly;
- explicitly unresolved state remained unresolved.

These observations should remain distinguishable rather than being silently collapsed into one judgment.

---

# 3. Local Task Success

Local task success is evaluated only against criteria frozen before execution.

Each required outcome is classified according to whether it was achieved.

The initial categories are:

**Satisfied**

**Partially satisfied**

**Not satisfied**

A task-level result may be derived from its predefined requirements, but the aggregation rule must be specified before confirmatory execution.

Conservation must not influence the local task rating unless preservation is itself an explicit requirement of that task.

---

# 4. Conservation Evaluation

Conservation is evaluated against relevant valid properties outside the authorized change set.

For each such property, the evaluator determines whether the transformation:

**Preserved** — retained the required semantic state.

**Degraded** — retained some relevant meaning but introduced a material loss or distortion.

**Violated** — produced a state incompatible with the frozen reference requirement.

**Not assessable** — available evidence is insufficient for a reliable judgment.

`Not assessable` is not equivalent to preservation.

It is also not equivalent to failure.

---

# 5. Failure Labels

Where degradation or violation occurs, one or more predefined failure labels may be attached:

- Omission
- Contradiction
- Unauthorized modification
- Relationship loss
- Authority or status error
- Premature closure
- Historical distortion

The severity classification and failure label answer different questions.

For example, a relationship loss may be either a degradation or a violation depending on its effect on the reference property.

---

# 6. Authorized Changes

Properties inside the authorized change set are not evaluated as conservation failures merely because they changed.

They are evaluated against the expected local outcome and any task-specific constraints defined before execution.

This prevents legitimate project evolution from being classified as degradation.

---

# 7. Semantic Equivalence

Different wording does not constitute failure when the required meaning remains equivalent.

Likewise, textual similarity does not establish preservation when meaning, authority, status or relationships have changed.

Where semantic equivalence requires evaluator judgment, that judgment must be recorded as such.

The framework must not substitute lexical similarity for semantic correctness without prior validation.

---

# 8. Evaluator Evidence

Every non-trivial evaluation judgment should be traceable to:

- the relevant frozen reference property;
- the model output or resulting artifact;
- the applicable evaluation rule.

Evaluators should not introduce project requirements that are absent from the frozen ground truth.

If a case exposes missing or ambiguous ground truth, it should be recorded as a methodological issue rather than resolved in favor of either experimental condition.

---

# 9. Independent Evaluation

Where feasible, outputs should be evaluated independently by more than one evaluator without revealing experimental condition or research expectation.

Evaluator disagreement must be preserved until the predefined adjudication procedure is applied.

Agreement should be reported using a method appropriate to the eventual annotation structure.

No agreement coefficient is selected before that structure is finalized.

---

# 10. Automated Evaluation

Mechanically verifiable properties may be evaluated automatically where the procedure has a clear relationship to the property being measured.

Examples may include:

- presence of required structured fields;
- deterministic dependency constraints;
- predefined test outcomes;
- machine-verifiable state transitions.

Automated checks must not be treated as evidence of semantic conservation beyond what they actually test.

---

# 11. AI-Assisted Evaluation

An AI system may assist evaluation only under a separately defined and validated procedure.

It must not become the unexamined authority for judging another AI system's semantic correctness.

If AI-assisted evaluation is used, the study must document:

- evaluator model and configuration;
- information supplied to it;
- evaluation instructions;
- validation against independent reference judgments;
- known limitations.

AI evaluation must remain distinguishable from ground truth.

---

# 12. Missing and Ambiguous Cases

The evaluation framework must preserve uncertainty when the evidence does not support a reliable classification.

Ambiguous cases must not be forced into success or failure categories solely to simplify analysis.

The frequency and causes of non-assessable cases may themselves reveal weaknesses in the experimental design.

---

# 13. Trajectory-Level Observation

Property-level observations may later be examined across successive transformations:

\[
P_0 \rightarrow P_1 \rightarrow \ldots \rightarrow P_n
\]

This allows the study to observe whether errors:

- appear once;
- persist;
- accumulate;
- propagate through dependencies;
- are later corrected;
- create downstream failures.

No trajectory-level aggregate metric is defined yet.

The longitudinal record should be preserved before deciding how it can be summarized validly.

---

# 14. No Premature Composite Score

The initial framework does not define:

\[
Score = w_1R + w_2L + w_3C
\]

or any equivalent weighted composite.

Such a score would require justification for:

- combining distinct constructs;
- assigning weights;
- treating categories as numerical distances;
- handling missing observations;
- interpreting trade-offs.

Those assumptions are not currently established.

Results should therefore remain multidimensional until evidence supports a valid aggregation method.

---

# 15. Pilot Evaluation Criteria

The pilot should determine whether:

1. reference properties can be evaluated consistently;
2. reconstruction categories are sufficiently discriminative;
3. local success criteria produce reproducible judgments;
4. conservation categories distinguish meaningful outcomes;
5. failure labels can be applied consistently;
6. semantic equivalence can be judged with acceptable reliability;
7. non-assessable cases remain limited enough for interpretation;
8. automated checks correspond to the properties they claim to evaluate.

Failure of these criteria indicates that the evaluation framework requires revision before confirmatory experimentation.

---

# Reporting Principle

Results should expose the underlying observations before presenting summaries.

At minimum, reporting must preserve the distinction:

\[
\boxed{
Reconstruction \neq Local\ Task\ Success \neq Conservation
}
\]

A model or representation may perform differently across these dimensions.

No overall claim of superiority should conceal those differences.

---

# Methodological Gate

The evaluation framework is ready for confirmatory use only after the pilot demonstrates that its categories and judgments can be applied with sufficient consistency.

Only then should the study determine:

- which variables can be represented quantitatively;
- which statistical comparisons are appropriate;
- whether any aggregation is justified;
- what sample size is required.

The next step is therefore **pilot construction**, not metric invention.
