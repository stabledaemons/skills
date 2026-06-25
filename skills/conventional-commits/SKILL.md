---
name: conventional-commits
description: Use when preparing, naming, reviewing, or creating commits for completed code or documentation changes. Do not use during implementation unless the user asks for commit planning.
---

# Conventional Commits

Create small, meaningful commits with conventional messages.

## Format

Use:

```text
type(scope): summary
```

Official semver-significant types:

- `feat`: user-visible feature; maps to a minor release.
- `fix`: user-visible bug fix; maps to a patch release.

Common extended types:

- `build`: build system, dependency, packaging, or lockfile change.
- `chore`: maintenance that does not affect runtime behavior.
- `ci`: continuous integration, release, or automation workflow change.
- `docs`: documentation-only change.
- `perf`: performance improvement without changing intended behavior.
- `refactor`: behavior-preserving code change.
- `revert`: revert a previous commit.
- `style`: formatting, whitespace, lint-only, or code style change.
- `test`: test-only change.

Use the repository's configured type list when it exists. If a change honestly
fits multiple types, prefer splitting the commit.

## Rules

1. Keep commits atomic and reviewable.
2. Choose the narrowest accurate type.
3. Use a scope when it clarifies the affected area.
4. Write the summary in imperative mood.
5. Do not hide behavior changes in `refactor` or `chore`.
6. Mark breaking changes with `!` after the type or scope, or with a
   `BREAKING CHANGE:` footer.

## Final Check

- Does the commit message match the actual diff?
- Is the commit small enough to review?
- Would the type make sense in a changelog?
