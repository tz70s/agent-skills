---
name: tickets
description: Break a published spec into a set of dependency-aware, tracer-bullet implementation tickets stored in its epic tracker directory. Use after the spec and epic skills when work needs to be decomposed into agent-sized, verifiable slices.
---

# Tickets

Turn one published spec into a set of vertical-slice tickets, each declaring the tickets that block it.

## Process

### 1. Load the spec context

Use the epic skill to locate the target spec and load the tracker context it requires. Read the selected `spec.md` and `state.md` in full. If ticket files already exist, read them before proposing changes.

Do not rewrite or expand the spec. If it lacks a decision required for ticketing, identify the gap and ask the user rather than inventing it.

### 2. Explore the codebase

Explore enough of the repository to understand its current architecture, terminology, and existing testing patterns. Look for small preparatory changes that would make the feature easier to implement.

### 3. Draft vertical slices

Break the spec into tracer-bullet tickets:

- Make each ticket a narrow but complete path through the layers it needs, not a horizontal task for only one layer.
- Make each completed ticket independently demonstrable or verifiable.
- Size each ticket to fit in one fresh agent context.
- Put necessary preparatory work first.
- Give each ticket explicit blocking edges. A ticket with no blockers can start immediately.

Wide mechanical refactors are the exception to vertical slicing. For changes whose blast radius prevents a green standalone slice, use expand–migrate–contract:

1. Add the new form alongside the old.
2. Migrate callers in independently safe batches.
3. Remove the old form only after every migration completes.

Represent each phase or batch as a ticket with the appropriate blockers. Keep the repository green between tickets whenever possible.

### 4. Confirm the breakdown

Present the proposed tickets as a numbered list. For each ticket, show:

- **Title**
- **Blocked by**
- **What it delivers**

Ask whether the granularity and blocking edges are correct and whether any tickets should be merged or split. Iterate until the user approves the breakdown.

### 5. Publish the tickets

Write one file per approved ticket under the selected spec's `tickets/` directory:

```text
.epics/<epic>/specs/<spec>/tickets/<NN>-<ticket-slug>.md
```

Number tickets from `01` in dependency order, blockers first. Never combine all tickets into one file and never overwrite existing tickets without explicit approval.

Use this template:

```markdown
# <NN> — <Ticket title>

**What to build:** <the end-to-end behavior this ticket delivers from the user's perspective>

**Blocked by:** <ticket numbers and titles, or "None — can start immediately">

**Status:** <ready-for-agent or blocked>

## Acceptance criteria

- [ ] Criterion 1
- [ ] Criterion 2
```

Set `ready-for-agent` only when every blocker is complete; otherwise set `blocked`. The current frontier is every ticket whose blockers are complete.

Update the selected spec's `state.md` without discarding existing history. Record that ticketing is complete and list the current frontier.

Do not include specific file paths or implementation code in tickets, because they become outdated quickly. You may include a minimal schema, interface, state machine, or type shape when it is the clearest way to capture an agreed technical contract. Keep it decision-focused and omit working implementation details.
