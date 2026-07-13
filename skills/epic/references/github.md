# GitHub backend

Track epics and specs as GitHub issues; tickets live inside the spec issue body. Use the `gh` CLI.

## Mapping

| Concept | Representation |
| --- | --- |
| Epic | Issue labeled `epic`; body holds an outline and a task list of spec issues (`- [ ] #<n>`) |
| Spec | Issue labeled `spec`, titled `NNN — <title>`; body holds the spec content |
| Ticket | `### NN — <title>` section under `## Tickets` in the spec issue body |
| Status | Labels `status:planned`, `status:in-progress`, `status:in-review`; `merged` = issue closed |
| History | Issue comments |
| PR link | The spec PR body says `Closes #<n>`; merging closes the spec issue |

## Setup

Create `.epics/README.md` declaring `backend: github`. Ensure the labels exist: `epic`, `spec`, `status:planned`, `status:in-progress`, `status:in-review` (`gh label create`).

## Add a spec

Create an issue labeled `spec` and `status:planned`, titled `NNN — <title>` using the next sequence in the epic, body holding the supplied specification. Add `- [ ] #<n>` to the epic issue's task list, creating the epic issue first if needed.

## Tickets

Append a `## Tickets` section to the spec issue body: one `### NN — <title>` subsection per ticket with its **Blocked by** line and acceptance criteria as checkboxes. A ticket is complete when all its checkboxes are checked; ready when its blockers are complete. Check boxes off by editing the issue body.

## Status and history

Keep exactly one `status:*` label per spec issue; move status with `gh issue edit --add-label/--remove-label`. `merged` needs no label — the spec PR's `Closes #<n>` closes the issue on merge. Record checkpoints and babysit passes as issue comments.

## Adopted PRs

Adopt an existing PR as a spec issue labeled `spec` and `status:in-review` whose body holds only the PR link; no spec content or tickets are required.
