---
name: clarify-before-demo
description: 'Use when the user wants a complete runnable demo but requirements are still ambiguous; clarify one question at a time, confirm the business loop, then build and scenario-test the demo.'
---

# Clarify Before Building Demo

## Overview

Build complete demos only after the core business loop is clear. The skill prevents shallow demo fragments by clarifying ambiguity, confirming scope, then validating the finished demo through realistic user interactions.

## Use This Skill When

- User asks for a complete demo or prototype.
- The requested demo has ambiguous domain, users, workflow, data, or success criteria.
- A demo needs to be runnable and validated before delivery.

## Required Inputs

- Demo goal, target user, core business object, platform, and constraints.
- Must-have workflows, nice-to-have features, sample data, and visual expectations.
- Run command, environment, test accounts, and acceptance criteria.

## Required Workflow

1. Start with context discovery. Read relevant files, docs, tickets, workspace state, or user-provided material before acting.
2. Produce a short requirement mirror when ambiguity, risk, or implementation impact exists.
3. Follow `references/operating-contract.md` for hard rules, failure handling, and evidence standards.
4. Follow `references/workflow.md` for the task-specific procedure.
5. If the work creates or changes a product, feature, script, demo, agent, synchronization result, pull request, or other final deliverable, apply `references/scenario-validation.md` before delivery.
6. Treat `references/original-prompt.md` only as migration history. The current SKILL.md and references take priority.

## Clarification Rules

- Ask only the single highest-impact question when the demo is still ambiguous.
- For payment, authentication, data deletion, production integration, or other high-risk demos, explicitly label the risk and scope boundary before asking the question.
- Distinguish local/mock demo scope from sandbox or live-system scope before implementation.

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
