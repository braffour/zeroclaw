---
id: ZC-SPC-005
title: Security policy, pairing, and secret handling
status: draft
risk_tier: high
---
## 1. Intent
Document current secure-by-default controls and the boundaries where policy/secret handling is enforced.

## 2. In scope
- `src/security/**`
- pairing flow and policy checks in runtime bootstrap and tool boundaries
- secret/config load boundaries

## 3. Current behavior to preserve
- Deny-by-default patterns are explicit.
- Secrets are not logged and are scoped to subsystem needs.
- Policy and pairing checks gate high-risk operations.

## 4. Requirements
- Specify exactly which operations require elevated permission.
- Define error/lockout behavior on policy mismatch.
- Define secret rotation/revocation expectations for operators.

## 5. Acceptance criteria
- Explicit threat-aware scenarios:
  - revoked credential
  - invalid pairing state
  - over-broad tool request from untrusted source
  - logging path attempted secret leak prevention
