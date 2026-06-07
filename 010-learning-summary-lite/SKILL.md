---
name: learning-summary-lite
description: 'Use when summarizing specified learning material into a concise, understandable, learner-appropriate version after clarifying scope, audience level, focus, and output style.'
---

# Concise Learning Summary

## Overview

Summarize learning material into a compact version that is easier to understand and retain. The skill prioritizes structure, plain language, key terms, examples, misconceptions, and a quick self-check.

## Use This Skill When

- User provides learning material and asks for a concise summary.
- User wants simpler wording, key points, or study notes.
- A topic needs to be made understandable for a specific level.

## Required Inputs

- Source material, target learner level, desired length, and focus.
- Must-keep sections, parts to skip, and preferred style.
- Whether examples, analogies, questions, or exam notes are needed.

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

## Summary Response Rules

- Always include a clearly labeled self-check section, such as `Self-check`, `自检问题`, or `检查问题`.
- The self-check must use the summarized concept in a small realistic example, not only ask the user to repeat definitions.
- Keep the summary concise, but do not omit common traps when the topic has frequent misconceptions.

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
