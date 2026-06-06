---
name: pr-check-commit-pr
description: 'Use when preparing code changes for review: inspect the workspace, verify behavior with realistic scenario tests, commit intentionally, push the branch, and open or prepare a pull request.'
---

# Pre-PR Check, Commit, and Pull Request

## Overview

Close out code changes before review. The skill is not just for running git commit; it verifies the changed behavior through realistic user workflows, keeps the commit scope clean, and prepares a reviewable pull request.

## Use This Skill When

- User asks to check changes and commit them.
- User asks to push code or create a PR.
- A code change needs final verification before review.

## Required Inputs

- Current branch, target branch, related issue or requirement.
- Changed behavior, user-visible workflows, and files that must stay out of scope.
- Test commands, dev server commands, test accounts, sample data, and required credentials.

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
