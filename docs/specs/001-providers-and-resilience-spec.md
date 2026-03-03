---
id: ZC-SPC-001
title: Providers, aliases, routing, and resilience behavior
status: draft
risk_tier: high
---
## 1. Intent
Document how provider factories, alias canonicalization, and resilient wrappers currently decide request routing/fallbacks.

## 2. In scope
- `src/providers/traits.rs`
- `src/providers/mod.rs`
- `src/providers/registry.rs` and adapter layers

## 3. Current behavior to preserve
- Provider creation is factory-driven.
- Canonical names and aliases are resolved before runtime selection.
- Resilient wrappers manage retries/circuit conditions for provider calls.

## 4. Requirements
- Explicitly document provider selection precedence and fallback boundaries.
- Explicitly document unsupported provider error behavior.
- Include cost of failure and how errors are propagated to agent loop.

## 5. Risks
- Silent fallback or widened provider support can change blast radius.
- Inconsistent naming between alias and canonical IDs can break config compatibility.

## 6. Acceptance criteria
- Test scenarios include unknown provider key, disabled provider, fallback sequence, and error surfacing.
