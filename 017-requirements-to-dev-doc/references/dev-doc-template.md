# Development Requirements Document Template

Use this structure when writing a standalone development requirements document. Keep sections concise but specific. Remove sections that do not apply only when they are truly irrelevant.

```md
# {Feature Or Project} Development Requirements

## Handoff Summary

- Handoff target: 012/session_0, direct implementer, QA, or other.
- Handoff status: Ready for session planning | Needs clarification | Draft with open questions.
- Project mode: Existing codebase | Greenfield/no code yet | Unknown | Mixed.
- Target repo or project path:
- Source materials inspected:
- What the next Codex window should do:

## 012 Launch Prompt

Use $codex-control-multisession as session_0. Read this document as the source of truth for the requirement. Inspect project context if needed, then either ask remaining clarification questions or create session task files under docs/codex-sessions/tasks/.

## Requirement Mirror

Summarize the user goal, target users, expected workflows, constraints, success criteria, and current open questions.

## Background And Problem

Explain the current pain point, opportunity, or reason for the work.

## Users And Jobs

- User or operator:
- Job to be done:
- Frequency or importance:

## Current State

Describe existing product behavior, relevant files, docs, tickets, architecture, data, or systems.

## Known Contradictions Or Conflicts

- Conflicting source:
- Why it matters:
- Decision needed before planning:

## Goals

- Goal 1:
- Goal 2:

## Non-Goals

- Explicitly excluded work:
- Deferred work:

## Scope

### In Scope

- Required workflow, feature, module, or document:

### Out Of Scope

- Work not owned by this requirement:

## User Workflows

### Normal Flow

1. User action:
2. System response:
3. Expected outcome:

### Error Or Edge Flows

- Error, permission, empty, invalid, retry, or boundary case:

## Functional Requirements

- Requirement:
- Rationale:
- Acceptance signal:

## Data, Permissions, And Integrations

- Data model or fields:
- Permission rules:
- External systems or APIs:
- Privacy or security constraints:

## UX Or Operational Requirements

- Interface, workflow, performance, accessibility, messaging, or operational expectations:

## Technical Constraints And Existing Patterns

- Existing code patterns:
- Compatibility or environment constraints:
- Dependencies:

## Acceptance Criteria

- Given/When/Then or equivalent criteria:
- Include normal, error, permission, data, and boundary cases where relevant.

## Scenario Validation Plan

- Scenario:
- Input data or account:
- Steps:
- Expected result:
- Evidence to collect:

## Suggested Workstream Split For 012

Non-binding draft. 012 should verify against project context before writing worker task files.

- session_1 candidate:
- session_2 candidate:
- integration candidate:

## Risks And Tradeoffs

- Risk:
- Mitigation or decision needed:

## Open Questions

- Question:
- Why it matters:
- Who can answer:

## Decision Log

- Decision:
- Source or rationale:
- Date:
```
