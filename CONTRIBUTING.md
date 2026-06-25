# Contributing

This repository is a plain-text library of portable engineering hygiene skills.
Keep contributions small, concrete, and easy for multiple agent harnesses to
consume.

## Skill Authoring Bar

Each skill must live at `skills/<skill-name>/SKILL.md` and use only valid skill
frontmatter:

```yaml
---
name: skill-name
description: Use when <trigger>. Do not use for <exclusion>.
---
```

Write the `description` as the routing contract:

- Lead with the concrete trigger.
- Include important exclusions; the wording is flexible ("Do not use for…",
  "Do not use when…", "Do not use during…").
- Keep it portable across Codex, Claude Code, and other skill-aware agents.
- Do not rely on custom frontmatter for routing.

Write the body as a short procedure:

- Prefer steps or rules over essays.
- Include a final check.
- Keep the skill focused on one job.
- Avoid anything tied to one specific project — its tooling, policy, repository
  names, paths, or runtime layout. Naming cross-ecosystem tools (npm, cargo, go)
  as examples is fine.
- Put phase guidance in `AGENTS.md`, not in per-skill metadata.

## Validation Scope

This repo should only carry static content checks, such as valid frontmatter and
well-formed skill text. Routing and behavioral validation belong in the consuming
project, because they depend on the harness, model, prompts, configuration
layout, and installed tooling.

Do not add routing or eval harnesses to this repository.
