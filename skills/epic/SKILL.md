---
name: epic
description: "Manage the project's epic tracker — epics composed of ordered specs with tickets and execution state — backed by a local `.epics/` directory or GitHub Issues. Use when setting up the tracker, organizing specs, publishing a completed spec, or loading tracker context."
---

# Epic

Manage the project tracker: long-lived epics composed of specs numbered in delivery order, each carrying its content, tickets, and execution state.

## Backend

`.epics/README.md` declares the tracker backend. Read the matching reference before any tracker operation:

- `references/local.md` — files under `.epics/` (default)
- `references/github.md` — GitHub Issues and labels

If `.epics/README.md` does not exist, ask the user which backend to use, then follow that reference's setup section.

## Conventions (all backends)

- Use concise kebab-case slugs.
- Treat each epic as a long-lived initiative composed of multiple specs.
- Number specs in intended delivery order with three-digit prefixes.
- Spec status lifecycle: `planned` → `in-progress` → `in-review` → `merged`.
- Use an existing epic when the spec advances the same overarching outcome; create a new epic when it has a distinct outcome, user group, or delivery lifecycle. Ask the user if ambiguous.
- Never overwrite an existing spec or renumber existing specs without explicit user approval.
- Preserve existing project-specific conventions when updating `.epics/README.md`.

## Required reading

Before changing the tracker:

1. Read `.epics/README.md` and the backend reference.
2. Inspect the epics and their ordered specs.
3. When using an existing epic, read every spec and its state in that epic to understand scope, sequence, progress, and possible overlap.
4. Read tickets only when modifying existing planned or active work; they are not required merely to add a new spec.
