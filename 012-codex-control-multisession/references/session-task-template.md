# Session Task File Template

Use this structure when `session_0` writes `docs/codex-sessions/tasks/session_n-task.md`.

```md
# session_n Task

## Startup Instruction

You are `session_n`. Read this file first, confirm your role, and execute only the scope assigned here. Do not rely on hidden context from `session_0`.

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

- Before implementation, write an `Agent Need Assessment` in your working notes and delivery document.
- If this task is complex, cross-file, multi-workflow, risky, or validation-heavy, default to creating at least one narrowly scoped agent unless you explicitly justify why agents are unnecessary.
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

## Delivery Document

Write or update:

`docs/codex-sessions/session_n-delivery.md`

The delivery document must include Agent Need Assessment, agents used or why no agents were used, changed files, decisions, skills called, child skills created, tests, realistic scenario evidence, blockers, risks, and next handoff needs.

## Return To session_0

Tell `session_0` the delivery document path and summarize whether the session is complete, blocked, or needs integration help.
```
