---
name: refactor-safely
description: Use before changing existing behavior, refactoring shared logic, extracting helpers from existing code, moving code, renaming public symbols, or editing code with unknown callers. For orienting in a new area before writing fresh code, use explore-before-edit instead. Do not use for brand-new isolated code.
---

# Refactor Safely

Protect existing behavior before changing structure.

Behavior means observable results for the same inputs: return values, raised
errors, side effects, and public contracts, not internal structure.

## Steps

1. Find the callers and entry points you can locate: direct calls, exports,
   dynamic or reflective access, and public API consumers. If callers are
   external or unknown, treat the change as contract-sensitive and widen
   verification accordingly.
2. Identify behavior that must remain unchanged.
3. Locate existing tests or add characterization tests (tests that pin current
   behavior as-is), and confirm they pass before restructuring. Where tests are
   not feasible, capture current behavior with a documented manual check of
   specific inputs and outputs.
4. State the likely blast radius (which code and callers this change can
   affect) in one sentence before editing.
5. Make the smallest change that achieves the intended restructuring without
   altering behavior.
6. Run focused tests or repeat the documented manual check for the affected
   code paths and their callers, and confirm the behavior still matches the
   baseline.

## When Not To Use

Do not use this skill to justify broad cleanup during an unrelated feature. If
the cleanup is not required, leave it for a separate task.

## Final Check

- Are callers mapped?
- Is current behavior pinned by tests, or by a documented manual check of
  specific inputs and outputs?
- Is the change behavior-preserving unless the user asked otherwise?
