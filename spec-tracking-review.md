# Spec Tracking and Review Map

## 1) Purpose
Track brownfield reverse-engineering into spec artifacts, coverage, and risk tier for implementation-ready follow-ups.

## 2) Spec Index
| Spec ID | Domain | Files Anchored | Contract Coverage | Risk Tier | Owner | Dependencies | Review Status | Open Gaps | Acceptance Evidence |
|---|---|---|---|---|---|---|---|---|
| ZC-SPC-000 | Runtime bootstrap & config | src/main.rs, src/lib.rs, src/config/schema.rs | High | Medium | Platform architect | `lib.rs` bootstrap flow, `main.rs` command router | Draft | Config compatibility edge cases, deterministic startup ordering under partial env vars | In-scope list and failure matrix defined in spec; no runtime call paths changed |
| ZC-SPC-001 | Provider abstraction and resilience | src/providers/** | High | High | Platform architect | `providers/traits.rs`, adapter modules | Draft | Routed/fallback policy visibility, unsupported provider diagnostics | Requirements include precedence + fallback + error propagation scenarios |
| ZC-SPC-002 | Channel + gateway ingress | src/gateway/**, src/channels/** | High | High | Platform architect | `gateway/mod.rs`, `channels/mod.rs`, `channels/traits.rs` | Draft | Auth/allowlist matrix, startup/shutdown failure semantics | Explicit ingress/health matrices included |
| ZC-SPC-003 | Tool surface governance | src/tools/** | High | High | Platform architect | `tools/traits.rs`, plugin registration path | Draft | Plugin/tool schema drift and timeout behavior | Scenario set includes malformed args, unsupported tool, timeout/failure propagation |
| ZC-SPC-004 | Memory stack and persistence | src/memory/** | High | Medium | Platform architect | `memory/traits.rs`, backend modules | Draft | Retention and compaction behavior, init failure mode | Scenarios include no-memory, invalid path, backend mismatch, retrieval edge states |
| ZC-SPC-005 | Security and policy posture | src/security/** | High | High | Platform architect | Bootstrap policy checks + runtime call sites | Draft | Pairing/secret lifecycle and lockout guarantees | Threat-aware scenarios explicitly listed in spec |
| ZC-SPC-006 | Runtime adapters | src/runtime/** | Medium | Medium | Platform architect | `runtime/traits.rs`, native/docker/wasm adapters | Draft | Runtime feature parity and unsupported command mode handling | Scenarios include startup success and adapter mismatch |
| ZC-SPC-007 | Observability and cost | src/observability/** | Medium | Medium | Platform architect | `observability/traits.rs`, backend implementations | Draft | Cost telemetry retention and partial sink failures | Normal/unavailable/partial-failure paths defined |
| ZC-SPC-008 | Plugin ABI and registry | src/plugins/** | Medium | Medium | Platform architect | plugin manifest parser, ABI wrapper modules | Draft | ABI compatibility envelope and deterministic ordering | Unsupported plugin diagnostics and privilege boundaries explicitly required |
| ZC-SPC-009 | Peripherals and hardware tools | src/peripherals/** | Medium | Medium | Platform architect | `peripherals/traits.rs`, board modules, docs design reference | Draft | Hardware safety invariants and unavailable-board behavior | Scenario list includes unavailable board, unsupported board ID, unsafe request rejection |
| ZC-SPC-010 | Docs/contract governance | docs/** | Medium | Low | Docs maintainer | docs IA, contracts, i18n guide, SUMMARY/reference sets | Draft | Locale follow-through and change gating process | Acceptance criterion requires impacted-locale list for shared wording changes |

## 3) Review Rules
- Security/runtime/tools/gateway specs require explicit failure-mode and rollback section before implementation kickoff.
- No spec can exit draft until:
  - at least one “current-behavior anchor” is listed
  - acceptance criteria includes safety for deny/allow boundaries
  - ownership and dependency path are explicit.

## 4) Status Lifecycle
- Draft: spec text exists and identifies risks and acceptance criteria.
- In Review: acceptance criteria mapping and dependency checks completed.
- Approved for Build: failure-mode/rollback paths and rollout constraints validated.
- Implemented: code changes made in a bounded PR with explicit rollback notes.

## 5) SDD Mapping
- PRD and Architecture docs define top-level “intent + structure.”
- Individual specs provide executable behavioral contracts for each subsystem.
- Future implementation PRs must cite impacted spec IDs and update row status to “In Review” then “Implemented”.
