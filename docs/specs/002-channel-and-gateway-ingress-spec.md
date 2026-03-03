---
id: ZC-SPC-002
title: Channel and gateway ingress, dispatch, and health
status: draft
risk_tier: high
---
## 1. Intent
Capture non-disruptive contract of message ingress from channels and gateway through agent ingestion and health telemetry.

## 2. In scope
- `src/gateway/mod.rs`
- `src/channels/mod.rs`
- `src/channels/traits.rs`
- channel-specific adapters

## 3. Current behavior to preserve
- Channels register send/listen/health semantics via trait contracts.
- Gateway starts and feeds normalized inbound events into agent runtime.
- Health path exists and is distinct from message path.

## 4. Requirements
- Keep transport auth boundaries explicit.
- Document message normalization and source attribution rules.
- Define channel startup/shutdown ordering.

## 5. Acceptance criteria
- Explicit matrix: normal ingress, denied inbound payload, unhealthy listener, listener restart path.
- No implicit widening of accept criteria.
