---
name: quota-resilient-handoff
description: 'Use when a Codex task may exceed token, context, quota, or rate-limit capacity; when Codex CLI or tool output shows quota/rate-limit/retry-after errors; when validation or delivery is incomplete near the end of a turn; or when the user wants Codex to avoid rushing and resume later through a durable handoff or automation. Creates continuation state, recovery prompts, and thread heartbeat/automation follow-ups when available.'
---

# Quota-Resilient Handoff

## Overview

Protect long-running work from rushed completion. When budget, context, or quota risk appears, preserve the latest user requirement, unfinished work, validation duties, and exact next steps, then create an automation-backed continuation when the platform supports it.

The goal is not to bypass limits. The goal is to stop lowering quality standards because limits are near.

## Required Inputs

- Latest user request, including any corrections after the original task.
- Current workspace path, branch, remote, and files that are in scope or out of scope.
- Completed work, pending work, validation evidence, and failed or blocked commands.
- Any visible quota, rate-limit, retry-after, or context-risk signal.
- Expected delivery standard, especially realistic daily-use validation before final delivery.

## Risk Signals

Invoke this skill immediately when any of these appear:

- A tool, Codex CLI run, API call, or log reports quota, rate limit, usage limit, retry-after, or "try again later".
- A long validation suite or implementation task remains unfinished and the current context or turn is likely insufficient.
- The agent is tempted to summarize as "done" even though tests, realistic scenario validation, installation sync, commit, push, or user-requested evidence is missing.
- The user explicitly says not to worry about token use, not to rush, to continue after quota refresh, or to use automation for continuation.
- A previous resume prompt or automation message asks the agent to continue from a handoff.

## Hard Rules

- Never claim a task is complete unless the requested implementation, sync, and realistic validation are complete.
- Do not downgrade validation to API, build, command, or interface smoke checks because quota is low.
- Treat quota exhaustion as a pause condition, not a reason to shrink scope silently.
- Preserve the newest user instruction before writing any handoff. If newer user instructions conflict with the old handoff, the newest instruction wins.
- Prefer durable state over memory. For repo work, write a handoff file when file writes are appropriate.
- Prefer thread heartbeat/automation over asking the user to remember to resume, when the platform provides an automation tool.
- Treat automation creation as scheduling evidence only, not execution evidence. If the user reports that an automation did not run, inspect the automation configuration and continue the task manually or reschedule; do not argue that creation means recovery succeeded.
- Do not fake automation IDs, schedules, completed validation, commits, pushes, or external sync.

## Standard Workflow

1. State the current objective, latest user requirement, delivery criteria, and out-of-scope items.
2. Inspect local state needed for continuity: workspace path, branch, changed files, recent logs, validation status, and any retry time.
3. Decide whether work can finish to the required standard now. If not, switch to pause-and-resume mode.
4. Build a recovery package with:
   - latest user requirement;
   - current workspace, branch, remote, and relevant paths;
   - completed work with evidence;
   - unfinished work and blockers;
   - failed commands, quota messages, and retry time if visible;
   - exact next commands or scenarios to run;
   - realistic validation duties that still gate delivery;
   - files or directories that must not be touched;
   - final delivery steps such as install, hash compare, commit, push, or PR.
5. If automation or heartbeat tools are available, create or update a continuation attached to the current thread. Schedule it at the visible retry time plus a small buffer when known; otherwise use a conservative near-future follow-up.
6. If automation tools are unavailable or fail, present a paste-ready continuation prompt and the handoff file path.
7. After creating automation, record its ID or name and the exact prompt summary. Do not treat it as proof that the work resumed.
8. On resume, read the handoff first, then check for newer user messages, current git state, automation status if relevant, and changed files before continuing.
9. Complete the original task only after the remaining implementation, sync, and realistic daily-use validation pass.

## Automation Guidance

Use the current platform's automation, reminder, or heartbeat tool when available. In Codex, use the `automation_update` tool rather than writing raw automation directives by hand.

Prefer a heartbeat attached to the current thread for continuation work. The automation prompt must be self-contained and include:

- absolute workspace path;
- latest user requirement;
- current completion status;
- precise next actions;
- validation scenarios to run;
- expected final delivery;
- explicit "do not claim done until validation passes" language.

If a retry time is present in logs, schedule the automation after that time. If no retry time is available, choose a short practical delay and explain the assumption in the handoff.

If the automation did not run, inspect the saved automation record when available. Report whether it was active, paused, missing, mis-scheduled, or lacked execution evidence. Then continue the task in the current thread or create a replacement automation with a clearer schedule and prompt.

## Handoff File

For repository work, write the handoff under:

`docs/codex-handoffs/YYYY-MM-DD-<short-slug>.md`

If that path would pollute a repository or the task is not repo-based, keep the handoff in the final response or another user-approved location.

The handoff must include these sections:

- `Latest User Requirement`
- `Current Status`
- `Completed Evidence`
- `Pending Work`
- `Blocked Or Failed Commands`
- `Next Actions`
- `Realistic Validation Gate`
- `Do Not Touch`
- `Resume Prompt`

## Output Contract

When pausing, report:

- whether an automation was created or why it was not;
- where the handoff is stored;
- what is complete and what is not complete;
- the exact next validation or delivery step.

When resuming, report:

- which handoff was read;
- whether any newer user instruction changed the task;
- whether an earlier automation actually executed or only existed as a saved schedule;
- what work will continue next.

When completing, include realistic validation evidence. If any validation could not be run, say why and do not present the task as fully complete.

## References

- `references/operating-contract.md` for hard rules and evidence standards.
- `references/workflow.md` for the detailed pause/resume procedure.
- `references/scenario-validation.md` for realistic validation examples.
- `references/original-prompt.md` for the source user intent that motivated this skill.
