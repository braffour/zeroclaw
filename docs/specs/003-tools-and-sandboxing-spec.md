---
id: ZC-SPC-003
title: Tool invocation contract and execution boundaries
status: draft
risk_tier: high
---
## 1. Intent
Document how tool schemas, registration, and execution currently guard runtime/tool behavior.

## 2. In scope
- `src/tools/traits.rs`
- `src/tools/mod.rs`
- plugin tool integration path
- default/system tool registries

## 3. Current behavior to preserve
- Tools are registered from static/default and plugin paths.
- Tool parameters pass schema checks before invocation.
- Tool results are normalized for agent loop integration.

## 4. Requirements
- Include explicit deny/allow behavior for high-risk actions.
- Require idempotent handling expectations per tool type.
- Define tool error taxonomy and logging hygiene (no secret leakage).

## 5. Acceptance criteria
- Scenario list includes malformed args, unsupported tool, partial result, and tool timeout/failure propagation.
