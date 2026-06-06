# Multi-Agent Architect Workflow

## Goal

Design a multi-agent system only when multiple agents are justified. The skill compares simpler alternatives, then defines roles, permissions, communication, orchestration, memory, evaluation, and realistic collaboration tests.

## Information To Collect

- Business goal, user workflows, candidate agent roles, tools, data, and permissions.
- Constraints on latency, cost, safety, ownership, and observability.
- Representative collaboration scenarios and failure cases.

## Standard Procedure

1. First decide whether a single agent or normal workflow is sufficient.
2. If multiple agents are justified, define each role, responsibilities, tools, permissions, and non-goals.
3. Define communication contracts, shared state, memory boundaries, orchestration, and escalation.
4. Identify conflict resolution, routing errors, duplicate work, and runaway-loop risks.
5. Create collaboration scenario tests before implementation.
6. Validate agent handoffs and final answer quality with realistic cases.

## Quality Gates

- Separate facts, assumptions, and open questions.
- Keep the implementation or document scope explicit.
- Prefer existing project patterns, field names, test data, and connector conventions.
- Apply `references/scenario-validation.md` whenever the output affects a real workflow or downstream user.
- Failed checks must be fixed and rerun; do not substitute command success for user workflow validation.

## Output Shape

Provide justification, role map, communication contracts, orchestration plan, memory policy, scenario tests, risks, and implementation roadmap.
