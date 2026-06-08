# Operating Contract

## Hard Rules

- Treat quota, context, and rate limits as pause-and-resume conditions, not reasons to lower standards.
- Do not claim a task is complete until the requested work, sync, and realistic validation are actually complete.
- Before pausing, preserve the latest user request, current workspace state, changed files, validation status, blockers, retry timing, and exact next actions.
- When available, create a thread heartbeat or automation to continue later. In Codex, use the `automation_update` tool rather than raw automation text.
- Treat a created automation as a scheduled follow-up, not as evidence that continuation executed. If it does not fire, inspect the automation record, explain the failure or uncertainty, and continue manually or reschedule.
- If automation is unavailable, provide a paste-ready continuation prompt and durable state.
- On resume, read the handoff first, then check for newer user messages and current git/workspace state before acting.
- For any final product, feature, script, demo, agent, sync result, pull request, operational document, handoff prompt, user story, or plan, run realistic scenario validation with a daily-use example. API, function, build, or command checks are supporting evidence only.
- Fix failed validation items and rerun the failed scenario before delivery. Do not present failed items as optional follow-up unless the user explicitly accepts the remaining risk.

## Evidence Standard

Record enough evidence for another Codex session to continue without hidden context:

- absolute workspace path;
- branch, remote, and relevant changed files;
- user-visible objective and delivery standard;
- completed steps and proof;
- pending steps and known blockers;
- failed command output summary and retry time when visible;
- realistic validation scenarios with expected and actual results;
- exact resume prompt.

## Failure Handling

- If a retry time is visible, schedule continuation after it with a small buffer.
- If no retry time is visible, choose a conservative short follow-up and state that the time is assumed.
- If automation creation fails, do not retry blindly. Save the handoff and tell the user what manual prompt to send later.
- If automation creation succeeds but later appears not to have run, do not claim the recovery worked. Check the saved automation status, update the handoff with the missed execution, and continue from the current thread when possible.
- If the workspace has unrelated user changes, do not revert them. Mark them as out of scope unless they block continuation.
- If validation cannot run because of quota, missing credentials, or unavailable systems, pause with a clear blocker instead of claiming completion.
