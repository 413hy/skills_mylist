---
name: codex-control-multisession
description: 'Use when the current Codex window should become session_0, a requirements/control window that clarifies the user need, inspects project context, avoids direct implementation, maintains a state anchor, then routes confirmed work into numbered Codex sessions using project task files, delivery document paths, agent/skill delegation rules, and validation duties.'
---

# Codex Control Multi-Session

## Overview

Use the current window as `session_0`, a requirements and control window. `session_0` clarifies the user need, reads project context when useful, maintains state, splits confirmed work into numbered sessions, and writes project task files that the user can point new windows at. Worker sessions own implementation, agent orchestration, skill usage, delivery documents, and evidence.

## Use This Skill When

- User wants a main Codex window to coordinate other sessions.
- User wants a requirements window that understands the project before routing work.
- A task is too broad for one context and needs manual session splitting.
- The user wants `session_0`, `session_1`, etc. with explicit roles, task files, progress documents, agents, skills, and validation evidence.

## Required Inputs

- Overall goal, current state, constraints, repositories, systems, and priority.
- Which sessions exist or should be created.
- Expected outputs, validation evidence, and state anchor format.

## Session 0 Rules

- Treat the current window as `session_0`.
- `session_0` may read project files, docs, tickets, tests, and architecture to understand unclear requirements.
- `session_0` may use read-only analysis agents if that helps requirement understanding, but must not use implementation agents and must not directly edit product code for the requested feature.
- If the requirement is unclear, ask focused clarification questions and do not split worker sessions yet.
- After the requirement is clear, produce a requirement mirror and a draft session plan for the user to approve or adjust.
- After the session plan is approved or clearly implied by the user, write task files at `docs/codex-sessions/tasks/session_n-task.md`.
- Give the user a short launch instruction for each new window, for example: `Open session_1 and tell it: read docs/codex-sessions/tasks/session_1-task.md and execute it.`
- If file writing is not appropriate or unavailable, fall back to paste-ready prompts named `session_1`, `session_2`, etc. These prompts are not summaries; they must contain the same worker contract, delivery path, agent policy, skill policy, validation duties, and return format that the task file would contain.
- Maintain the control state at `docs/codex-sessions/session_0-state.md` when writing files is appropriate.

## Worker Session Rules

- Every worker session must start from its task file: `docs/codex-sessions/tasks/session_n-task.md`.
- Every worker session prompt must specify a delivery document path: `docs/codex-sessions/session_n-delivery.md`.
- If `session_0` gives a paste-ready prompt instead of a task file, the prompt must still tell the worker to treat it as its task file and execute the full worker contract.
- Each worker session must perform an `Agent Capability Check` and `Agent Need Assessment` before any substantive work, including research, planning, document drafting, implementation, or validation.
- If agent/subagent creation is available and the task is complex, cross-file, multi-workflow, risky, validation-heavy, or likely to benefit from an independent review perspective, the worker session must create at least one narrowly scoped agent before substantive work.
- If agent creation is unavailable, the worker session must state `Agent creation unavailable` in its delivery document and compensate with explicit manual review steps.
- Do not treat small file count alone as enough reason to skip agents when validation or integration risk is nontrivial.
- If agents are useful, the worker session must create narrowly scoped agents with explicit ownership and integration rules.
- Agents may call existing skills when their task matches a skill trigger.
- A worker session may create project-local child skills only when the workflow is reusable across sessions or agents. It must document the skill path, trigger, owner, and validation evidence in its delivery document.
- Worker sessions should prefer scoped tests owned by their module. Shared smoke, end-to-end, integration, or checklist files should be owned by the integration session unless the task file explicitly assigns otherwise.
- If a non-integration session must touch a shared test or checklist file, it must document the reason and coordinate the expected change in its delivery document.
- Worker sessions must report the `Agent Capability Check`, `Agent Need Assessment`, agents used or why agent creation was unavailable, changed files, decisions, skills called, child skills created, tests, realistic scenario evidence, blockers, and next handoff needs.

## Paste-Ready Prompt Contract

When task files cannot be written, every paste-ready `session_n` prompt must include this contract explicitly:

```text
Worker Contract:
1. Treat this prompt as your session task file.
2. Start with Agent Capability Check before research, planning, drafting, implementation, or validation.
3. Then perform Agent Need Assessment. If agents/subagents are available and this task is complex, risky, validation-heavy, multi-workflow, or benefits from independent review, create 1-3 narrowly scoped agents before substantive work. If not, explain why and how you will compensate.
4. Call relevant skills before working.
5. Do only the assigned scope and respect other sessions' ownership.
6. Write or update docs/codex-sessions/session_n-delivery.md. If writing files is not allowed, output the exact equivalent Markdown in the response and state the intended path.
7. The delivery must include Agent Capability Check, Agent Need Assessment, agents used or why not, skills called, changed files or no-file statement, decisions, validation evidence, blockers, risks, and next handoff needs.
```

Do not abbreviate this contract away when the user asks for copy-paste task packages. If a previous prompt omitted it, `session_0` must send a corrective follow-up before accepting that worker's delivery.

## Required Workflow

1. Start with context discovery. Read relevant files, docs, tickets, workspace state, or user-provided material before acting.
2. Produce a short requirement mirror when ambiguity, risk, or implementation impact exists.
3. Follow `references/operating-contract.md` for hard rules, failure handling, and evidence standards.
4. Follow `references/workflow.md` for the task-specific procedure.
5. If the work creates or changes a product, feature, script, demo, agent, synchronization result, pull request, or other final deliverable, apply `references/scenario-validation.md` before delivery.
6. Treat `references/original-prompt.md` only as migration history. The current SKILL.md and references take priority.

## Scenario Validation Gate

Before saying the work is done, validate each user-facing function or operational deliverable with a realistic operation. If a delivered system contains account login, use a real or reserved test account through the normal UI and verify successful login, failed login, session behavior, logout, and protected-route access. Do not replace this with a bare API smoke test.

For non-code deliverables, run a representative sample through the document, plan, or workflow. A User Story, handoff prompt, architecture plan, or learning summary is only complete after a small example proves the next person can act on it.

## Output Contract

- State whether the requirement is still being clarified or ready for session planning.
- When unclear, ask only the next focused clarification questions and do not assign implementation work.
- When clear, provide a requirement mirror, ownership map, created `session_n` task file paths, one-line launch instructions, delivery document paths, validation duties, integration checklist, and `session_0` state anchor.
- Prefer task files over long pasted prompts. Use paste-ready prompts only as a fallback when task files cannot be written, and make each paste-ready prompt contract-complete.
- Require every worker session to write or update `docs/codex-sessions/session_n-delivery.md`.
- Call out unresolved assumptions, blocked sessions, and evidence that `session_0` must inspect before declaring the overall work complete.

## References

- `references/operating-contract.md` for hard rules, failure handling, and evidence standards.
- `references/workflow.md` for the full task-specific procedure.
- `references/session-task-template.md` when writing `docs/codex-sessions/tasks/session_n-task.md` files.
- `references/scenario-validation.md` for realistic self-test requirements and examples.
- `references/original-prompt.md` for the legacy source prompt only.
