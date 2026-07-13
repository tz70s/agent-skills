# Local backend

Track everything in a Git-tracked `.epics/` directory.

## Layout

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

## Setup

Create `.epics/README.md` declaring `backend: local`, this layout, and the conventions from SKILL.md. Do not create example epics.

## Add a spec

For an existing epic, choose the next three-digit sequence after its highest numbered spec. For a new epic, create a concise epic slug and begin with `001`. Create the spec directory with `spec.md` holding the supplied specification, an empty `tickets/`, and `state.md` with status `planned`. Do not create ticket files until work has been broken down.

## Tickets

One file per ticket: `tickets/<NN>-<ticket-slug>.md`, written by the tickets skill.

## Status and history

`state.md` holds the status, the PR URL once submitted, and an append-only history. Update the status in place; append history entries without discarding existing ones.

## Adopted PRs

A spec directory adopted from an existing PR may hold only `state.md`.
