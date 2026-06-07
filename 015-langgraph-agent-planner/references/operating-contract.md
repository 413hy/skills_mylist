# Operating Contract

## Hard Rules

- Understand the user goal before acting. Do not silently expand a short request into a larger scope.
- Prefer facts from local files, code, docs, tickets, or user-provided material before asking for missing information.
- Before implementation, define the current objective, deliverable, out-of-scope items, and validation method.
- For any final product, feature, script, demo, agent, sync result, pull request, operational document, handoff prompt, user story, or plan, run realistic scenario validation with a daily-use example. API, function, build, or command checks are supporting evidence only.
- Fix failed validation items and rerun the failed scenario before delivery. Do not present failed items as optional follow-up unless the user explicitly accepts the remaining risk.

## Interaction Recipe

1. Identify the task type: document generation, code implementation, system sync, learning guidance, agent planning, multi-session routing, or review closeout.
2. Read this skill's SKILL.md first. Load references/workflow.md when the task needs detailed procedure.
3. Load references/scenario-validation.md before delivering anything user-facing or operational.
4. Build a short requirement mirror when ambiguity, risk, or implementation impact exists.
5. Execute the task in the smallest safe scope.
6. Deliver with evidence, untested items, blockers, and residual risk.

## Failure Handling

- If a test account, sample data, permission, target system, or runtime environment is missing, try to discover it from the project first; otherwise list it as a blocker.
- If realistic scenario validation fails, repair the deliverable or narrow the claim, then rerun the failed scenario.
- If the user asks to skip validation, state the residual risk clearly.
- If the task is a document, plan, or prompt, validate it with a small representative example before treating it as complete.

## Evidence Standard

Validation evidence should include scenario name, input data or account, operation steps, expected result, actual result, evidence artifact when available, and pass/fail conclusion. For UI or browser work, prefer visible page state, screenshot, DOM state, logs, or target-system links as evidence.
