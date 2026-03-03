---
id: ZC-SPC-000
title: Runtime bootstrap and configuration contract
status: draft
risk_tier: medium
---
## 1. Intent
Preserve and document the full startup contract from CLI into runtime composition and config loading without altering behavior.

## 2. In scope
- `src/main.rs`
- `src/lib.rs`
- `src/config/schema.rs`
- CLI command routing and bootstrap error paths

## 3. Current behavior to preserve
- CLI parses command mode and routes into runtime services.
- Config is loaded, merged, and validated before subsystem construction.
- Fail-fast behavior on malformed/invalid config keys is expected.

## 4. Requirements
- Must keep trait-based composition untouched in this phase.
- Must document bootstrap order and explicit dependency prerequisites.
- Must document what fails fast and where.

## 5. Non-goals
- No new config keys or migration format changes in this pass.

## 6. Acceptance criteria
- Specification defines exact bootstrap sequence.
- Failure matrix is explicit (load error, merge error, policy mismatch, provider mismatch).
- No recommendations requiring command-line behavior changes.
