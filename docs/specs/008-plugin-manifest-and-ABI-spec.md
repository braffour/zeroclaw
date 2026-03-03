---
id: ZC-SPC-008
title: Plugin manifest, tool wiring, and ABI compatibility
status: draft
risk_tier: medium
---
## 1. Intent
Document plugin contract to avoid silent incompatibility while preserving current partial WASM ABI state.

## 2. In scope
- `src/plugins/**`
- manifest loading/parsing/registration paths
- plugin discovery and registration ordering

## 3. Current behavior to preserve
- Plugin manifest-driven registration exists.
- WASM boundary symbols and compatibility assumptions must remain explicit.
- Plugin load failure does not cascade into unsafe defaults.

## 4. Requirements
- Define exact compatibility boundaries for current ABI version and host expectations.
- Document unsupported plugin scenarios and error classification.
- Require deterministic plugin registration order where applicable.

## 5. Acceptance criteria
- Unsupported plugin should fail with explicit diagnostic and no broad privilege extension.
