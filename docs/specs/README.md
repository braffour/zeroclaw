# Specs Index

This directory contains the Spec Kit reverse-engineering pack for ZeroClaw’s brownfield architecture.

## Purpose
- Capture current behavioral contracts in stable, non-breaking slices.
- Enable bounded implementation PRs with explicit acceptance criteria.
- Preserve trait-first, factory-oriented architecture while making boundary behavior auditable.

## Spec Inventory
| ID | File | Domain | Risk Tier |
|---|---|---|---|
| ZC-SPC-000 | [000-runtime-bootstrap-and-config-spec.md](/Users/benjaminraffour/Code/zeroclaw/docs/specs/000-runtime-bootstrap-and-config-spec.md) | Runtime bootstrap and config | medium |
| ZC-SPC-001 | [001-providers-and-resilience-spec.md](/Users/benjaminraffour/Code/zeroclaw/docs/specs/001-providers-and-resilience-spec.md) | Providers and resilience | high |
| ZC-SPC-002 | [002-channel-and-gateway-ingress-spec.md](/Users/benjaminraffour/Code/zeroclaw/docs/specs/002-channel-and-gateway-ingress-spec.md) | Channels + gateway | high |
| ZC-SPC-003 | [003-tools-and-sandboxing-spec.md](/Users/benjaminraffour/Code/zeroclaw/docs/specs/003-tools-and-sandboxing-spec.md) | Tools execution boundaries | high |
| ZC-SPC-004 | [004-memory-backend-and-search-spec.md](/Users/benjaminraffour/Code/zeroclaw/docs/specs/004-memory-backend-and-search-spec.md) | Memory and persistence | medium |
| ZC-SPC-005 | [005-security-policy-and-pairing-spec.md](/Users/benjaminraffour/Code/zeroclaw/docs/specs/005-security-policy-and-pairing-spec.md) | Security and pairing | high |
| ZC-SPC-006 | [006-runtime-adapter-and-execution-spec.md](/Users/benjaminraffour/Code/zeroclaw/docs/specs/006-runtime-adapter-and-execution-spec.md) | Runtime adapters | medium |
| ZC-SPC-007 | [007-observability-cost-and-audit-spec.md](/Users/benjaminraffour/Code/zeroclaw/docs/specs/007-observability-cost-and-audit-spec.md) | Observability and cost | medium |
| ZC-SPC-008 | [008-plugin-manifest-and-ABI-spec.md](/Users/benjaminraffour/Code/zeroclaw/docs/specs/008-plugin-manifest-and-ABI-spec.md) | Plugin model and ABI | medium |
| ZC-SPC-009 | [009-peripherals-and-hardware-tools-spec.md](/Users/benjaminraffour/Code/zeroclaw/docs/specs/009-peripherals-and-hardware-tools-spec.md) | Peripherals and hardware | medium |
| ZC-SPC-010 | [010-docs-governance-and-reference-update-spec.md](/Users/benjaminraffour/Code/zeroclaw/docs/specs/010-docs-governance-and-reference-update-spec.md) | Docs governance and references | low |

## Format Contract
- Markdown frontmatter includes: `id`, `title`, `status`, `risk_tier`.
- Each spec includes: intent, in-scope files, current behavior, requirements, and acceptance criteria.
- High-risk specs include explicit failure-mode and rollback notes in section 6.

## Tracking
Use [/Users/benjaminraffour/Code/zeroclaw/spec-tracking-review.md](/Users/benjaminraffour/Code/zeroclaw/spec-tracking-review.md) for lifecycle status and review gating.
