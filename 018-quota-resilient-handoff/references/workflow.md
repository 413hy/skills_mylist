# Quota-Resilient Handoff Workflow

## Goal

Preserve task quality during quota, rate-limit, token, or context pressure. The agent should either finish to the agreed delivery standard or pause with enough state and automation support to resume later.

## Standard Procedure

1. Identify the latest user requirement. Include corrections and constraints from the newest user messages.
2. Inspect continuity state:
   - workspace path;
   - git branch and remote;
   - changed, staged, and untracked files;
   - relevant logs or validation output;
   - installed/runtime state when the task involves installation or sync.
3. Identify risk:
   - visible quota/rate-limit/retry-after message;
   - long remaining work or validation;
   - context pressure;
   - incomplete commit, push, PR, sync, installation, or verification.
4. If the remaining work can still be completed properly, continue normally.
5. If the remaining work cannot be completed properly, stop implementation and build a recovery package.
6. Write a handoff file for repo work when appropriate:
   `docs/codex-handoffs/YYYY-MM-DD-<short-slug>.md`
7. Create or update a heartbeat/automation when the platform supports it.
8. Record the automation ID or name, schedule assumption, and prompt summary. Do not mark the continuation as executed just because it was scheduled.
9. Report the pause status without claiming completion.
10. On resume, read the handoff, inspect current state again, check whether any prior automation actually executed when relevant, and continue from the next action.

## Recovery Package Template

Use this structure for handoff files and automation prompts:

```markdown
# Codex Resume Handoff

## Latest User Requirement

<Restate the newest instruction, including delivery and validation standards.>

## Current Status

- Workspace:
- Branch:
- Remote:
- In scope:
- Out of scope:

## Completed Evidence

- <Completed step and proof.>

## Pending Work

- <Unfinished step.>

## Blocked Or Failed Commands

- Command:
- Result summary:
- Retry time:

## Next Actions

1. <Exact next action.>
2. <Exact next action.>

## Realistic Validation Gate

- Scenario:
- Input/sample:
- Expected:
- Actual:
- Status:

## Do Not Touch

- <Directories, systems, files, or user changes outside scope.>

## Resume Prompt

Continue in `<absolute workspace>` from this handoff. First confirm the latest user request and current git state. Do not claim completion until the pending realistic validation and delivery steps pass.
```

## Automation Prompt Requirements

The automation prompt must be self-contained. Include:

- absolute workspace path;
- latest user requirement;
- current status;
- exact next actions;
- retry time or reason for chosen schedule;
- validation gate;
- final delivery target;
- explicit instruction not to rush or claim completion before evidence exists.
- note that automation creation is not completion or execution evidence.

## Resume Rules

When a session wakes from automation:

1. Read the handoff or automation prompt fully.
2. Check for newer user messages. Newer user instructions override old handoff instructions.
3. Inspect git status before editing.
4. Continue only the scoped pending work.
5. If quota is still unavailable, update the handoff and reschedule.

When the user reports that an automation did not run:

1. Inspect the saved automation configuration or status when available.
2. State whether the automation exists, is active, has execution evidence, or appears missed.
3. Continue the pending work immediately if the current session has capacity.
4. If work still cannot continue, create a replacement automation and keep a paste-ready fallback prompt.

## Quality Gates

- Handoff contains no vague "continue later" without exact next action.
- Handoff separates completed evidence from pending work.
- Handoff lists validation that still gates delivery.
- Automation is created when available, or a clear fallback prompt is provided.
- Scheduled automation is not treated as completed execution evidence.
- Final delivery includes realistic scenario validation evidence.
