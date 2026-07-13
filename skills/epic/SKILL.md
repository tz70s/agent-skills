---
name: epic
description: "Manage a repository-local `.epics` project tracker: initialize its conventions, add a spec to an existing or new epic, and load the context required to work safely. Use when setting up the tracker, organizing specs, or publishing a completed spec."
---

# Epic

Manage `.epics/` as the project's durable, Git-tracked workspace for initiatives and their ordered specs.

## 1. Set up the tracker

If `.epics/README.md` does not exist, create it with this convention:

```text
.epics/
└── <epic-slug>/
    └── specs/
        ├── 001-<spec-slug>/
        │   ├── spec.md
        │   ├── tickets/
        │   └── state.md
        ├── 002-<spec-slug>/
        │   ├── spec.md
        │   ├── tickets/
        │   └── state.md
        └── ...
```

Document these rules in `.epics/README.md`:

- Use concise kebab-case slugs.
- Treat each epic as a long-lived initiative composed of multiple specs.
- Number spec directories in intended delivery order with three-digit prefixes.
- Keep each spec, its derived tickets, and its execution state together.
- A spec directory adopted from an existing PR may hold only `state.md`.
- Preserve existing project-specific conventions when updating the tracker README.

Do not create example epics during setup.

## 2. Add a spec

Decide whether the spec belongs to an existing epic:

- Use an existing epic when the spec advances the same overarching outcome.
- Create a new epic when it has a distinct outcome, user group, or delivery lifecycle.
- If the choice remains ambiguous after reading the required context, ask the user.

For an existing epic, choose the next three-digit sequence after its highest numbered spec. For a new epic, create a concise epic slug and begin with `001`.

Create:

```text
.epics/<epic-slug>/specs/<sequence>-<spec-slug>/
├── spec.md
├── tickets/
└── state.md
```

Write the supplied specification to `spec.md`, create `tickets/`, and initialize `state.md` with a `planned` status. Do not create ticket files until work has been broken down.

## 3. Required reading

Before changing the tracker:

1. Read `.epics/README.md`.
2. Inspect the epic directory names and ordered spec directories.
3. When using an existing epic, read every `spec.md` and `state.md` in that epic to understand its scope, sequence, progress, and possible overlap.
4. Read ticket files only when modifying existing planned or active work; they are not required merely to add a new spec.

Never overwrite an existing spec or renumber existing spec directories without explicit user approval.
