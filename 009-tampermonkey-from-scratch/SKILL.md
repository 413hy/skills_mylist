---
name: tampermonkey-from-scratch
description: 'Use when designing and implementing a Tampermonkey userscript from scratch, including page analysis, permissions, selectors, interaction behavior, persistence, and real browser validation.'
---

# Tampermonkey Script From Scratch

## Overview

Create a Tampermonkey userscript from real page behavior. The skill covers page analysis, match rules, permissions, selectors, injection timing, persistence, error handling, installation, and browser validation.

## Use This Skill When

- User asks for a Tampermonkey or userscript solution.
- A browser page needs automation, form filling, UI changes, scraping, or workflow shortcuts.
- A script must be installed and validated on a real or representative page.

## Required Inputs

- Target URL patterns, manual workflow, desired automation, and allowed permissions.
- Page HTML or access to the page, selectors, dynamic loading behavior, and login requirements.
- Persistence requirements, safety constraints, and validation steps.

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
