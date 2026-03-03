---
id: ZC-SPC-009
title: Peripherals and hardware tool interfaces
status: draft
risk_tier: medium
---
## 1. Intent
Document hardware adapters and tool exposure model for GPIO/STM32/RPi-like peripherals.

## 2. In scope
- `src/peripherals/**`
- board-specific tool exposure contract
- `docs/hardware-peripherals-design.md`

## 3. Current behavior to preserve
- Peripheral implementations expose tool sets through `tools()`.
- Hardware capabilities are typed and intentionally constrained.

## 4. Requirements
- Require safe failure behavior for missing/unavailable boards.
- Document firmware/tooling assumptions and command-side validations.
- Explicitly block unsafe operations by default.

## 5. Acceptance criteria
- Scenario coverage includes device unavailable, unsupported board ID, and unsafe request rejection.
