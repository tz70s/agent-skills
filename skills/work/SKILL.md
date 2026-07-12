---
name: work
description: Implement a spec's tickets end to end on the spec's branch, checkpointing the tracker per ticket, and submit the spec's PR when the last ticket completes. Resumes interrupted runs from tracker state. Use for autonomous implementation after tickets are published.
---

# Work

Drive one spec from ready tickets to a submitted PR. Tickets are commits on the spec's branch; each spec becomes exactly one PR, stacked on the previous spec in the epic.

## Process

### 1. Select the spec

The user must name the target spec; if none is given, ask rather than guessing. Use the epic skill to locate it and load the tracker context it requires.

Read the spec's `state.md` and ticket statuses first. Never redo a completed ticket; continue from the current frontier.

Do not start a spec until the previous spec in the epic is at least `in-review`.

### 2. Check out the spec branch

Each spec has one branch: `<epic-slug>/<NNN>-<spec-slug>`. Create it if missing:

- Base it on the previous spec's branch while that spec's PR is open.
- Base it on the default branch otherwise.

Set the spec's `state.md` status to `in-progress` when its first ticket starts.

### 3. Implement tickets until the spec is done

Loop over the spec's tickets, one at a time:

1. Take the lowest-numbered `ready-for-agent` ticket. Never start a ticket whose blockers are incomplete.
2. Implement exactly what the ticket describes. Follow the repository's conventions for structure, style, testing, and commands. Do not expand scope beyond the ticket.
3. Verify every acceptance criterion and run the repository's test suite. Commit to the spec branch.
4. Checkpoint the tracker before the next ticket: mark the ticket complete, check off its acceptance criteria, flip newly unblocked tickets to `ready-for-agent`, and record the frontier in `state.md`.

### 4. Submit the spec PR

When the last ticket completes, open one PR for the whole spec:

- Base per the stacking rule in step 2.
- Synthesize the PR description from `spec.md`.
- Record the PR URL in `state.md` and set the status to `in-review`.

## Stop and surface instead of proceeding

- An acceptance criterion cannot be met without changing the spec's scope or contradicting a spec decision.
- A ticket's assumptions no longer match the codebase.
- Tests fail for pre-existing reasons unrelated to the ticket.

Checkpoint the tracker before stopping; the next `work` invocation resumes from the frontier.
