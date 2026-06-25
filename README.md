# Foundational Agent Skills

This repo defines small, trigger-based skills for keeping code clean, readable,
and maintainable. The skills are organized around three development phases, but
the files are split by trigger so agents can load only the relevant procedure.

## Core Philosophy

Code should be easy for a human to read, change, review, and delete. These
skills exist to make agents slow down at the moments where maintainability
usually gets lost: before they understand the existing code, while they are
authoring new logic, and when they are about to call the work done.

The skills should stay:

- Procedural enough for coding agents to follow.
- Small enough to route cleanly.
- Explicit about when not to apply a rule.
- Focused on readable, maintainable code over clever code.

## Organization

Phases organize the philosophy. Triggers organize the files. Each skill lives in
`skills/<skill-name>/SKILL.md`, and its `description` frontmatter is the routing
surface — so the description, not this README, is the source of truth for when a
skill loads.

The skills cover the phases of development work, and apply in two modes —
writing new code and changing existing code. `AGENTS.md` is the canonical guide
for how the phases and modes shape a task.

## V1 Skills

### Before Writing

- `explore-before-edit`: inspect the codebase before adding or changing code.
- `refactor-safely`: map blast radius and pin behavior before changing existing
  code.

These skills protect context. They keep agents from inventing patterns,
duplicating helpers, or refactoring behavior they have not pinned down.

### During Writing

- `house-style`: keep names, control flow, functions, reuse, and change scope
  clean while authoring code.
- `comments-explain-why`: write comments only when they clarify intent,
  tradeoffs, constraints, or surprising behavior.
- `handle-failures`: write explicit, useful error paths.
- `vet-dependency`: check existing project options before adding dependencies.
- `write-tests`: test real behavior rather than implementation trivia.

These skills shape the code as it is produced. They keep implementation boring,
readable, local to the task, and aligned with the project.

### Finishing

- `finish-up`: review the diff, delete dead code, run checks, and verify claims.
- `conventional-commits`: create small commits with conventional messages.

These skills close the loop. They keep finished work reviewable, verified, and
easy to understand later.

## Provenance

These skills are hand-authored and reviewed in this repository.

## Skill Shape

Each skill lives in `skills/<skill-name>/SKILL.md` with `name` + `description`
frontmatter and a short, procedural body. See `CONTRIBUTING.md` for the full
authoring bar.

## Validation

This is a plain-text library — only static frontmatter/text checks belong here;
routing and behavioral validation live in the consuming project. See
`CONTRIBUTING.md` for the validation scope.
