# Understand Code Before Change Workflow

## Goal

Make changes in an existing codebase only after understanding the relevant architecture, data flow, conventions, and tests. The skill prevents blind edits and requires realistic validation of changed behavior.

## Information To Collect

- Requested change, target behavior, relevant files or modules, and acceptance criteria.
- Repository patterns, test commands, run commands, and protected areas.
- Sample data, test accounts, and user workflows needed for validation.

## Standard Procedure

1. Inspect the directory, relevant files, imports, routes, data models, and existing tests before editing.
2. Summarize the current behavior and the intended change.
3. Choose the smallest change that fits existing patterns.
4. Edit only the necessary files.
5. Run relevant tests and build checks.
6. Validate the changed user-facing workflow with realistic operations, then report evidence.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Report code understanding, files changed, test results, scenario validation, unresolved risks, and any follow-up needed.
