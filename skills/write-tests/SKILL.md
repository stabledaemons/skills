---
name: write-tests
description: Use during writing when adding, changing, or repairing tests for code behavior. Use before refactors that need a safety net. Do not use for mechanical snapshot updates or tests that only mirror implementation details.
---

# Write Tests

Test observable behavior, not private implementation trivia.

Behavior is what a user or caller can observe: returned values, raised errors,
state changes, persisted data, emitted events, rendered output, or calls to a
public boundary. Private implementation trivia is the internal path used to get
there: helper names, local variable names, loop shape, private method calls, or
temporary data structures.

## Steps

1. Name the behavior in caller terms before choosing assertions.
2. Exercise the public entry point used by the caller whenever one exists.
3. Use real inputs and outputs for in-process behavior.
4. Mock only the boundaries listed in When To Mock below; do not mock the code
   path you are trying to verify.
5. Cover the normal path, at least one relevant failure path, and any boundary
   case named by the code contract or bug report.
6. Keep each test independent: it should not depend on test order, leaked
   state, network access, wall-clock timing, or data left by another test.
7. Structure the test so the setup, action, and assertions are easy to separate.
8. Name the test after the expected behavior, not after the implementation
   detail it happens to touch.

## Example

A refactor-resistant test for `calculateInvoiceTotal(items, taxRate)` checks
that taxable and non-taxable items produce the expected total and that invalid
input raises the documented error.

A brittle test checks that `calculateInvoiceTotal` calls a private helper named
`sumLineItems` exactly once. That test can fail after a harmless rename or
inlining even though callers still get the right total.

## When To Mock

Mock a dependency when using the real dependency would make the test cross a
process, network, filesystem, clock, random, payment, email, analytics, or other
unsafe boundary. Prefer a small fake or stub that preserves the boundary
contract over assertions about every internal call.

## Final Check

- Would the test fail if the user-visible behavior broke?
- Would the test keep passing after a behavior-preserving rename, extraction, or
  inlining?
- Are success, failure, and relevant boundary cases covered?
- Is the test independent of order, shared state, live services, and time?
- Did you run the focused test or explain why not?
