---
name: socratic-concept-learning
description: 'Use when guiding a user to understand one or more concepts through Socratic questioning, progressive hints, examples, correction, and a final memory-friendly summary.'
---

# 苏格拉底式概念学习

## Overview

用于概念学习，不直接灌输长篇解释，而是通过全局框架、单点提问、用户回答、纠偏和总结，帮助用户自己想明白。

## Trigger

- 用户想理解一组概念、区别、原理或术语。
- 用户希望通过问答、引导、类比学习，而不是直接看长文。
- 用户容易混淆多个概念，需要逐步辨析。

## Required Inputs

- 概念集合、用户背景、学习目标。
- 优先困惑点、应用场景、输出偏好。
- 是否需要最后生成表格、口诀、例题或迁移练习。

## Required Workflow

1. Start with context discovery. Read the relevant files, docs, tickets, current workspace state, or user-provided material before acting.
2. Produce a short requirement mirror when the task has ambiguity, risk, or implementation impact.
3. Follow `references/operating-contract.md` for hard rules, interaction discipline, failure handling, and evidence standards.
4. Follow the detailed procedure in `references/workflow.md`.
5. If the work creates or changes a product, feature, script, demo, Agent, synchronization result, PR, or other final deliverable, apply the scenario validation gate in `references/scenario-validation.md` before delivery.
6. Preserve the original migrated prompt only as historical reference in `references/original-prompt.md`; current environment rules and the optimized workflow here take priority.

## Scenario Validation Gate

Before saying the work is done, validate each user-facing function with a realistic operation. For example, if a delivered system contains account login, use a real or reserved test account to log in through the normal UI, verify successful login, failed login, session behavior, logout, and protected-route access. Do not replace this with a bare API smoke test.

For non-code deliverables, run a representative sample through the document or workflow. A User Story, handoff prompt, architecture plan, or learning summary is only complete after a small example proves that the next person can act on it.

## Output Contract

- State what was produced or changed.
- List the scenario tests performed with inputs, expected results, actual results, and pass/fail status.
- Call out any functionality that could not be scenario-tested and why.
- Keep unrelated refactors, unrelated documentation, and unsupported assumptions out of scope.

## References

- `references/operating-contract.md` for hard rules, failure handling, and evidence standards.
- `references/workflow.md` for the full operating procedure.
- `references/scenario-validation.md` for realistic self-test requirements and examples.
- `references/original-prompt.md` for the source prompt migrated from the old collection.
