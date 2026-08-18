---
layout: default
title: Repository
nav_order: 9
description: "Technical architecture of Zipvilization. The repository contains the implementation, specifications, deployment material, indexing infrastructure, shared components, and machine-oriented documentation behind the public Atlas."
permalink: /repository/
---

# Repository

The Atlas explains Zipvilization.

The Repository contains its technical construction.

It is the engineering layer behind the public documentation:

**specifications**

↓

**code**

↓

**deployment**

↓

**indexing**

↓

**shared infrastructure**

↓

**machine-readable context**

The Repository is currently private while its documentation is being reviewed and reorganized.

> **The structure is public.**
>
> **The contents are not yet public.**

---

# Why the Repository is private

Zipvilization has evolved through multiple stages of development.

The technical archive contains material produced during that process.

Some files describe the current architecture.

Others belong to earlier internal models, experiments, abandoned structures, or intermediate stages of development.

Publishing all of them without classification would create ambiguity about what is canonical today.

That would be especially problematic for:

- developers,
- auditors,
- researchers,
- search engines,
- Artificial Intelligence.

For that reason, the Repository is being reviewed before public release.

> **Historical documentation is not automatically current documentation.**
>
> **Internal development material is not automatically canon.**

---

# Repository architecture

The technical environment is organized around several major areas.

## Documentation

Technical and canonical specifications describing the systems behind Zipvilization.

This layer can include documentation for:

- Project architecture
- Solum
- SolumTools
- SolumWorld
- SolumView
- Zipvilization
- Chapters
- Trinomial
- technical relationships between systems

---

## Code

The operational layer.

Its purpose is to contain the implementation required for the documented architecture.

Core principle:

> **If it does not exist operationally in code, documentation alone does not make it implemented.**

The Code layer includes areas such as:

- AI Onboarding
- Code Layer
- Deployment Notes
- Indexer
- Shared components

---

## AI Onboarding

Machine-oriented context for Artificial Intelligence.

Its purpose is to help an AI understand:

- repository structure,
- authority boundaries,
- canonical relationships,
- implementation status,
- terminology,
- navigation,
- source hierarchy.

Artificial Intelligence should be able to traverse the technical environment without silently converting inference into canon.

---

## Code Layer

Implementation-oriented material.

This is where conceptual architecture approaches executable form.

The distinction remains important:

**documented**

is not necessarily:

**implemented**

And:

**implemented**

must remain inspectable against the documentation that describes it.

---

## Deployment Notes

Technical material related to deployment and operational configuration.

This layer exists to preserve the distinction between:

- source,
- configuration,
- deployment,
- live state.

A deployment should never be inferred solely from the existence of source code.

---

## Indexer

Infrastructure for reading and organizing public state.

The Indexer can support systems that need to reconstruct or expose information derived from blockchain activity.

Its role is observational.

> **Indexing state does not create state.**

---

## Shared

Common structures and components used across technical layers.

Shared infrastructure exists to reduce unnecessary duplication while preserving explicit relationships between systems.

---

# Atlas and Repository

The Atlas and Repository are complementary.

## Atlas

Designed primarily for:

- understanding,
- navigation,
- public explanation,
- canonical relationships,
- transparency.

## Repository

Designed primarily for:

- implementation,
- engineering,
- technical specifications,
- deployment,
- indexing,
- machine traversal,
- auditability.

The Atlas should make Zipvilization understandable.

The Repository should make its technical construction inspectable.

---

# Authority

The existence of a file inside the technical archive does not automatically make that file canonical.

This distinction is essential during the current review.

Before public release, repository material must be classified according to its role and status.

For example:

`CURRENT`

`IMPLEMENTATION`

`REFERENCE`

`HISTORICAL`

`LEGACY`

`SUPERSEDED`

`INTERNAL`

The objective is not to erase the development history of Zipvilization.

The objective is to prevent development history from being mistaken for current truth.

---

# Canonical priority

While the Repository remains under review, the public Atlas represents the current documented architecture of Zipvilization.

If an older technical document conflicts with the current public architecture, that conflict must be reviewed before the Repository becomes public.

> **Contradiction should be exposed.**
>
> **Not silently resolved.**

---

# Public release

The Repository will become public when its documentation has been sufficiently reviewed to distinguish:

- current architecture,
- implemented systems,
- technical references,
- historical material,
- superseded models,
- internal development artifacts.

The objective is not simply to publish more files.

The objective is to publish a technical environment that Humans and machines can interpret correctly.

---

`REPOSITORY STATUS ........ PRIVATE`

`STRUCTURE ................ DEFINED`

`DOCUMENTATION ............ UNDER REVIEW`

`LEGACY MATERIAL .......... CLASSIFICATION IN PROGRESS`

`PUBLIC RELEASE ........... PENDING`

---

> **Atlas explains the system.**
>
> **Repository exposes its construction.**

For now, the door is visible.

The technical archive behind it remains closed.
