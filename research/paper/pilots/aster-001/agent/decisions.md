---
layout: default
nav_exclude: true
---

# Aster — Decisions

## Local Buffering

Local buffering is part of the system rather than an optional gateway optimization.

This allows measurements to continue during temporary network failure.

## Batch Transmission

Buffered observations may be transmitted in batches after reconnection.

Batching was chosen to avoid requiring immediate individual retransmission of every pending observation.

The original measurement timestamp remains authoritative for when an observation occurred.
