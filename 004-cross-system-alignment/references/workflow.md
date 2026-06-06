# Cross-System Alignment Workflow

## Goal

Check whether multiple sources are saying the same thing: implementation, requirements, task tracker, tests, design files, and external systems. The skill finds gaps, ranks impact, and proposes a correction order.

## Information To Collect

- Systems, documents, code paths, and records to compare.
- Authority order, such as production behavior, requirement document, or task tracker.
- Alignment scope and systems that must not be changed.

## Standard Procedure

1. Inventory every source to compare and record the authority order.
2. Extract claims about behavior, status, ownership, dates, and acceptance criteria.
3. Verify important behavioral claims through code inspection or realistic runtime checks when possible.
4. Build a difference table with severity, evidence, affected users, and likely owner.
5. Recommend a correction order and identify which system should be updated first.
6. If changes are made, re-check the relevant source after correction.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Return an alignment matrix, evidence, severity, recommended corrections, owners, blockers, and unverified assumptions.
