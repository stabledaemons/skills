---
name: house-style
description: Use during code authoring when adding or changing names, control flow, functions, helpers, modules, or repeated logic. Apply while writing production code or tests. Do not use for non-code tasks.
---

# House Style

Keep code readable while it is being written.

## Rules

1. Use intention-revealing names from the project domain; name non-obvious
   magic values instead of inlining them.
2. Prefer clear control flow: guard clauses over deep nesting.
3. Keep functions focused on one job.
4. Remove unjustified duplication, but avoid premature abstraction.
5. Match nearby style for imports, file shape, naming, and error handling.
6. Follow the project's configured formatter and linter; do not hand-format
   against them.
7. Keep changes scoped to the task; do not fold in unrelated refactors or
   cleanup while authoring.

## When Not To Abstract

Do not extract shared code only because two blocks look similar. Extract only
when they represent the same concept or behavior and the shared name is clear.

## Final Check

- Are names meaningful without extra context, with non-obvious magic values
  named?
- Is nesting shallow enough to scan?
- Does each function have one clear responsibility?
- Is repeated code either justified or intentionally shared?
- Does the code satisfy the project's formatter and linter?
- Is the change scoped to the task, with unrelated cleanup left out?
