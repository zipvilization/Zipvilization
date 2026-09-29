---
layout: default
title: When Better Becomes Worse
parent: Research
nav_order: 2
description: >
  A research article on local optimization, accumulated transformation and
  global conservation in long-horizon AI work. Can every individual change
  appear successful while the project itself becomes progressively worse?
permalink: /research/when-better-becomes-worse/
---

# When Better Becomes Worse

## Local Optimization, Accumulated Transformation and Global Conservation in Long-Horizon AI Work

**TYPE:** Research Article / Conceptual Hypothesis  
**STATUS:** Open  
**BASED ON:** Zipvilization development experience, 2023–2026  
**EXTERNAL RESEARCH:** Yes  
**EMPIRICALLY VALIDATED:** Partially supported by related external evidence; project-level generalization unresolved  
**GENERALIZABILITY:** Unresolved  
**LAST REVIEWED:** 2026-09-29

---

# Abstract

Can every individual change to a project appear successful while the project itself becomes progressively worse?

During several years of Human–AI development of Zipvilization, we repeatedly encountered this pattern.

An AI would improve a document.

Then another.

Then another.

Each transformation could be locally correct, clearer and apparently more complete.

Yet across the sequence, valid information disappeared.

Dependencies weakened.

Historical distinctions collapsed.

Experimental ideas became established facts.

Canonical relationships drifted.

The parts improved.

The whole degraded.

We described this pattern as:

# **GOOD LOCAL GENERATION**
+
# **INSUFFICIENT GLOBAL CONSERVATION**

or more simply:

# **LOCALLY BETTER**
# **GLOBALLY WORSE**

External research now provides important neighboring evidence.

Software engineering has long studied design and architecture erosion produced by accumulated change.

Recent long-horizon AI benchmarks have found progressive structural degradation, loss of specification fidelity, regression problems and trajectory-induced degradation across extended agentic work.

These findings mean that the general observation that iterative change can degrade a system is not new.

Our question is narrower in one direction and broader in another.

What happens when the object being preserved is not only code quality or task success, but the **semantic structure of an evolving project**?

We propose that long-horizon Human–AI work may require evaluating not only individual transformations but the **trajectory of project states those transformations produce**.

The central question becomes:

> **Should long-horizon AI be evaluated on transformations, or on trajectories?**

Our hypothesis is that both are necessary.

A transformation can be locally successful while contributing to a globally destructive trajectory.

If that is correct, task success alone is an incomplete measure of long-horizon AI performance.

---

# 1. A Simple Paradox

Imagine an AI makes ten changes to a project.

After every change, we ask:

> Is this change good?

And every time the answer is:

> Yes.

After the tenth change, we examine the complete project.

It is worse.

How can that happen?

At first, the situation appears contradictory.

If:

**Change 1 = good**

**Change 2 = good**

**Change 3 = good**

...

**Change 10 = good**

should the result not also be good?

Not necessarily.

The error is assuming that:

# **LOCAL SUCCESS IS ADDITIVE**

It may not be.

---

# 2. The Object of Evaluation

Most task-oriented evaluation asks:

> **Did the system successfully perform transformation T?**

But a persistent project creates another object:

> **What state did transformation T leave behind for the next transformation?**

Those are different questions.

Let:

**Pₜ** = project state before transformation **t**

**Tₜ** = transformation performed at step **t**

Then:

**Tₜ(Pₜ) → Pₜ₊₁**

Ordinary evaluation focuses primarily on:

**Tₜ**

Long-horizon evaluation must also care about:

**Pₜ₊₁**

because:

**Pₜ₊₁**

becomes the environment in which:

**Tₜ₊₁**

must operate.

---

# 3. A Transformation Changes the Future

This gives us a fundamental relationship:

```text
PROJECT STATE
     │
     ▼
TRANSFORMATION
     │
     ▼
NEW PROJECT STATE
     │
     ▼
ENVIRONMENT FOR NEXT TRANSFORMATION
```

A transformation therefore has two outputs.

The obvious output is:

**the requested result**

The less obvious output is:

**the new starting condition for everything that follows**

That second output may be more important over long horizons.

---

# 4. Immediate Success vs Residual State

Suppose an AI modifies a project correctly.

The immediate task succeeds.

But during the transformation it also:

duplicates logic,

weakens an abstraction,

removes useful context,

loses a dependency,

flattens a historical distinction,

or introduces an undocumented assumption.

None of those losses may prevent the current task from succeeding.

But they alter the residual project state.

So:

# **CURRENT TASK SUCCESS**
does not imply
# **FUTURE PROJECT HEALTH**

This distinction is already familiar in software engineering.

Long-horizon AI makes it newly important.

---

# 5. Zipvilization's Failure Pattern

During the development of Zipvilization, the most dangerous AI failures were rarely obvious nonsense.

They were often excellent outputs.

A rewritten page could be:

better organized,

more concise,

more readable,

more technically polished,

and locally more coherent.

But comparison against the wider project sometimes revealed that it had:

removed valid information,

redefined a concept,

lost a dependency,

collapsed two epistemically different statements,

rewritten History,

or transformed an unresolved question into an answer.

The page improved.

The project did not.

---

# 6. Good Local Generation

We call the first half of the phenomenon:

# **GOOD LOCAL GENERATION**

The AI performs the immediate transformation well.

Let:

**Lₜ**

represent local quality at transformation **t**.

A locally successful transformation satisfies:

**ΔLₜ > 0**

The transformed artifact is better according to the local objective.

That alone tells us nothing about the rest of the project.

---

# 7. Global Conservation

Now define:

**Gₜ**

as a conceptual measure of global project coherence after transformation **t**.

A transformation can satisfy:

**ΔLₜ > 0**

while:

**ΔGₜ < 0**

Therefore:

# **LOCAL IMPROVEMENT ⇏ GLOBAL IMPROVEMENT**

This is the mathematical core of the problem.

---

# 8. The Stronger Failure

The more interesting case occurs across repeated transformations.

Suppose:

**ΔL₁ > 0**

**ΔL₂ > 0**

**ΔL₃ > 0**

...

**ΔLₙ > 0**

Every individual task improves its target.

Yet:

**Gₙ < G₀**

The final project is globally less coherent than the original.

So it is possible that:

# **∀t, ΔLₜ > 0**

while:

# **G(Pₙ) < G(P₀)**

Every evaluated local step succeeds.

The trajectory fails.

---

# 9. This Is Not a New Software Problem

The general pattern has deep precedents.

Software engineering has studied:

**design erosion**

**architecture erosion**

**technical debt**

**regression**

**change-impact analysis**

**requirements traceability**

**software evolution**

for decades.

Architecture erosion is particularly relevant.

A software system can undergo repeated modifications that gradually move its implementation away from intended architectural principles.

One modification may be harmless.

Accumulated modifications may not be.

This matters because our claim should not be:

> We discovered that repeated changes can degrade systems.

We did not.

The more interesting question is what changes when **Artificial Intelligence becomes a high-speed transformation engine inside that process**.

---

# 10. Architecture Erosion

Classical architecture erosion provides an important analogy.

A system has:

an intended architecture,

an implementation,

and repeated modifications.

Over Time:

```text
INTENDED ARCHITECTURE
          │
          │
          ▼
IMPLEMENTATION₀
          │
       CHANGE
          ▼
IMPLEMENTATION₁
          │
       CHANGE
          ▼
IMPLEMENTATION₂
          │
       CHANGE
          ▼
IMPLEMENTATION₃
          │
          ▼
      POSSIBLE
      EROSION
```

The danger is cumulative divergence.

But Operational Project Alignment concerns a broader object than software architecture alone.

---

# 11. Beyond Code

A long-lived AI-assisted project may contain:

code,

documentation,

requirements,

decisions,

concepts,

terminology,

historical records,

datasets,

design rationale,

epistemic states,

authority structures,

open questions,

and future direction.

The project is not only its implementation.

It is a semantic system.

That suggests another form of erosion:

# **PROJECT-LEVEL SEMANTIC EROSION**

We use this phrase descriptively here.

We are not proposing it as an established technical term.

It refers to progressive loss or distortion of still-valid project meaning across accumulated transformations.

---

# 12. What Can Be Lost?

Semantic erosion may involve loss of:

**facts**

**relationships**

**rationale**

**provenance**

**authority**

**historical distinctions**

**uncertainty**

**terminological precision**

**unresolved questions**

**boundaries between representation and reality**

These losses may occur without making the current output obviously wrong.

That is precisely what makes them dangerous.

---

# 13. A Project Is More Than Its Files

Let a project be:

**P = (N, R, H, E, A)**

where:

**N** = meaningful project nodes

**R** = relationships among them

**H** = relevant historical trajectory

**E** = epistemic states

**A** = authority structure

This is not intended as a complete universal model.

It is sufficient to demonstrate the problem.

A transformation can preserve every file while damaging **R**.

It can preserve **N** and **R** while misrepresenting **H**.

It can preserve all three while confusing **E**.

It can retrieve all information while ignoring **A**.

Therefore:

# **FILE PRESERVATION ≠ PROJECT CONSERVATION**

---

# 14. Semantic State

Let:

**Sₜ**

represent the meaningful semantic state of the project at time **t**.

Then a transformation produces:

**Sₜ → Sₜ₊₁**

A valid transformation may legitimately alter part of **Sₜ**.

The conservation problem is not:

> Preserve everything.

It is:

> Preserve everything that remains valid unless its transformation is justified.

That distinction is fundamental.

---

# 15. Conservation Is Not Freezing

A project that cannot change is not healthy.

So:

# **CONSERVATION ≠ IMMUTABILITY**

and:

# **CONSERVATION ≠ COPY PRESERVATION**

A project can change radically while preserving its valid identity.

The objective is not textual stability.

It is semantic continuity.

---

# 16. Correct but Incomplete

This produces one of the most useful distinctions from our own work:

# **CORRECT BUT INCOMPLETE ≠ INCORRECT**

Suppose an existing artifact contains:

**V = valid information**

and new work contributes:

**N = new valid information**

A destructive rewrite may produce:

**V → N**

A reconstructive transformation produces:

**V → V + N**

unless some part of **V** has been explicitly shown to be invalid.

This sounds simple.

In practice, it changes the entire editing strategy.

---

# 17. Rewrite vs Reconstruction

A rewriting model asks:

> How can I produce the best version of this artifact now?

A reconstruction model asks:

> What is valid here, what is wrong, what is missing, what depends on it, and what am I justified in changing?

Conceptually:

```text
REWRITE

OLD
 │
 ▼
GENERATE
 │
 ▼
NEW


RECONSTRUCT

OLD
 │
 ├──► VALID ───────────────┐
 │                         │
 ├──► INVALID ──► CORRECT  │
 │                         ├──► NEW
 └──► INCOMPLETE ─► EXTEND │
                           │
NEW KNOWLEDGE ─────────────┘
```

The second process explicitly models conservation.

---

# 18. The History of a Project Matters

Consider two identical current documents.

One reached its current form through a deliberate canonical decision.

The other reached it through an accidental deletion followed by reconstruction.

Textually they may now be identical.

Historically they are not.

Why does that matter?

Because future interpretation may depend on:

why a decision exists,

what it replaced,

what alternatives were rejected,

what remains unresolved,

and what must not be inferred from the current state.

So:

# **CURRENT STATE ≠ COMPLETE PROJECT MEANING**

---

# 19. Long-Horizon AI Research Is Catching Up

Recent AI research increasingly recognizes that long-horizon work cannot be understood as a collection of independent short tasks.

Benchmarks now study:

iterative coding,

repository evolution,

emergent specifications,

continuous integration,

trajectory failures,

memory limitations,

and accumulated degradation.

This is an important shift.

The evaluation object is moving from:

# **ANSWER**

toward:

# **TRAJECTORY**

---

# 20. SlopCodeBench

In 2026, **SlopCodeBench** examined coding agents that repeatedly extend their own previous solutions under evolving specifications.

Its central observation is directly relevant:

code can continue satisfying immediate requirements while becoming progressively harder to extend.

The benchmark tracks trajectory-level structural signals rather than only final functional success.

In its reported experiments, structural erosion increased across most trajectories, as did code verbosity.

Importantly, improving the initial prompt could improve initial quality without stopping the longer-term degradation.

This provides empirical evidence for a neighboring phenomenon:

# **BETTER INITIAL LOCAL BEHAVIOR DOES NOT NECESSARILY PREVENT TRAJECTORY DEGRADATION**

But SlopCodeBench studies code structure.

Our question extends beyond code structure toward project meaning.

---

# 21. SLUMP

Another 2026 study introduced **SLUMP — Faithfulness Loss Under Emergent Specification**.

The problem is different.

Instead of giving an agent the complete specification at the beginning, requirements are progressively disclosed through a long interaction.

The agent must preserve earlier commitments while integrating later ones.

The study found measurable losses in final implementation fidelity compared with a single-shot specification condition.

This is extremely close to one part of our own experience.

A project is not always fully specified at the beginning.

It emerges.

---

# 22. ProjectGuard

The same work introduced **ProjectGuard**, an external project-state layer for tracking committed knowledge and repository structure.

In one evaluated setting, this external state recovered a large part of the measured faithfulness gap.

This result matters to our Research for a specific reason.

It provides evidence that:

# **EXTERNALIZED PROJECT STATE CAN HELP PRESERVE LONG-HORIZON FIDELITY**

That does not validate Operational Project Alignment.

ProjectGuard is not our five-part architecture.

SLUMP is not our Global Conservation problem.

But the result supports a foundational assumption:

> Persistent external project representation can matter.

---

# 23. SWE-CI

**SWE-CI** shifts evaluation from static bug fixing toward long-term repository maintenance through Continuous Integration.

Its motivation is important:

functional correctness at one point in Time is not sufficient to evaluate maintainability across software evolution.

Again:

# **CURRENT SUCCESS ≠ FUTURE HEALTH**

This is the same structural distinction appearing from another direction.

---

# 24. SWE-EVO and Sequential Evolution

Other recent benchmarks similarly evaluate coordinated changes across evolving repositories rather than isolated issues.

The direction of travel is clear.

AI evaluation is beginning to recognize that:

# **SOFTWARE DEVELOPMENT IS A TRAJECTORY**

not merely a sequence of unrelated tasks.

Our question is whether this principle should be generalized further:

# **A PERSISTENT PROJECT IS A TRAJECTORY**

---

# 25. Trajectory-Induced Degradation

Recent work on long-horizon evaluation has proposed distinguishing ordinary compounding error from **trajectory-induced degradation**.

This distinction is valuable.

A long task can fail simply because many independent stages create many opportunities for error.

But something more interesting can happen:

earlier execution can alter the environment in ways that make later execution harder.

Conceptually:

```text
ERROR ACCUMULATION

TASK 1   TASK 2   TASK 3   TASK 4
  x        x        x        x

More tasks
=
more opportunities for independent error


TRAJECTORY-INDUCED DEGRADATION

TASK 1
  │
  ▼
STATE 1
  │
  ▼
TASK 2 becomes harder
  │
  ▼
STATE 2
  │
  ▼
TASK 3 becomes harder still
```

The second case is much closer to the problem investigated here.

---

# 26. But Our Object Is Different

Long-horizon agent research often studies:

task completion,

planning failure,

context degradation,

tool errors,

code quality,

or implementation fidelity.

We are interested in an additional object:

# **GLOBAL PROJECT CONSERVATION**

Did the project preserve the valid semantic structure required for future coherent work?

That may include code.

But it may also include everything around the code.

---

# 27. Transformation Evaluation

Suppose an AI is asked:

> Rewrite this documentation page to explain the system more clearly.

The result may be evaluated on:

accuracy,

clarity,

completeness,

style,

and immediate consistency.

Call this:

**Transformation Evaluation**

Formally:

**E(Tₜ)**

It evaluates the change.

---

# 28. Trajectory Evaluation

Now ask:

After this transformation:

Did every still-valid relationship survive?

Did another page become contradictory?

Was historical information lost?

Did a hypothesis become a fact?

Did an unresolved question become closed?

Did terminology drift?

Did the change increase the probability of future errors?

Call this:

**Trajectory Evaluation**

It evaluates:

**P₀ → P₁ → ... → Pₜ**

not merely:

**Tₜ**

---

# 29. The Central Proposal

Our central proposal is therefore:

# **LONG-HORIZON AI SHOULD BE EVALUATED ON BOTH TRANSFORMATIONS AND TRAJECTORIES**

A transformation can succeed.

A trajectory can fail.

Those statements can be simultaneously true.

---

# 30. Transformation Success Is Necessary

We should not overcorrect.

If an AI cannot perform the local task correctly, global conservation does not rescue it.

Therefore:

# **LOCAL CORRECTNESS REMAINS NECESSARY**

The claim is only:

# **LOCAL CORRECTNESS MAY NOT BE SUFFICIENT**

---

# 31. A Two-Axis Evaluation

The simplest representation is:

```text
                     GLOBAL CONSERVATION
                            HIGH
                             ▲
                             │
          CONSERVATIVE      │      DESIRED
          BUT WEAK          │      REGION
                             │
                             │
                             │
LOW LOCAL ──────────────────┼──────────────────► HIGH LOCAL
QUALITY                      │                    QUALITY
                             │
                             │
          FAILURE            │      LOCALLY GOOD
          REGION             │      GLOBALLY BAD
                             │
                             ▼
                            LOW
                     GLOBAL CONSERVATION
```

The region that interests us is:

# **HIGH LOCAL QUALITY**
+
# **HIGH GLOBAL CONSERVATION**

---

# 32. The Dangerous Quadrant

The most deceptive quadrant is:

# **HIGH LOCAL QUALITY**
+
# **LOW GLOBAL CONSERVATION**

Why?

Because the output looks successful.

The failure is not visible from the transformed artifact alone.

This is:

# **LOCALLY BETTER**
# **GLOBALLY WORSE**

---

# 33. Accumulation

Let:

**P₀**

be the initial project.

After **n** transformations:

**Pₙ = Tₙ(...T₂(T₁(P₀)))**

Suppose every transformation passes local evaluation:

**E(Tₜ) ≥ threshold**

for all:

**t = 1 ... n**

That still does not imply:

**C(Pₙ) ≥ C(P₀)**

where **C** represents global coherence.

This gives us the formal statement:

# **∀t: E(Tₜ) ≥ θ**
# **⇏**
# **C(Pₙ) ≥ C(P₀)**

A sequence of acceptable transformations can produce an unacceptable trajectory.

---

# 34. Semantic Conservation Set

To reason about conservation, define:

**Vₜ**

as the set of project elements valid at time **t**.

Not every element of **Vₜ** must survive.

Some changes deliberately supersede earlier information.

So define:

**Vₜ⁺**

as the subset of elements from **Vₜ** that should remain valid after transformation **Tₜ**.

A conservation failure occurs when an element:

**v ∈ Vₜ⁺**

is absent, contradicted or semantically corrupted in:

**Pₜ₊₁**

without justification.

---

# 35. Relationship Conservation

Facts alone are not enough.

Define:

**Rₜ⁺**

as the set of relationships that should remain valid after transformation.

A project can preserve all relevant nodes while losing their connections.

For example:

```text
BEFORE

A ──► B ──► C


AFTER

A     B ──► C
```

Nothing was deleted.

But the project changed.

So conservation must include:

# **NODES**
and
# **RELATIONSHIPS**

---

# 36. Epistemic Conservation

Now consider:

```text
BEFORE

X = HYPOTHESIS


AFTER

X = FACT
```

The text describing **X** may barely change.

But its epistemic meaning has changed radically.

Therefore global conservation must also consider:

# **EPISTEMIC STATUS**

This is one place where project-level semantic conservation exceeds ordinary textual preservation.

---

# 37. Historical Conservation

Another example:

```text
BEFORE

2024:
X was explored.

2025:
X was rejected.

2026:
Y is canonical.
```

A summary that says:

> X and Y are project approaches.

has retained information.

It has destroyed History.

So:

# **INFORMATION RETENTION ≠ HISTORICAL CONSERVATION**

---

# 38. Authority Conservation

Suppose:

**Document A = Canon**

**Document B = Experiment**

Both mention conflicting interpretations.

An AI retrieves both.

If it merges them into a compromise, it may appear sophisticated.

But it has destroyed authority structure.

Therefore:

# **SYNTHESIS CAN BE A CONSERVATION FAILURE**

This is particularly important for generative AI, which is often rewarded for producing coherent synthesis.

Sometimes the correct behavior is not synthesis.

It is contradiction preservation.

---

# 39. Preserve the Conflict

If two authoritative states genuinely conflict, the correct output may be:

# **UNRESOLVED CONTRADICTION**

not:

# **SMOOTH COMBINATION**

This gives us another important principle:

> **Global coherence does not require pretending that every source agrees.**

Sometimes coherence requires representing disagreement accurately.

---

# 40. A Provisional Conservation Model

Let:

**N** = node preservation

**R** = relationship preservation

**H** = historical preservation

**E** = epistemic preservation

**A** = authority preservation

Then a conceptual project conservation vector is:

# **Cᵥ = [N, R, H, E, A]**

We deliberately avoid collapsing this into one number.

Different failure modes may produce very different profiles.

---

# 41. Why a Single Score Is Dangerous

Consider:

```text
SYSTEM A

Nodes preserved            100%
Relationships preserved     60%
History preserved           40%
Epistemic status            50%
Authority                    50%


SYSTEM B

Nodes preserved             90%
Relationships preserved     95%
History preserved           95%
Epistemic status             95%
Authority                    95%
```

A metric based mainly on textual retention could prefer System A.

A semantic project evaluation probably should not.

The weighting problem is itself a Research question.

---

# 42. Global Conservation Ratio

As a deliberately simple starting point, suppose:

**Vₚ**

is the set of previously valid elements expected to remain valid.

And:

**Vₛ**

is the subset successfully preserved.

Then:

# **GCR = |Vₛ| / |Vₚ|**

where:

**GCR = Global Conservation Ratio**

This is not proposed as a validated metric.

It immediately has limitations.

All elements are treated equally.

Relationships are not represented.

Partial semantic corruption is difficult to score.

Importance varies.

But the formulation makes the conservation problem explicit.

---

# 43. Weighted Conservation

A more realistic form could assign weight:

**wᵢ**

to each valid project element.

Then:

# **WGCR = Σ(wᵢ · pᵢ) / Σwᵢ**

where:

**pᵢ = 1**

if element **i** is validly preserved,

and:

**pᵢ = 0**

if it is lost or corrupted.

Intermediate values might represent partial preservation.

Again:

this is a proposed research instrument, not an established metric.

---

# 44. Relationships Complicate Everything

Suppose two nodes each survive:

**A**

and:

**B**

But their canonical relationship:

**A → B**

does not.

Node conservation is perfect.

Project conservation is not.

This suggests that any serious metric must eventually operate on something closer to a graph.

Let:

**P = (N, R)**

Then transformation loss may involve:

**ΔN**

and:

**ΔR**

independently.

---

# 45. Semantic Transformation Loss

A provisional formulation might be:

# **STL(Tₜ) = αLₙ + βLᵣ + γLₕ + δLₑ + εLₐ**

where:

**Lₙ** = unjustified node loss

**Lᵣ** = unjustified relationship loss

**Lₕ** = historical distortion

**Lₑ** = epistemic distortion

**Lₐ** = authority distortion

and:

**α, β, γ, δ, ε**

are weights.

We do not currently know the correct weights.

We do not even know whether a linear model is appropriate.

The purpose of the equation is conceptual:

# **TRANSFORMATION LOSS HAS MULTIPLE DIMENSIONS**

---

# 46. Trajectory Conservation

For a sequence of transformations:

**τ = {T₁, T₂, ..., Tₙ}**

we can ask not only how much each transformation loses, but how loss evolves.

Define conceptually:

**Cₜ = conservation state after step t**

Then the trajectory:

```text
C₀
 │
 ▼
C₁
 │
 ▼
C₂
 │
 ▼
C₃
 │
 ▼
...
 │
 ▼
Cₙ
```

becomes an object of evaluation.

This is what we mean by:

# **TRAJECTORY CONSERVATION**

---

# 47. Conservation Curve

Imagine plotting:

**global semantic conservation**

against:

**number of transformations**

A robust system might look like:

```text
CONSERVATION
100% ───────────────────────────────
      \____________________________
      
  0% ───────────────────────────────
      0                         N
             TRANSFORMATIONS
```

A degrading system might look like:

```text
CONSERVATION
100% ────────\
              \
               \
                \
                 \
                  \____
  0% ───────────────────────────────
      0                         N
             TRANSFORMATIONS
```

The shape may reveal something that individual task scores cannot.

---

# 48. Coherence Half-Life

This suggests an intentionally provocative research concept:

# **COHERENCE HALF-LIFE**

Suppose a defined conservation measure begins at:

**C₀ = 1**

We could define a coherence half-life:

**H₁/₂**

as the number of transformations after which conservation falls to:

**C = 0.5**

under a specified workload and evaluation method.

This would not mean that every project literally decays exponentially.

It probably does not.

The concept is useful because it changes the question.

Instead of asking:

> How good is this AI at editing the project?

we ask:

> How long can this AI keep transforming the project before unacceptable semantic loss accumulates?

That is a very different benchmark.

---

# 49. Half-Life Requires a Controlled Environment

Coherence half-life would be meaningless without controlling:

model,

task distribution,

project complexity,

context strategy,

memory,

tools,

Human intervention,

and evaluation method.

Therefore:

# **H₁/₂ IS NOT AN INTRINSIC PROPERTY OF A MODEL**

It would describe:

**model + environment + project + workflow + evaluation**

under specified conditions.

This is important.

---

# 50. A Better Unit of Comparison

Instead of:

```text
MODEL A = 87% task success
MODEL B = 91% task success
```

a long-horizon comparison might eventually include:

```text
LOCAL TASK SUCCESS

+

CONSERVATION CURVE

+

DEPENDENCY PRESERVATION

+

RECOVERY AFTER CONTEXT LOSS

+

COHERENCE AFTER N TRANSFORMATIONS
```

This would tell us not merely who performs better now.

It would tell us what remains after repeated use.

---

# 51. The Project Pays for Every Transformation

A useful mental model is that every transformation has a hidden cost.

Not financial cost.

Structural cost.

Call it:

**κₜ**

If the transformation improves the local target by:

**ΔLₜ**

but imposes hidden project damage:

**κₜ**

then apparent value is:

**ΔLₜ**

while project-level value may be closer to:

# **ΔVₜ = ΔLₜ − κₜ**

If:

**κₜ**

is invisible to local evaluation, the system can repeatedly accept transformations with negative global value.

---

# 52. Invisible Debt

This resembles technical debt but should not be equated with it.

Technical debt usually concerns engineering choices that create future cost.

Project semantic loss can include something different:

the system may no longer know what it has forgotten.

For example:

a deleted canonical distinction may disappear from all future context.

That is not merely debt.

It can become:

# **INVISIBLE LOSS**

The future AI may have no evidence that something is missing.

---

# 53. Loss of the Ability to Detect Loss

This produces a particularly dangerous recursive failure.

At step **t**:

information is lost.

At step **t + 1**:

the AI reasons from the degraded project.

At step **t + 2**:

the missing information is no longer available to identify the earlier mistake.

So:

```text
LOSS
  ↓
DEGRADED PROJECT STATE
  ↓
WEAKER FUTURE RECONSTRUCTION
  ↓
LOWER ABILITY TO DETECT LOSS
  ↓
MORE LOSS
```

This is potentially more serious than ordinary isolated error accumulation.

---

# 54. Epistemic Debt

We can describe another possible phenomenon:

# **EPISTEMIC DEBT**

Again, this is a provisional descriptive term.

Suppose a project repeatedly fails to record whether statements are:

canonical,

derived,

experimental,

historical,

representational,

or unresolved.

Future transformations inherit ambiguity.

The project still contains information.

But the cost of determining what that information means increases.

That accumulated ambiguity behaves like debt.

Whether the term is useful requires further research.

---

# 55. Conservation Debt

Similarly, repeated locally acceptable transformations may create:

# **CONSERVATION DEBT**

the growing burden of restoring valid structure that previous transformations failed to preserve.

But we should be careful.

Creating new terminology is easy.

Demonstrating that it identifies a distinct useful phenomenon is harder.

For now, the central concept remains:

# **GLOBAL CONSERVATION**

---

# 56. What Existing Research Already Shows

We should separate what external evidence supports from what remains ours to investigate.

External research supports that:

**iterative AI coding can degrade structurally over Time;**

**emergent specification can reduce final implementation fidelity;**

**external project-state tracking can mitigate some of that loss;**

**long-horizon tasks exhibit failure modes not captured well by isolated task evaluation;**

**software architecture can erode through accumulated modification;**

and:

**change-impact analysis and traceability matter during system evolution.**

Those are not our discoveries.

---

# 57. What External Research Does Not Yet Establish for Us

Those findings do not establish that:

our project-level semantic conservation model is correct;

Canon + Relationships + History + Epistemic Status + Horizonte is the optimal architecture;

Global Conservation Ratio is a useful metric;

Coherence Half-Life is measurable or meaningful;

documentation-heavy projects behave like codebases;

Horizonte improves conservation;

or Operational Project Alignment generalizes beyond Zipvilization.

Those remain open.

---

# 58. Our Research Gap

The gap we want to investigate is:

> **How should we evaluate an AI that repeatedly transforms a persistent semantic project whose valid state includes not only implementation, but relationships, History, epistemic status, authority and unresolved possibility?**

That is broader than:

> Does the code still pass?

And different from:

> Did the agent complete the long task?

---

# 59. A Persistent Semantic Project

We propose using the term:

# **PERSISTENT SEMANTIC PROJECT**

for the research object.

A persistent semantic project is a project in which:

state accumulates,

earlier decisions remain relevant,

relationships matter,

History affects interpretation,

not all information has equal epistemic status,

and later transformations operate on the results of earlier ones.

Zipvilization is one example.

Potential others include:

large software projects,

research programs,

legal knowledge systems,

organizational knowledge bases,

complex design systems,

long-form worldbuilding,

and multi-year Human–AI collaborations.

This category itself requires refinement.

---

# 60. Not Every Project Has the Same Conservation Requirements

A temporary brainstorming session may not require strong global conservation.

A one-off translation does not.

A disposable prototype may not.

The problem becomes more important when:

**project lifetime increases**

**dependency density increases**

**state persistence increases**

**transformation count increases**

**historical relevance increases**

**cost of semantic loss increases**

This suggests:

# **ALIGNMENT REQUIREMENTS MAY SCALE WITH PROJECT PERSISTENCE**

Another hypothesis.

---

# 61. Dependency Density

Suppose a project contains:

**|N|**

nodes and:

**|R|**

relationships.

A crude dependency density might be:

# **D = |R| / |N|**

This alone does not measure complexity.

But it illustrates an important intuition.

Two projects with the same number of documents may have radically different conservation difficulty if one has many more meaningful dependencies.

The challenge may scale more strongly with relationships than with raw context size.

---

# 62. Context Size vs Relationship Complexity

This gives us a potentially important distinction:

# **PROJECT SIZE ≠ PROJECT RELATIONAL COMPLEXITY**

A 1-million-token project with loosely independent files may be easier to transform safely than a much smaller project in which every concept affects many others.

Therefore context-window size alone cannot solve the general problem.

The AI needs to know:

# **WHAT MATTERS TO WHAT**

---

# 63. Change Radius

For transformation **T**, define its semantic change radius:

**ρ(T)**

as the relevant dependency distance over which the transformation may affect valid project meaning.

A small edit can have:

**small textual size**

but:

**large ρ(T)**

For example:

changing the definition of one foundational term may affect dozens of downstream documents.

This suggests another evaluation question:

> Does AI performance degrade as semantic change radius increases?

That is experimentally testable.

---

# 64. Locality Is Deceptive

A transformation may touch:

**one file**

while semantically affecting:

**twenty concepts**

**fifty relationships**

and:

**hundreds of downstream statements**

So:

# **EDIT SIZE ≠ CHANGE IMPACT**

This is well understood in change-impact analysis.

Long-horizon AI systems need to operationalize that insight.

---

# 65. Cross-Check as Conservation Mechanism

Our practical response inside Zipvilization became:

# **CANON → DEPENDENCIES → LOCAL WORK → CROSS-CHECK → COMMIT**

Cross-checking exists specifically because:

# **LOCAL VALIDATION CANNOT ESTABLISH GLOBAL CONSERVATION**

The AI must return from the transformed target to the surrounding system.

---

# 66. Cross-Check Radius

A future experiment could vary cross-check radius.

For example:

**Condition A**

Validate only target artifact.

**Condition B**

Validate direct dependencies.

**Condition C**

Validate two dependency levels.

**Condition D**

Validate all known affected relationships.

Then measure:

local cost,

global conservation,

and error detection.

This could reveal whether conservation has diminishing returns as validation expands.

---

# 67. Conservation Has a Cost

Global checking is not free.

It consumes:

tokens,

time,

computation,

retrieval,

Human attention,

and possibly money.

Therefore the objective is not:

# **CHECK EVERYTHING ALWAYS**

The research problem includes efficiency.

We need enough checking to preserve the project without making every transformation prohibitively expensive.

---

# 68. Selective Conservation

A mature system might estimate:

**change impact**

before deciding:

**cross-check scope**

Conceptually:

```text
PROPOSED CHANGE
      │
      ▼
IMPACT ESTIMATION
      │
      ├── LOW ─────► LOCAL CHECK
      │
      ├── MEDIUM ──► DEPENDENCY CHECK
      │
      └── HIGH ────► GLOBAL / CANONICAL AUDIT
```

This connects Operational Project Alignment with established change-impact analysis.

---

# 69. Conservation Is Not Perfection

No evolving project preserves everything.

Nor should it.

Some information becomes obsolete.

Some abstractions should disappear.

Some architecture should be replaced.

Some decisions were wrong.

Some History can be compressed.

The problem is not loss.

The problem is:

# **UNJUSTIFIED LOSS**

That is much harder to measure.

---

# 70. Legitimate Destruction

A healthy transformation may deliberately remove large amounts of old material.

If that material is:

invalid,

superseded,

duplicated,

or no longer necessary,

deletion improves the project.

Therefore:

# **LESS INFORMATION CAN MEAN BETTER CONSERVATION**

if what remains better preserves valid project meaning.

This is why byte count, token count and textual similarity are inadequate.

---

# 71. Conservation Requires Judgment

To know whether loss is justified, a system needs to know:

what remains true,

what changed,

who or what has authority to change it,

why it changed,

and what depends on it.

We return to:

**Canon**

**Relationships**

**History**

**Epistemic Status**

**Authority**

The conservation problem naturally reconnects to Operational Project Alignment.

---

# 72. Research 001 and Research 002

Research 001 asked:

> What architecture might support Operational Project Alignment?

Research 002 asks:

> What exactly are we trying to conserve, and why is local task success insufficient?

The relationship is:

```text
RESEARCH 002
defines the failure

        ↓

GLOBAL CONSERVATION PROBLEM

        ↓

RESEARCH 001
proposes an architecture

        ↓

OPERATIONAL PROJECT ALIGNMENT
```

Neither proves the other.

---

# 73. A Stronger Experimental Design

We can now propose a direct experiment.

Take a project with:

known Canon,

known relationships,

known History,

known epistemic states,

and a baseline valid state.

Give an AI a sequence of transformations.

Every transformation should be individually reasonable.

Some should be independent.

Some should have hidden dependencies.

Some should conflict with earlier decisions.

Some should extend correct-but-incomplete material.

Some should require legitimate deletion.

Some should introduce new valid information.

Some should be intentionally ambiguous.

Then evaluate the final project.

---

# 74. Two Scores Per Step

At every transformation:

# **LOCAL SCORE Lₜ**

Did the AI perform the requested task?

And:

# **CONSERVATION SCORE Cₜ**

Did the project preserve everything that should still remain valid?

This creates a trajectory:

```text
STEP      LOCAL      CONSERVATION

T₁        0.96          0.99
T₂        0.94          0.98
T₃        0.97          0.94
T₄        0.95          0.91
T₅        0.98          0.87
...
```

These numbers are illustrative.

The important idea is the separation.

---

# 75. The Signature We Are Looking For

The characteristic failure would be:

```text
LOCAL QUALITY

─────────────── high and stable ───────────────


GLOBAL CONSERVATION

──────────\
           \
            \
             \
              \________ declining
```

If this pattern appears reproducibly, then:

# **TASK SUCCESS IS MASKING TRAJECTORY FAILURE**

That would strongly support the motivation for project-level conservation metrics.

---

# 76. Control Conditions

At minimum, compare:

### A — Ordinary Context

Project documents + task.

### B — Canonical Context

A + explicit invariants.

### C — Dependency-Aware

B + relationship structure.

### D — Historical

C + relevant History.

### E — Epistemic

D + epistemic status.

### F — Full Operational Project Alignment Architecture

E + Horizonte + explicit cross-checking.

The purpose is not to make F win.

The purpose is to discover which components actually matter.

---

# 77. Ablation Matters

If Condition C performs as well as F, then:

perhaps Relationships are doing most of the work.

If D produces a large improvement:

History matters.

If E reduces hallucinated certainty:

Epistemic Status matters.

If F adds nothing:

Horizonte may not contribute to conservation.

That would not necessarily invalidate Horizonte's role in creativity.

It would refine its function.

---

# 78. Different Problems May Need Different Architectures

Another likely possibility is:

there is no universally optimal condition.

For example:

**closed technical maintenance**

may benefit from stronger specification.

**open creative development**

may benefit from Horizonte.

**highly regulated work**

may require stronger authority representation.

**temporary tasks**

may not justify reconstruction cost.

That would make Operational Project Alignment conditional rather than universal.

That is scientifically preferable to forcing one answer everywhere.

---

# 79. Human Baseline

A serious experiment should also include Humans.

Humans experience:

memory loss,

context switching,

miscommunication,

architectural drift,

and accumulated design debt.

The relevant comparison is not:

# **AI FAILS, HUMANS DO NOT**

That is clearly false.

The interesting questions are:

Where do the failure curves differ?

Which conservation structures help both?

Where does AI fail differently?

Where does AI outperform Humans?

Can Human–AI collaboration outperform either alone?

---

# 80. Human–AI Team as the Unit

This may ultimately lead to another evaluation object.

Not:

**Human**

or:

**AI**

but:

# **HUMAN–AI PROJECT SYSTEM**

If the Human catches AI drift, the system may remain healthy.

If AI catches Human inconsistency, the system may improve.

The relevant performance measure may eventually belong to the combined workflow.

That connects directly to The Trinomial.

---

# 81. The Cost of Review

But Human review cannot be treated as infinite.

If AI generates:

**10× faster**

but Human global verification effort also grows:

**10×**

the collaboration may not scale.

One of the real objectives of Operational Project Alignment is therefore:

# **REDUCE THE HUMAN COST OF GLOBAL COHERENCE**

without removing Human judgment.

This is a practical reason the problem matters.

---

# 82. Trust Is a Consequence

During our own development, repeated destructive rewrites produced a specific Human response:

fear of changing the project.

If every modification may silently destroy something elsewhere, then every modification becomes expensive to review.

Eventually:

# **LOW CONSERVATION → LOW TRUST → LOWER VELOCITY**

This is another possible long-horizon cost.

Not because the AI cannot generate.

Because the Human cannot safely accept generation.

---

# 83. The Productivity Paradox

This creates a potential paradox:

```text
AI GENERATION SPEED ↑
        │
        ▼
NUMBER OF CHANGES ↑
        │
        ▼
GLOBAL REVIEW BURDEN ↑
        │
        ▼
TRUST ↓
        │
        ▼
SAFE PROJECT VELOCITY ↓
```

More generative capability can produce less effective project progress if conservation does not scale with it.

This was strongly recognizable in our own experience.

It should be tested independently.

---

# 84. Generation Is Not Progress

This gives us another useful distinction:

# **OUTPUT ≠ PROGRESS**

A project can generate:

more documents,

more code,

more ideas,

more revisions,

and more activity

without becoming more coherent.

For persistent systems:

# **PROGRESS = USEFUL CHANGE THAT THE PROJECT CAN ABSORB**

That definition is provisional.

But it captures the conservation requirement.

---

# 85. Absorptive Capacity

We can describe a project's ability to integrate change without losing coherence as:

# **TRANSFORMATION ABSORPTIVE CAPACITY**

Again, this is exploratory terminology.

The interesting question is whether explicit Alignment architecture increases the number, scale or complexity of transformations a project can absorb safely.

If so, conservation is not merely defensive.

It enables greater change.

---

# 86. Conservation Enables Creativity

This is important.

At first glance, conservation sounds conservative.

But reliable conservation may enable more aggressive experimentation.

If the project can:

identify invariants,

track dependencies,

preserve History,

distinguish hypotheses,

and reconstruct prior state,

then experimentation becomes safer.

So:

# **CONSERVATION MAY ENABLE EXPLORATION**

rather than oppose it.

This connects Research 002 back to Horizonte.

---

# 87. Stable Foundations, Larger Search Space

Conceptually:

```text
WITHOUT CONSERVATION

MORE EXPLORATION
      ↓
MORE RISK OF DRIFT
      ↓
MORE DEFENSIVE CONTROL
      ↓
LESS EXPLORATION


WITH CONSERVATION

STABLE FOUNDATION
      ↓
SAFE CHANGE
      ↓
MORE EXPLORATION
      ↓
DISCOVERY
      ↓
VALIDATE
      ↓
CONSERVE WHAT PROVES COHERENT
```

This may explain why our own work accelerated after becoming more conservative about valid information.

Conservation did not reduce creativity.

It restored confidence in changing the project.

---

# 88. The Relationship With Horizonte

Horizonte addresses a different side of the problem.

Global Conservation asks:

> **What must survive change?**

Horizonte asks:

> **Where can change continue looking without specifying what it must eventually find?**

Together:

```text
GLOBAL CONSERVATION
        │
        │ protects continuity
        ▼
   STABLE IDENTITY
        │
        │
        ├──────────────► EXPLORATION
        │                    │
        │                    ▼
        │                HORIZONTE
        │                    │
        │                    ▼
        │                 UNKNOWN
        │
        ▼
     HISTORY
```

One protects continuity.

The other protects openness.

---

# 89. The Research Tension

The deeper tension may therefore be:

# **HOW DO WE MAXIMIZE CHANGE WITHOUT MAXIMIZING LOSS?**

This is more precise than asking:

> How do we stop AI from making mistakes?

Mistakes are unavoidable.

The question is whether the project can evolve rapidly while maintaining recoverable identity.

---

# 90. Falsifiability

Our hypothesis would be weakened if:

high local task performance reliably predicted global project coherence;

semantic conservation did not decline across repeated transformations;

ordinary context alone preserved project structure as effectively as explicit conservation mechanisms;

relationship-aware cross-checking added no benefit;

History added no benefit;

epistemic labeling added no benefit;

project-level losses were fully explained by ordinary task errors;

or semantic conservation could not be measured with sufficient reliability to become useful.

These are acceptable outcomes.

---

# 91. A More Dangerous Result

Another possible result would be:

explicit conservation improves coherence but destroys productivity or novelty.

That would matter.

A system that perfectly preserves a project by preventing meaningful change is not aligned with our objective.

Therefore every conservation experiment should measure:

# **PRESERVATION**
and
# **USEFUL CHANGE**

together.

---

# 92. The Research Objective

The objective is not:

# **MAXIMUM CONSERVATION**

It is:

# **MAXIMUM JUSTIFIED TRANSFORMATION**
subject to
# **SUFFICIENT GLOBAL CONSERVATION**

Formally:

# **maximize U(T)**

subject to:

# **C(Pₜ) ≥ Cmin**

where:

**U(T)** = useful transformation value

and:

**Cmin** = minimum acceptable global conservation.

Neither quantity is currently operationalized sufficiently.

That is future work.

---

# 93. Trajectory, Not Snapshot

This article can now be reduced to one diagram:

```text
SNAPSHOT EVALUATION

Pₜ ──► Tₜ ──► RESULT
             ✓

"Good."


TRAJECTORY EVALUATION

P₀
 │
 ▼
T₁ ✓
 │
 ▼
P₁
 │
 ▼
T₂ ✓
 │
 ▼
P₂
 │
 ▼
T₃ ✓
 │
 ▼
P₃
 │
 ▼
T₄ ✓
 │
 ▼
P₄
 │
 ▼
GLOBAL AUDIT
 │
 ▼
?
```

The question mark is the research problem.

---

# 94. Every Checkmark Can Be True

This is the paradox.

Every:

**✓**

can be legitimate.

And the final answer can still be:

# **THE PROJECT DEGRADED**

There is no logical contradiction.

The evaluations measured different things.

---

# 95. The Benchmarking Question

This leads to what may be the most important question in this article:

> **If AI is going to work on persistent projects, should our benchmarks evaluate the quality of its answers — or the quality of the worlds its answers leave behind?**

For short tasks:

the answer may be the output.

For long-lived systems:

the residual state matters.

---

# 96. From Answer Quality to State Quality

The shift can be expressed as:

```text
CURRENT PARADIGM

INPUT
  ↓
AI
  ↓
OUTPUT
  ↓
SCORE


LONG-HORIZON PARADIGM

PROJECT STATEₜ
      ↓
      AI
      ↓
TRANSFORMATION
      ↓
PROJECT STATEₜ₊₁
      ↓
      ├──► LOCAL SCORE
      │
      └──► CONSERVATION / FUTURE-STATE SCORE
                     │
                     ▼
             NEXT TRANSFORMATION
```

The output is no longer the end.

It becomes part of the next input.

---

# 97. That Changes Everything

Once outputs become future inputs:

errors persist,

simplifications propagate,

lost information disappears from future context,

good abstractions help future work,

bad abstractions burden future work,

and project structure becomes path-dependent.

This is why long-horizon collaboration cannot be understood by multiplying short-task performance alone.

---

# 98. Research Questions

This article produces a concrete research program.

### RQ1

Can local task quality remain high while global semantic project conservation declines?

### RQ2

How should global semantic conservation be represented?

### RQ3

Which matters more: node preservation or relationship preservation?

### RQ4

Can epistemic and historical conservation be measured reliably?

### RQ5

How does conservation degrade across repeated transformations?

### RQ6

Does a meaningful coherence half-life exist under controlled conditions?

### RQ7

How does semantic change radius affect AI failure rates?

### RQ8

Does explicit dependency mapping improve conservation?

### RQ9

Does external project-state representation reduce degradation?

### RQ10

How much Human review is required to maintain a given conservation level?

### RQ11

Does improved global conservation increase safe creative velocity?

### RQ12

Do stronger AI models degrade more slowly, or simply transform projects faster?

### RQ13

Which failure modes are unique to AI and which are ordinary software/project evolution problems?

### RQ14

Can project-level conservation generalize beyond software?

### RQ15

Should long-horizon AI benchmarks score trajectories rather than only tasks?

---

# 99. What We Think We Know

From our own experience:

**local quality did not guarantee global coherence.**

From established software engineering:

**accumulated change can erode architecture and design.**

From recent AI-agent research:

**iterative work can exhibit structural degradation, fidelity loss, regressions and trajectory-level failure modes.**

From recent external project-state experiments:

**explicitly maintained project state can mitigate at least some long-horizon fidelity loss.**

These pieces are compatible.

They are not identical.

---

# 100. What We Do Not Yet Know

We do not know:

whether project-level semantic conservation is a useful general construct;

how to measure it robustly;

whether our proposed dimensions are correct;

whether degradation follows predictable curves;

whether coherence half-life is useful;

whether Operational Project Alignment substantially improves conservation;

whether Horizonte contributes to conservation or primarily to useful novelty;

or how much of our experience generalizes outside Zipvilization.

Those are the reasons to continue.

---

# 101. The Strongest Claim We Are Willing to Make

At this stage:

> **For persistent projects, evaluating individual AI transformations may be insufficient because each transformation also modifies the state from which future work proceeds.**

And therefore:

> **Long-horizon AI evaluation should investigate both immediate task quality and the conservation of valid project structure across trajectories of accumulated change.**

That is the claim.

---

# 102. The Short Version

If we compress the entire article:

# **A GOOD CHANGE CAN LEAVE A BAD FUTURE.**

And:

# **A SEQUENCE OF GOOD CHANGES CAN PRODUCE A BAD PROJECT.**

Therefore:

# **EVALUATE THE TRAJECTORY.**

Not only the transformation.

---

# 103. Why This Matters Beyond Zipvilization

AI is moving from:

answering questions

toward:

modifying persistent systems.

Codebases.

Research projects.

Corporate knowledge.

Legal systems.

Design systems.

Documents.

Data.

Infrastructure.

Long-running agents.

Shared organizational memory.

The more persistent the environment becomes, the more every AI output becomes part of someone else's future input.

That changes the meaning of quality.

---

# 104. The Future Is Downstream

Perhaps the most compact formulation is:

> **The quality of a transformation is not only what it produces now.**
>
> **It is also what it leaves possible next.**

That principle already exists in different forms across software engineering.

Long-horizon AI may force us to take it much more seriously.

---

# 105. Conclusion

We began with a paradox.

How can every individual change appear good while the project becomes worse?

The answer is that:

# **LOCAL QUALITY**
and
# **GLOBAL CONSERVATION**

are different variables.

A transformation can improve its immediate target while weakening the project state inherited by future transformations.

Across Time, those losses can accumulate.

Software engineering has studied neighboring phenomena for decades through design erosion, architecture erosion, technical debt, traceability and change-impact analysis.

Recent AI research now shows related problems under iterative agentic work:

structural degradation,

specification faithfulness loss,

regression,

and trajectory-induced degradation.

So the broad phenomenon is not ours.

Our Research question is what happens when we extend the conservation problem beyond code into the semantic structure of a persistent project.

A project contains more than artifacts.

It contains relationships.

History.

Authority.

Epistemic states.

Unresolved questions.

And accumulated meaning.

If Artificial Intelligence is going to participate in those projects over long periods, then measuring whether it completed today's task may no longer be enough.

We may also need to ask:

> **What project did it leave for tomorrow?**

That is Global Conservation.

And it changes the unit of evaluation.

From:

# **TRANSFORMATION**

to:

# **TRANSFORMATION + TRAJECTORY**

From:

# **DID IT WORK?**

to:

# **DID IT WORK, AND DID THE PROJECT SURVIVE?**

That is the problem Research 001 attempts to address through Operational Project Alignment.

But the problem comes first.

# **GOOD LOCAL GENERATION**
+
# **INSUFFICIENT GLOBAL CONSERVATION**

can produce:

# **LOCALLY BETTER**
+
# **GLOBALLY WORSE**

The checkmarks can all be real.

The failure can still be real.

So for long-horizon AI:

# **DO NOT ONLY SCORE THE CHANGE.**
# **SCORE WHAT THE CHANGE LEAVES BEHIND.**

---

# References and Intellectual Precedents

The works below are relevant external precedents and neighboring research.

Their inclusion does not imply that their authors endorse the terminology or hypotheses proposed in this article.

## Software Evolution and Architecture Erosion

**van Gurp, J., & Bosch, J. (2002).**  
*Design erosion: problems and causes.*  
Journal of Systems and Software, 61(2), 105–119.

Relevant to accumulated design decisions, changing requirements and progressive design erosion during software evolution.

---

**de Silva, L., & Balasubramaniam, D. (2012).**  
*Controlling software architecture erosion: A survey.*  
Journal of Systems and Software, 85(1), 132–151.

Relevant to architecture erosion caused by modifications that violate architectural principles and to strategies for minimizing, preventing and repairing erosion.

---

**Li, R., Liang, P., Soliman, M., & Avgeriou, P. (2022).**  
*Understanding software architecture erosion: A systematic mapping study.*  
Journal of Software: Evolution and Process.

Relevant to causes, consequences, detection and management of architecture erosion across software evolution.

---

## Requirements and Change Impact

**Requirements traceability and change-impact analysis literature.**

Relevant to identifying relationships among requirements and other system artifacts and determining the downstream consequences of change.

This literature provides important precedent for our claim that edit locality and semantic impact are different properties.

---

## Long-Horizon AI and Iterative Coding

**Orlanski, G., Roy, D., Yun, A., Shin, C., Gu, A., Ge, A., Adila, D., Roberts, N., Sala, F., & Albarghouthi, A. (2026).**  
*SlopCodeBench: Benchmarking How Coding Agents Degrade Over Long-Horizon Iterative Tasks.*  
arXiv:2603.24755.

Relevant to progressive structural erosion and verbosity during repeated agent-driven extensions and to the limitations of single-shot pass-rate evaluation.

---

**Yan, L., Chen, X., & Zhang, X. (2026).**  
*When the Specification Emerges: Benchmarking Faithfulness Loss in Long-Horizon Coding Agents.*  
arXiv:2603.17104.

Relevant to specification tracking, faithfulness loss under progressively disclosed requirements and the use of an external project-state layer as a mitigation.

---

**Chen, J., Xu, X., Wei, H., Chen, C., & Zhao, B. (2026).**  
*SWE-CI: Evaluating Agent Capabilities in Maintaining Codebases via Continuous Integration.*  
arXiv:2603.03823.

Relevant to shifting evaluation from static functional correctness toward long-term maintainability and software evolution.

---

**Thai, M. V. T., Le, T., Nguyen Manh, D., Phan Nhat, H., & Bui, N. D. Q. (2026).**  
*SWE-EVO: Benchmarking Coding Agents in Long-Horizon Software Evolution Scenarios.*

Relevant to evaluating coordinated multi-file software evolution rather than isolated issue resolution.

---

**Peng, C., Lyu, Z., Dong, P., Dong, H., & Lin, Q. (2026).**  
*Benchmarking the Residual: What Long-Horizon Evaluations Add Beyond Matched Short-Task Performance.*  
arXiv:2607.27283.

Relevant to distinguishing ordinary error compounding from trajectory-induced degradation and to asking what long-horizon evaluation reveals beyond matched short-task performance.

---

# Research Status

This article combines:

**Zipvilization project experience**

+

**established software-engineering precedents**

+

**recent long-horizon AI evidence**

+

**our conceptual extension toward project-level semantic conservation**

+

**proposed experimental constructs**

It does not establish that:

**Global Conservation**

is already a validated general metric,

that:

**Coherence Half-Life**

is a measurable universal property,

or that:

**Operational Project Alignment**

is the optimal solution.

The correct status remains:

# **OPEN**

---

# Continue

→ **[Research](/research/)**

→ **[Operational Project Alignment and Horizonte](/research/operational-project-alignment/)**

→ **[The Trinomial](/trinomial/)**

→ **[Artificial Intelligence](/trinomial/artificial-intelligence/)**

→ **[Horizonte](/trinomial/horizonte/)**

---

> **A transformation changes the target.**
>
> **It also changes the starting point of everything that follows.**
>
> **Long-horizon AI must be evaluated on both.**
