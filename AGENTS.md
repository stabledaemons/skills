# Agent Guidance

This repository contains foundational engineering hygiene skills for coding
agents. Keep the skills procedural, concrete, and easy to route.

When doing coding work, organize behavior into three phases:

1. Before writing: inspect existing code, find patterns, map callers, and pin
   existing behavior before changing it.
2. During writing: keep code readable, small, tested, consistent, and
   non-duplicative.
3. Finishing: review the diff, remove dead code, verify claims, and commit
   cleanly.

Two modes change how the phases apply. For new code, move forward through the
phases. For changing existing code, pin current behavior first, keep the change
behavior-preserving, and treat the diff as the review artifact: intentional,
scoped, and easy to verify.

Use skills whose descriptions match the current phase and action. Do not load a
skill only because it is philosophically related; load it when the trigger fits
the task.
