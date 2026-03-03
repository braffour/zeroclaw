---
id: ZC-SPC-004
title: Memory subsystems and persistence contracts
status: draft
risk_tier: medium
---
## 1. Intent
Document memory semantics including backend selection, storage migration, and retrieval behavior.

## 2. In scope
- `src/memory/traits.rs`
- backends in `src/memory/*`
- merge/index paths for retrieval

## 3. Current behavior to preserve
- Memory backend selected by config with deterministic defaulting.
- Retrieval and persistence path remains deterministic for same input state.
- Storage overrides and migration paths are explicit.

## 4. Requirements
- Clarify write/read consistency expectations.
- Clarify retention or pruning assumptions per backend.
- Clarify behavior when backend initialization fails.

## 5. Acceptance criteria
- Scenario set includes startup with no memory, invalid path, backend mismatch, and retrieval latency/empty result.
