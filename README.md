# Agent Skills

Agent skills for project use.

## Local skills

| Skill | Purpose | Source |
| --- | --- | --- |
| [`epic`](skills/epic/SKILL.md) | Sets up and manages the local epic tracker and publishes specs | Original |
| [`spec`](skills/spec/SKILL.md) | Clarifies intent with `grilling` when needed, synthesizes a spec, then publishes through `epic` | Adapted from [`mattpocock/skills`](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-spec/SKILL.md) |
| [`tickets`](skills/tickets/SKILL.md) | Breaks a published spec into dependency-aware vertical-slice tickets | Adapted from [`mattpocock/skills`](https://github.com/mattpocock/skills/blob/main/skills/engineering/to-tickets/SKILL.md) |

## Open source skills

| Skill | Purpose | Relationship | Source |
| --- | --- | --- | --- |
| [`grilling`](https://github.com/mattpocock/skills/blob/main/skills/productivity/grilling/SKILL.md) | Interviews the user one question at a time to stress-test a plan or design | Standalone skill | `mattpocock/skills` |

## Installation

```bash
npx skills add https://github.com/mattpocock/skills --skill grilling
```
