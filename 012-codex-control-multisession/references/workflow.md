# Codex Control Multi-Session Workflow

## Goal

Use one control session to clarify requirements, maintain state, split work into numbered sessions, and produce paste-ready handoffs. The control session routes work; each worker session owns implementation and evidence.

## Information To Collect

- Overall goal, current state, constraints, repositories, systems, and priority.
- Which sessions exist or should be created.
- Expected outputs, validation evidence, and state anchor format.

## Standard Procedure

1. Clarify the overall requirement and write a requirement mirror.
2. Define session roles, ownership boundaries, inputs, outputs, and forbidden overlap.
3. Generate numbered handoff prompts for each session.
4. Require each session to return changed files, decisions, blockers, tests, and scenario evidence.
5. Maintain a state anchor that can be pasted into future turns.
6. Reconcile returned evidence before declaring the overall work complete.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Provide session handoff prompts, state anchor, ownership map, validation duties, and integration checklist.
