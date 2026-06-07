---
name: step-by-step-guide
description: 'Use when the user wants one-step-at-a-time guidance, with each reply containing only the next executable step and the exact feedback needed before continuing.'
---

# Step-By-Step Guide

## Overview

Guide the user through a task one action at a time. This skill intentionally avoids dumping the full procedure when the next step depends on user feedback, logs, screenshots, or local observations.

## Use This Skill When

- User asks for step-by-step help.
- The task depends on local output or screenshots after each action.
- The user is learning or debugging and needs controlled pacing.

## Required Inputs

- Final goal and current state.
- User environment, tools, permissions, and comfort level.
- What feedback the user can provide: output, screenshot, log, or observation.

## Required Workflow

1. Start with context discovery. Read relevant files, docs, tickets, workspace state, or user-provided material before acting.
2. Produce a short requirement mirror when ambiguity, risk, or implementation impact exists.
3. Follow `references/operating-contract.md` for hard rules, failure handling, and evidence standards.
4. Follow `references/workflow.md` for the task-specific procedure.
5. If the work creates or changes a product, feature, script, demo, agent, synchronization result, pull request, or other final deliverable, apply `references/scenario-validation.md` before delivery.
6. Treat `references/original-prompt.md` only as migration history. The current SKILL.md and references take priority.

## Step Response Rules

- Start every reply with an explicit step label, such as `Step 1` or `第 1 步`, matching the user's language when obvious.
- Give exactly one executable action for the current turn.
- Ask for exactly one feedback item or output to be sent back.
- If the user already named the needed command or target and the context is sufficient, use that direct next action instead of adding a prerequisite confirmation step.
- For browser login/debugging issues, prefer the simplest observable first, such as the visible error message; move to DevTools or Network only after that feedback if needed.

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
