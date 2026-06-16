# Session Task File Template

Use this structure when `session_0` writes `docs/codex-sessions/tasks/session_n-task.md`.

When file writing is unavailable or the user asks for copy-paste launch prompts, use the same structure as a paste-ready prompt. Do not shorten it into a role summary; the prompt must preserve the startup instruction, agent policy, skill policy, delivery document path, validation duties, and return format.

```md
# session_n Task

## Startup Instruction

You are `session_n`. Read this file or prompt first, confirm your role, and execute only the scope assigned here. Do not rely on hidden context from `session_0`.

## Worker Contract

1. Treat this file or prompt as your session task file.
2. Start with Agent Capability Check before research, planning, drafting, implementation, or validation.
3. Then perform Agent Need Assessment. If agents/subagents are available and this task is complex, risky, validation-heavy, multi-workflow, or benefits from independent review, create 1-3 narrowly scoped agents before substantive work. If not, explain why and how you will compensate.
4. Call relevant skills before working.
5. Do only the assigned scope and respect other sessions' ownership.
6. Write or update `docs/codex-sessions/session_n-delivery.md`. If writing files is not allowed, output the exact equivalent Markdown in the response and state the intended path.
7. The delivery must include Agent Capability Check, Agent Need Assessment, agents used or why not, skills called, changed files or no-file statement, decisions, validation evidence, blockers, risks, and next handoff needs.
8. The first screen of your final answer must include `## Delivery Document Path` with the exact path in backticks. A filename in the title is not enough.
9. Your final answer must end with `## Return To session_0`, stating the delivery path and whether you are complete, blocked, or need integration help.

## Role

State the session role and its ownership boundary.

## Goal

State the user-facing goal this session contributes to.

## Inputs To Read

- Project files, docs, tickets, state anchors, and delivery docs to inspect.
- Required upstream session documents.

## Ownership

### In Scope

- Explicit files, modules, features, docs, or workflows owned by this session.

### Out Of Scope

- Files, modules, features, docs, or workflows owned by other sessions.
- Any implementation that should wait for another session.

## Dependencies And Assumptions

- Upstream dependencies.
- Assumptions that must be verified.
- What to do if dependencies are missing.

## Agent Policy

- Before research, planning, drafting, implementation, or validation, write an `Agent Capability Check` in your working notes and delivery document: state whether this session has a tool or mechanism to create agents/subagents.
- Then write an `Agent Need Assessment`: identify which parts of the task benefit from independent agents.
- If agent/subagent creation is available and this task is complex, cross-file, multi-workflow, risky, validation-heavy, or benefits from independent review, create at least one narrowly scoped agent before substantive work.
- If agent creation is unavailable, write `Agent creation unavailable` in the delivery document and compensate with explicit manual review steps.
- Do not treat small file count alone as enough reason to skip agents when validation or integration risk exists.
- Consider agents for independent codebase exploration, test/validation planning, UI review, API/data model inspection, or risk review.
- Give each agent narrow ownership.
- Tell agents they are not alone in the codebase, must not revert others' work, and must adapt to parallel changes.
- Do not let multiple agents edit the same files concurrently.

## Skill Policy

- Call existing skills when the task matches their trigger.
- Create project-local child skills only for reusable project-specific workflows.
- Store child skills at `.codex/project-skills/<skill-name>/SKILL.md`.
- Document any child skill path, trigger, owner, and validation evidence.

## Required Work

List concrete tasks this session must complete.

## Validation Duties

Use realistic daily-use scenario tests. API, function, build, or command checks are supporting evidence only.

List normal, error, and boundary scenarios with sample data or accounts.

Prefer scoped tests owned by this session's module. Shared smoke, end-to-end, integration, or checklist files belong to the integration session unless this task explicitly assigns them to you. If you must touch a shared test or checklist, document why and what coordination is needed.

## Delivery Document

Write or update:

`docs/codex-sessions/session_n-delivery.md`

If this session is running from a paste-ready prompt and file writing is not allowed, do not write the file. Instead, output the exact equivalent Markdown in the response and clearly state that the intended path is `docs/codex-sessions/session_n-delivery.md`.

The delivery document must include Agent Capability Check, Agent Need Assessment, agents used or `Agent creation unavailable`, changed files, decisions, skills called, child skills created, tests, realistic scenario evidence, blockers, risks, and next handoff needs.

Use these top-level sections exactly:

```md
## Delivery Document Path

`docs/codex-sessions/session_n-delivery.md`

## Agent Capability Check

## Agent Need Assessment

## Agents Used

If no agents were used, replace this with `## Agent Fallback`.

## Skills Called

## Changed Files

If no files changed, use `## No File Changes`.

## Decisions

## Validation Evidence

## Blockers

## Risks

## Next Handoff Needs

## Return To session_0
```

## Return To session_0

Tell `session_0` the delivery document path and summarize whether the session is complete, blocked, or needs integration help. This must be a top-level section in the delivery, not only a final sentence.
```
