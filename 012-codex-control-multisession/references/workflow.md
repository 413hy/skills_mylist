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
9. Generate paste-ready prompts for `session_1`, `session_2`, etc. only when file writing is unavailable or the user explicitly asks for copy-paste prompts.
10. Require each worker session to perform an `Agent Capability Check` and `Agent Need Assessment`, decide which agents to create, which skills to call, whether a project-local child skill is justified, and how it will avoid overlap with other sessions.
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

Every `docs/codex-sessions/tasks/session_n-task.md` file must include:

- Role and ownership boundary.
- Inputs and files or modules to inspect.
- Prohibited overlap with other sessions.
- Required delivery document path: `docs/codex-sessions/session_n-delivery.md`.
- Agent Capability Check: before implementation, the worker must state whether agent/subagent creation is available in that session.
- Agent Need Assessment: before implementation, the worker must explicitly decide which agents are needed. If agent creation is available and the task is complex, cross-file, multi-workflow, risky, or validation-heavy, the worker must create at least one narrowly scoped agent before implementing.
- Agent fallback: if agent creation is unavailable, the worker must write `Agent creation unavailable` and compensate with explicit manual review steps. Small file count alone is not enough reason to skip agents when validation or integration risk exists.
- Agent policy: give each agent clear ownership; tell agents they are not alone in the codebase and must not revert others' work.
- Skill policy: call existing skills when appropriate; create project-local child skills only for reusable project-specific workflows and document them.
- Validation policy: use realistic daily-use scenario tests, not API or command smoke tests alone.
- Return format: Agent Capability Check, Agent Need Assessment, agents used or `Agent creation unavailable`, changed files, decisions, skills called, child skills created, tests, evidence, blockers, risks, and next handoff needs.
- Startup instruction: the worker session must read this task file, confirm its role, and then execute only its assigned scope.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Keep `session_0` out of implementation unless the user explicitly changes its role.
- Do not split sessions before the requirement is clear enough to assign ownership.
- Use numbered session names exactly: `session_1`, `session_2`, etc.
- Prefer task files over long pasted prompts.
- Include delivery document paths in every worker task file.
- Include explicit Agent Capability Check, Agent Need Assessment, agent delegation rules, and skill delegation rules in every worker task file.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

If requirements are unclear, provide `session_0` status, what was inspected, what is unclear, and the next focused questions only.

If requirements are clear, provide requirement mirror, session split rationale, ownership map, created task file paths, one-line launch instructions for each `session_n`, delivery document paths, agent and skill policies, validation duties, state anchor, and integration checklist.
