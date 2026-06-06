---
name: learning-summary-lite
description: 'Use when summarizing specified learning material into a concise, understandable, learner-appropriate version after clarifying scope, audience level, focus, and output style.'
---

# 学习内容精简总结

## Overview

用于把指定学习材料总结成够用、易懂、可吸收的版本。重点是先确认范围和读者水平，再提炼结构、核心观点、例子和易混点。

## Trigger

- 用户提供文章、章节、课程、笔记或长文本，希望精简总结。
- 用户指定某个主题或部分，需要面向学习而不是做摘要归档。
- 用户希望通俗、少术语、带例子或便于记忆。

## Required Inputs

- 原文或材料位置、总结范围。
- 用户水平、重点关注点、输出长度和风格。
- 是否需要例子、对比表、知识地图、复习问题。

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
