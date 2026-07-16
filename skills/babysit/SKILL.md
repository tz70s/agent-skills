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

Walk these steps in order for every PR. Skip a step only when its check comes back clean — never leave one unchecked.

1. **Merged?** If merged: set the spec's status to `merged`, rebase the next spec's branch onto the default branch, retarget its PR base, and move to the next PR.
2. **Review comments.** Address implementation-level comments with `git commit --fixup <ticket commit>` on the spec branch and reply on the thread; step 4 auto-squashes them. Escalate comments that change scope or contradict a spec decision to the user; do not act on them.
3. **CI.** Fix failures caused by this PR's changes, also as fixup commits. Report pre-existing or unrelated failures and leave them.
4. **Rebase.** When the base branch has advanced, the platform reports the PR unmergeable, or fixup commits were added: rebase onto the current base with `git rebase --autosquash`, keeping history aligned with the ticket split. Never rebuild the branch with cherry-pick and `git reset --hard`. Resolve a conflict when the overlap is mechanical or one side clearly wins; surface a conflict that requires choosing between intents — do not guess.
5. **Verify and push.** When any step changed the branch, rerun the repository's test suite, then push with `git push --force-with-lease` — one stacked branch at a time, in stack order.

### 3. Record the pass

Append what was done to each touched spec's history so the next pass does not repeat work.

When no specs remain `in-review`, report that there is nothing left to babysit and stop the loop or schedule driving this skill. Repeated no-op passes while PRs await review action are expected — do not stop the loop for them.

## Stop and surface instead of proceeding

- A review comment requests a scope or design change.
- A rebase conflict requires choosing between intents.
- CI fails for reasons unrelated to the PR.
- The stack diverged from the tracker (a PR merged out of order, closed, or retargeted by hand).

When escalating, also stop the loop or schedule driving this skill so no pass runs while the user resolves it.
