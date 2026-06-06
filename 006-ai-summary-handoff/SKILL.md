---
name: ai-summary-handoff
description: 'Use when compressing a long conversation or unfinished task into a structured, safe, executable handoff prompt for another AI or another Codex session.'
---

# AI Summary Handoff

## Overview

Turn a long or messy conversation into a concise handoff that another AI session can execute without rediscovering everything. The output must preserve decisions, current state, blockers, verification evidence, and next actions.

## Use This Skill When

- User asks for a summary to continue in another AI or Codex window.
- Context is long and needs compression without losing execution state.
- A task is partially complete and needs a precise continuation prompt.

## Required Inputs

- Original goal, current state, completed work, changed files, and decisions.
- Known blockers, failed attempts, logs, credentials boundaries, and safety constraints.
- Next session role, expected output, and validation requirements.

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
