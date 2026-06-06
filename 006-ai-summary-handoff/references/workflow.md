# AI Summary Handoff Workflow

## Goal

Turn a long or messy conversation into a concise handoff that another AI session can execute without rediscovering everything. The output must preserve decisions, current state, blockers, verification evidence, and next actions.

## Information To Collect

- Original goal, current state, completed work, changed files, and decisions.
- Known blockers, failed attempts, logs, credentials boundaries, and safety constraints.
- Next session role, expected output, and validation requirements.

## Standard Procedure

1. Separate facts, assumptions, unresolved questions, and user preferences.
2. Capture completed work and exact files, commands, links, or artifacts that matter.
3. Capture failed attempts and why they failed, without burying them in prose.
4. Write the handoff as an actionable prompt for the next session.
5. Include validation duties and evidence requirements for any deliverable.
6. Keep secrets out; mention that credentials must be obtained from the user or environment.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Produce a copy-ready handoff prompt plus a short checklist of known gaps, validation requirements, and risks.

Use explicit sections when possible: Handoff Prompt, Known Facts, Assumptions, Next Task, Validation Duties, Do Not Do, Remaining Risks. The next session should be able to paste the prompt and start work without rereading the original conversation.
