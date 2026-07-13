---
name: babysit
description: Run one idempotent maintenance pass over an epic's open spec PRs — address review comments, fix CI failures, and rebase or restack after merges. Use on a recurring loop or schedule; each pass reads its state from the epic tracker.
---

# Babysit

Keep an epic's stacked spec PRs healthy. One invocation is one stateless pass; recurrence comes from a loop or schedule. The tracker is the memory between passes.

## Process

### 1. Collect the open PRs

Use the epic skill to locate the epics and load the tracker context it requires. Gather every spec with status `in-review` and a recorded PR — for the named epic, or across all epics when none is named. Process them in spec-sequence order, lowest first, so restacking cascades correctly.

When the user requests babysitting PRs that are not in the tracker, adopt them first: register each under the epic the user names (or a new epic) as a spec holding only its state — status `in-review` and the PR link. No spec content or tickets are required. Derive adopted PRs' stack order from their base branches.

### 2. Handle each PR

**Merged.** Set the spec's status to `merged`. Rebase the next spec's branch onto the default branch and retarget its PR base.

**CI failing.** Fix failures caused by this PR's changes. Report pre-existing or unrelated failures and leave them.

**Review comments.** Address implementation-level comments with commits on the spec branch and reply on the thread. Escalate comments that change scope or contradict a spec decision to the user; do not act on them.

**Base moved.** Rebase the spec branch onto its updated base and force-push per the repository's conventions. Force-push stacked branches one by one, in stack order. Resolve textual conflicts; surface semantic ones.

### 3. Record the pass

Append what was done to each touched spec's history so the next pass does not repeat work.

When no specs remain `in-review`, report that there is nothing left to babysit and stop the loop or schedule driving this skill. Repeated no-op passes while PRs await review action are expected — do not stop the loop for them.

## Stop and surface instead of proceeding

- A review comment requests a scope or design change.
- A rebase conflict is semantic rather than textual.
- CI fails for reasons unrelated to the PR.
- The stack diverged from the tracker (a PR merged out of order, closed, or retargeted by hand).

When escalating, also stop the loop or schedule driving this skill so no pass runs while the user resolves it.
