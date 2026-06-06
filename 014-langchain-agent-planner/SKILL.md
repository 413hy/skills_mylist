---
name: langchain-agent-planner
description: 'Use before designing or implementing a LangChain Agent: clarify task, tools, memory, inputs, outputs, failure handling, evaluation cases, and scenario validation.'
---

# LangChain Agent Planner

## Overview

Plan a LangChain Agent before building it. The skill decides whether an agent is justified, defines tools, memory, schemas, guardrails, failure handling, and evaluation scenarios.

## Use This Skill When

- User asks to create or design a LangChain Agent.
- A workflow may need tool use, retrieval, memory, or structured output.
- Agent behavior needs to be evaluated before implementation.

## Required Inputs

- Task goal, users, available tools, data sources, and constraints.
- Input/output schema, memory requirements, permissions, and failure behavior.
- Representative user queries and expected outcomes.

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

- State what was produced or changed.
- List scenario tests with inputs, expected results, actual results, evidence, and pass/fail status.
- Call out any functionality that could not be scenario-tested and why.
- Keep unrelated refactors, unrelated documentation, and unsupported assumptions out of scope.

## References

- `references/operating-contract.md` for hard rules, failure handling, and evidence standards.
- `references/workflow.md` for the full task-specific procedure.
- `references/scenario-validation.md` for realistic self-test requirements and examples.
- `references/original-prompt.md` for the legacy source prompt only.
