---
name: spec
description: Turn an idea or existing conversation into a confirmed project spec. Use the `grilling` skill when intent is incomplete, synthesize the agreed context without repeating discovery, then publish with the `epic` skill.
---

Use this skill as the entry point for turning intent into a published spec.

## Process

1. Check whether the spec template below can be filled from confirmed conversation content — things the user said or explicitly agreed to, not your inferences:

   - **Objective** and **Out of Scope** must be fully covered.
   - **Technical Decisions** and **Testing Decisions** need only capture the decisions that were actually made. They may be incomplete, as long as every gap is non-blocking — a decision that would change the outcome, the scope, or any user story is blocking and must be resolved, not left open.

2. If a required section needs invention, or an open decision would change what gets built, use the `grilling` skill to close exactly those gaps. Do not write the spec until the user confirms the shared understanding. Do not repeat discovery for sections the conversation already covers.

3. Explore the repo to understand the current state of the codebase, if you haven't already. Facts live in the codebase — look them up rather than asking; only decisions go to the user.

4. Synthesize the confirmed conversation into the template below. Record only the decisions that were actually made; do not invent decisions.

5. Use the `epic` skill to publish the completed spec.

<spec-template>

## Objective

What are we building and why? Who is the user? What does success look like?

## User Stories

A LONG, numbered list of user stories. Each user story should be in the format of:

1. As an <actor>, I want a <feature>, so that <benefit>

<user-story-example>
1. As a mobile bank customer, I want to see balance on my accounts, so that I can make better informed decisions about my spending
</user-story-example>

This list of user stories should be extremely extensive and cover all aspects of the feature.

## Technical Decisions

A list of technical decisions that were made. This can include:

- The modules that will be built/modified
- The interfaces of those modules that will be modified
- Technical clarifications from the developer
- Architectural decisions
- Schema changes
- API contracts
- Specific interactions

Do not include specific file paths or implementation code, because they become outdated quickly. You may include a minimal schema, interface, state machine, or type shape when it is the clearest way to capture an agreed technical contract. Keep it decision-focused and omit working implementation details.

## Testing Decisions

A list of testing decisions that were made. Include:

- A description of what makes a good test (only test external behavior, not implementation details)
- Which modules will be tested
- Prior art for the tests (i.e. similar types of tests in the codebase)

## Out of Scope

A description of the things that are out of scope for this spec.

## Further Notes

Any further notes about the feature.

</spec-template>
