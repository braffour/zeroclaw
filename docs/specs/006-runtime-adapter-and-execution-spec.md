---
id: ZC-SPC-006
title: Runtime adapters and execution semantics
status: draft
risk_tier: medium
---
## 1. Intent
Document the runtime adapter abstraction and selection behavior without changing adapter interfaces.

## 2. In scope
- `src/runtime/traits.rs`
- `src/runtime/{native,docker,wasm}/**`
- adapter registration and fallback behavior

## 3. Current behavior to preserve
- Runtime adapter abstraction is selected from config/factory.
- Adapter errors are surfaced to orchestration layer with bounded retry semantics where present.

## 4. Requirements
- Document supported runtime feature matrix by command mode.
- Document unsupported runtime behavior as explicit errors (not silent ignore).

## 5. Acceptance criteria
- Startup success and adapter mismatch scenarios are documented.
- Runtime boundaries for side effects and I/O are explicit.
