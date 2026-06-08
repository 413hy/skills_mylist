---
name: requirements-to-dev-doc
description: 'Use when clarifying a vague product, engineering, automation, agent, or workflow request through dialogue and turning the confirmed need into a development requirements document that can be handed to codex-control-multisession, session_0, or another implementation-planning window. Trigger when the user wants help articulating requirements, avoiding context bloat, preparing a dev doc, or creating a handoff document before implementation.'
---

# Requirements To Dev Doc

## Overview

Clarify the user's real need and compress the conversation into a durable development requirements document. This skill is upstream of `$codex-control-multisession`: it produces the source document that a later `session_0` can read, inspect, split, and route.

## Position

- Treat the current window as a requirements clarification window, not an implementation or multi-session control window.
- Read user-provided notes, project files, docs, tickets, architecture, and tests when they help clarify the requirement.
- Do not implement product code, create worker sessions, or write `docs/codex-sessions/tasks/session_n-task.md` unless the user explicitly changes this window's role.
- Prefer a standalone document over preserving chat history. The document must be usable by another Codex window without hidden context.
- If the user wants the next step to be 012, include a concise launch prompt for `$codex-control-multisession`.

## Required Inputs

- User goal, target repo or product area, current state, constraints, and priority.
- Project mode: existing codebase, greenfield/no code yet, unknown, or mixed.
- Target users, business or operational workflow, must-have outcomes, and success criteria.
- Known source materials, screenshots, docs, tickets, conversations, or files to inspect.
- Expected handoff target: 012/session_0, direct implementer, product owner, QA, or another workflow.

## Required Workflow

1. Start with context discovery. Read relevant user-provided material and local project files when needed.
2. Maintain a working split of facts, assumptions, open questions, contradictions, and decisions.
3. If missing information could change implementation scope, ask only the next one to three highest-impact clarification questions. Prefer one question when the answer is likely to be long.
4. Mirror the requirement after each meaningful clarification round: goal, users, workflows, scope, non-goals, constraints, success criteria, and open questions.
5. When the requirement is ready, write a development requirements document. Use `references/dev-doc-template.md` for structure.
6. If writing to a project is appropriate, default to `docs/requirements/{date}-{short-slug}-dev-requirements.md`. If not, render the document in the conversation.
7. Validate the document using `references/scenario-validation.md` before delivery.
8. If the output is for 012, include a launch prompt that tells 012 to read the document as the source of truth and continue as `session_0`.

## Readiness Gate

Write the final document only when it can answer enough of the following for a downstream planner:

- What problem or opportunity is being addressed.
- Who the users or operators are.
- What workflows must work, including normal, error, and boundary flows.
- What is explicitly in scope and out of scope.
- What current project context, files, systems, or constraints matter.
- Whether the work is for an existing codebase, a greenfield project, or an unknown target.
- Whether source materials conflict and which conflict must be resolved before planning.
- What acceptance criteria and realistic validation scenarios should prove completion.
- What assumptions remain and which questions are still open.
- Whether 012 should continue clarifying or can split worker sessions.

If the user asks to proceed despite gaps, write the document with a visible `Open Questions` section and mark the handoff status as `Needs clarification`.

## Output Contract

- If requirements are unclear, provide the current requirement mirror and focused questions only.
- If requirements are ready, provide the development requirements document path or full markdown, plus the 012 launch prompt when relevant.
- Include facts, assumptions, non-goals, acceptance criteria, validation scenarios, risks, open questions, and decision log.
- Include project mode and known contradictions when relevant.
- Keep the document independent of the chat transcript. Avoid phrases like "as discussed above" unless the referenced decision is restated.
- Do not hide unresolved ambiguity inside acceptance criteria.

## References

- `references/operating-contract.md` for hard rules, failure handling, and evidence standards.
- `references/workflow.md` for the detailed clarification and document creation workflow.
- `references/dev-doc-template.md` for the standalone development requirements document structure.
- `references/scenario-validation.md` for document handoff validation.
- `references/original-prompt.md` for the source user intent that motivated this skill.
