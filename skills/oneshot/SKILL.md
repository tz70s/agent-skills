---
name: oneshot
description: Run the whole pipeline autonomously for one spec — collect required inputs upfront, self-grill to settle the design, then spec, tickets, work, and a scheduled babysit without further user input. Use when the user wants an idea driven end to end by the agent alone.
---

# Oneshot

Drive one spec through the pipeline autonomously. Collect what only the user can decide upfront; after that, replace the stages' interactive gates with your best judgment.

## Process

1. Collect required inputs in one round before starting: the tracker backend when none is declared, anything essential missing from the idea, and the babysit cadence (default 30 minutes). Do not ask again after this point.

2. Run a self-grilling session: walk the design tree as the `grilling` skill prescribes, but answer each question yourself with your recommended answer. Record the decisions so the spec and its PR carry them for review.

3. Run the pipeline with gates self-answered:
   - `spec` — the self-grilling session satisfies its grilling gate.
   - `tickets` — review and approve the breakdown yourself.
   - `work` — submit the draft PR without asking.

4. Schedule the recurring `babysit` driver at the agreed cadence. Its escalation rules still apply — autonomy ends where babysit stops the loop and surfaces.
