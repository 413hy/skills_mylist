# Codex Control Multi-Session Workflow

## Goal

Use the current Codex window as `session_0`, a requirements and control session. It clarifies the user's real need, reads project context when useful, maintains a state anchor, and routes confirmed work into numbered worker sessions through project task files. The control session does not implement product work; each worker session owns implementation, agents, skills, delivery documents, and evidence.

## Information To Collect

- Overall goal, current state, constraints, repositories, systems, and priority.
- Which sessions exist or should be created.
- Expected outputs, validation evidence, and state anchor format.
- Whether the requirement is clear enough to split. If not clear, collect only the next missing facts.
- Project areas, likely ownership boundaries, reusable workflows, and existing skills that worker sessions may need.

## Standard Procedure

1. Declare that this window is `session_0` and will act as the requirements/control window.
2. Inspect user-provided material and relevant project files when that helps clarify an unclear request.
3. If the requirement is unclear, ask focused clarification questions and stop. Do not create implementation session prompts yet.
4. Once the requirement is clear, write a requirement mirror covering goal, users, workflows, constraints, non-goals, risks, and success criteria.
5. Decide whether multiple sessions are justified. Split only when it reduces context load, ownership conflict, or validation complexity.
6. Define session roles, ownership boundaries, inputs, outputs, forbidden overlap, dependencies, and expected delivery document paths.
7. Write one task file per worker session at `docs/codex-sessions/tasks/session_n-task.md`; use `references/session-task-template.md` as the structure.
8. Give the user short launch instructions, not long pasted prompts, when task files are available.
9. Generate paste-ready prompts for `session_1`, `session_2`, etc. only when file writing is unavailable or the user explicitly asks for copy-paste prompts. Paste-ready prompts must be contract-complete task files in prompt form, not condensed summaries.
10. Require each worker session to perform an `Agent Capability Check` and `Agent Need Assessment` before any substantive work, decide which agents to create, which skills to call, whether a project-local child skill is justified, and how it will avoid overlap with other sessions.
11. Require each worker session to write or update `docs/codex-sessions/session_n-delivery.md`.
12. Maintain `docs/codex-sessions/session_0-state.md` or provide a pasteable state anchor when file writing is not appropriate.
13. Reconcile returned delivery documents and evidence before declaring the overall work complete.

## Default Paths

- `session_0` state: `docs/codex-sessions/session_0-state.md`
- Worker task directory: `docs/codex-sessions/tasks/`
- Worker task file: `docs/codex-sessions/tasks/session_n-task.md`
- Worker delivery document: `docs/codex-sessions/session_n-delivery.md`
- Optional integration checklist: `docs/codex-sessions/integration-checklist.md`
- Optional project-local child skills: `.codex/project-skills/<skill-name>/SKILL.md`

## Worker Task File Requirements

Every `docs/codex-sessions/tasks/session_n-task.md` file and every paste-ready `session_n` prompt must include:

- Role and ownership boundary.
- Inputs and files or modules to inspect.
- Prohibited overlap with other sessions.
- Required delivery document path: `docs/codex-sessions/session_n-delivery.md`.
- Agent Capability Check: before research, planning, drafting, implementation, or validation, the worker must state whether agent/subagent creation is available in that session.
- Agent Need Assessment: before substantive work, the worker must explicitly decide which agents are needed. If agent creation is available and the task is complex, cross-file, multi-workflow, risky, validation-heavy, or benefits from an independent review perspective, the worker must create at least one narrowly scoped agent before substantive work.
- Agent fallback: if agent creation is unavailable, the worker must write `Agent creation unavailable` and compensate with explicit manual review steps. Small file count alone is not enough reason to skip agents when validation or integration risk exists.
- Agent policy: give each agent clear ownership; tell agents they are not alone in the codebase and must not revert others' work.
- Skill policy: call existing skills when appropriate; create project-local child skills only for reusable project-specific workflows and document them.
- Test ownership policy: each worker should prefer scoped tests for its own module. Shared smoke, end-to-end, integration, or checklist files should be owned by the integration session unless explicitly assigned otherwise. If a worker must touch a shared test, it must document why and what coordination is needed.
- Validation policy: use realistic daily-use scenario tests, not API or command smoke tests alone.
- Return format: Agent Capability Check, Agent Need Assessment, agents used or `Agent creation unavailable`, changed files, decisions, skills called, child skills created, tests, evidence, blockers, risks, and next handoff needs.
- Delivery path format: the worker's final answer or delivery file must include a top-level `## Delivery Document Path` section with the exact path in backticks. A path in the title alone is not enough.
- Return section format: the worker's final answer or delivery file must end with a top-level `## Return To session_0` section that states the path and completion status.
- Startup instruction: the worker session must read this task file, confirm its role, and then execute only its assigned scope.

## Paste-Ready Prompt Requirements

When `session_0` cannot write task files, each paste-ready prompt must include this block, adapted with the correct session number and delivery path:

```text
Worker Contract:
1. Treat this prompt as your session task file.
2. Start with Agent Capability Check before research, planning, drafting, implementation, or validation.
3. Then perform Agent Need Assessment. If agents/subagents are available and this task is complex, risky, validation-heavy, multi-workflow, or benefits from independent review, create 1-3 narrowly scoped agents before substantive work. If not, explain why and how you will compensate.
4. Call relevant skills before working.
5. Do only the assigned scope and respect other sessions' ownership.
6. Write or update docs/codex-sessions/session_n-delivery.md. If writing files is not allowed, output the exact equivalent Markdown in the response and state the intended path.
7. The delivery must include Agent Capability Check, Agent Need Assessment, agents used or why not, skills called, changed files or no-file statement, decisions, validation evidence, blockers, risks, and next handoff needs.
8. The first screen of the final answer must include a `## Delivery Document Path` section with the exact path in backticks. The final answer must end with `## Return To session_0`.
```

If a generated worker prompt does not include this block or equivalent requirements, it is incomplete and must be corrected before the user launches that session.

## Worker Delivery Acceptance Gate

When a worker reports back, `session_0` must reject the delivery and ask for a corrected handoff if any required section is missing. Required sections:

- `## Delivery Document Path`
- `## Agent Capability Check`
- `## Agent Need Assessment`
- `## Agents Used` or `## Agent Fallback`
- `## Skills Called`
- `## Changed Files` or `## No File Changes`
- `## Validation Evidence`
- `## Blockers`
- `## Risks`
- `## Next Handoff Needs`
- `## Return To session_0`

Do not treat a filename in the heading, a prose mention of the path, or an implicit final summary as satisfying these sections. The point is to make worker output easy for `session_0` and the user to audit without rereading the whole answer.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Keep `session_0` out of implementation unless the user explicitly changes its role.
- Do not split sessions before the requirement is clear enough to assign ownership.
- Use numbered session names exactly: `session_1`, `session_2`, etc.
- Prefer task files over long pasted prompts.
- Treat paste-ready prompts as task files in prompt form; do not omit delivery paths, agent policy, skill policy, validation duties, or return format.
- Include delivery document paths in every worker task file.
- Include explicit Agent Capability Check, Agent Need Assessment, agent delegation rules, and skill delegation rules in every worker task file and paste-ready prompt.
- Include the delivery acceptance gate in every worker task file and paste-ready prompt, especially when file writing is disabled.
- Assign ownership for shared smoke, end-to-end, integration, and checklist files; default them to the integration session.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

If requirements are unclear, provide `session_0` status, what was inspected, what is unclear, and the next focused questions only.

If requirements are clear, provide requirement mirror, session split rationale, ownership map, created task file paths, one-line launch instructions for each `session_n`, delivery document paths, agent and skill policies, validation duties, state anchor, and integration checklist.
