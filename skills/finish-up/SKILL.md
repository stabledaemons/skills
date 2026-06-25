---
name: finish-up
description: Use when code changes are believed complete and before reporting done, opening a PR, or handing work back. Do not use at the start of implementation or for non-code tasks.
---

# Finish Up

Close the loop before claiming completion.

## Steps

1. Review the diff for unrelated changes.
2. Remove dead code, commented-out code, unused imports, and tests made
   obsolete by this change (never tests that are merely failing).
3. Check for accidental duplication or inconsistent naming.
4. Do not add new behavior or unrelated changes while finishing; note anything
   out of scope instead of fixing it here.
5. Run the most relevant checks.
6. Report what changed and what verification ran.

## Final Check

- Is the diff scoped to the task?
- Are claims backed by commands, tests, or file inspection?
- Are remaining risks or skipped checks stated clearly?
