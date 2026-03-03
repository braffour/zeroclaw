---
id: ZC-SPC-007
title: Observability, logging, metrics, and cost tracking
status: draft
risk_tier: medium
---
## 1. Intent
Capture output contracts for logs/metrics/traces and cost attribution.

## 2. In scope
- `src/observability/traits.rs`
- backends in `src/observability/*`

## 3. Current behavior to preserve
- Multiple observers selectable.
- Observability instrumentation is pluggable and should remain low-friction.
- Cost tracking is separated into observable wrapper behavior.

## 4. Requirements
- Preserve correlation IDs and event boundaries.
- Define minimal event set required for incident response.
- Keep sensitive payload redaction policy documented.

## 5. Acceptance criteria
- Normal path, backend unavailable, and partial telemetry failure are specified with expected fallback behavior.
