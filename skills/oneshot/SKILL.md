---
name: oneshot
description: Drive one spec end to end — spec, tickets, work, then schedule recurring babysit passes for its PR. Use when the user wants the whole pipeline from an idea or discussion in one go.
---

# Oneshot

Chain the pipeline skills for one spec. Each stage's own rules and gates apply unchanged; this skill adds no shortcuts.

## Process

1. Run the `spec` skill to confirm intent and publish the spec.
2. Run the `tickets` skill and get the breakdown approved.
3. Run the `work` skill on the published spec.
4. Once the PR is submitted, start a recurring driver for the `babysit` skill — a loop or scheduled agent — at a cadence agreed with the user (default 30 minutes). If the user defers submission for local review, stop here and note that babysit can be scheduled after submission.
