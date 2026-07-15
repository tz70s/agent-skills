# Agent Skills

Agent skills for project use.

## Local skills

| Skill | Purpose | Source |
| --- | --- | --- |
| [`epic`](skills/epic/SKILL.md) | Manages the epic tracker — local `.epics/` or GitHub Issues backend — and publishes specs | Original |
| [`spec`](skills/spec/SKILL.md) | Runs `grilling` first unless already done, synthesizes a spec, then publishes through `epic` | Adapted from [`mattpocock/skills`](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-spec/SKILL.md) |
| [`tickets`](skills/tickets/SKILL.md) | Breaks a published spec into dependency-aware vertical-slice tickets | Adapted from [`mattpocock/skills`](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-tickets/SKILL.md) |
| [`work`](skills/work/SKILL.md) | Implements a spec's tickets end to end with per-ticket checkpoints, then submits the spec's PR | Original |
| [`babysit`](skills/babysit/SKILL.md) | One idempotent pass over an epic's stacked spec PRs: review comments, CI, rebasing | Original |
| [`oneshot`](skills/oneshot/SKILL.md) | Drives one spec end to end: `spec` → `tickets` → `work`, then schedules recurring `babysit` | Original |

## Open source skills

| Skill | Purpose | Relationship | Source |
| --- | --- | --- | --- |
| [`grilling`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md) | Interviews the user one question at a time to stress-test a plan or design | Standalone skill | `mattpocock/skills` |

## Installation

```bash
npx skills add https://github.com/mattpocock/skills --skill grilling
```
