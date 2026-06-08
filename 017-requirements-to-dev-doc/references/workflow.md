# Requirements To Dev Doc Workflow

## Goal

Turn an unclear or long-running requirements conversation into a standalone development requirements document. The document should be suitable for 012/session_0 to read later, inspect against project context, and decide whether to continue clarifying or split work into sessions.

## Information To Collect

- Product or engineering goal and why it matters.
- Project mode: existing codebase, greenfield/no code yet, unknown, or mixed.
- Target users, operators, customers, or systems.
- Current state, target repo, existing files, docs, tickets, screenshots, and known constraints.
- Core workflows, edge cases, permissions, data states, integrations, and failure cases.
- In-scope work, out-of-scope work, deadlines, priorities, and tradeoffs.
- Acceptance criteria and realistic validation examples.
- Handoff target and expected next action.

## Standard Procedure

1. Read provided material and inspect relevant local context when available.
2. Build a compact requirement mirror with facts, assumptions, open questions, contradictions, and decisions.
3. Ask focused clarification questions only when a missing answer could change implementation scope, ownership, validation, or handoff.
4. Avoid broad questionnaires. Prefer the next highest-impact question or a short set of up to three questions.
5. Update the requirement mirror after the user's answer.
6. Decide whether the request is ready for a dev doc:
   - `Ready`: enough information exists for 012 or an implementer to plan.
   - `Needs clarification`: key workflow, scope, constraint, or success criteria is still missing.
   - `Draft with open questions`: the user asked to proceed even with gaps.
7. Write the final document using `references/dev-doc-template.md`.
8. If a target project is writable, write the document to `docs/requirements/{date}-{short-slug}-dev-requirements.md`; otherwise render the markdown in chat.
9. Add a 012 launch prompt when the user wants to hand the document to `codex-control-multisession`.
10. Validate the document with `references/scenario-validation.md` before delivery.

## Clarification Priorities

Ask about these first when unclear:

- Core user workflow and expected outcome.
- Target repo or product area.
- Required scope versus nice-to-have scope.
- Existing behavior or current pain point.
- Project mode and whether missing code is expected because the project is greenfield.
- Acceptance criteria and realistic scenario evidence.
- Constraints that affect implementation: security, privacy, permissions, integrations, data shape, deadlines, performance, compatibility, or UI expectations.

## 012 Handoff Rules

- Do not pre-create `docs/codex-sessions/tasks/session_n-task.md`; that is 012's job.
- You may include a suggested workstream split as a draft, but label it non-binding.
- Include enough context for 012 to decide whether it should ask more questions or generate worker task files.
- Include this launch prompt shape:

```text
Use $codex-control-multisession as session_0. Read {dev-doc-path-or-markdown} as the source of truth for the requirement. Inspect project context if needed, then either ask remaining clarification questions or create session task files under docs/codex-sessions/tasks/.
```

## Quality Gates

- The document is standalone and does not rely on hidden chat context.
- Facts, assumptions, open questions, decisions, and contradictions are separated.
- Existing-code and greenfield requirements are clearly distinguished.
- Contradictory source materials are listed in their own section when present.
- Scope and non-goals are explicit.
- Acceptance criteria cover normal, error, permission, data, and boundary cases where relevant.
- Validation scenarios describe realistic daily-use operations, not only unit tests or command checks.
- The handoff status clearly says whether 012 should continue clarifying or can plan sessions.

## Output Shape

If unclear: requirement mirror, inspected material, what is unclear, and focused questions.

If ready: document path or full markdown, handoff status, 012 launch prompt, validation evidence, and unresolved risks.
