---
name: handle-failures
description: Use during writing when adding catch blocks, error branches, retries, validation failures, fallbacks, or user-facing failure messages. Do not use when no failure path is being changed.
---

# Handle Failures

Make failures explicit, actionable, and consistent with the surrounding code.

## Rules

1. Do not silently swallow errors, and do not catch broader than you actually
   handle — let unrelated errors propagate.
2. Either handle the error, rethrow with useful context, or document why ignoring
   it is correct. Preserve original error details when they help debugging.
3. On failure, leave a consistent state: release resources, roll back partial
   writes, and do not commit half-finished work.
4. Match the repository's existing error style: find a nearby error path and
   mirror its error type, logging call, and message format.
5. For user-facing failures, write an actionable message and keep internal
   details — stack traces, secrets, identifiers — out of it; log those instead.
6. For retries and fallbacks, bound retry attempts, do not retry errors that
   cannot succeed, and never let a fallback hide that the primary path failed —
   record it.
7. Include tests for the failure paths you add or change.

## Final Check

- Can a developer understand what failed and why?
- On failure, is the system left in a consistent state — resources freed and
  partial work rolled back?
- Is the failure observable in logs, return values, UI, or tests?
- Do user-facing messages keep internal and sensitive detail out?
