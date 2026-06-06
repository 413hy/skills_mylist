---
name: step-by-step-guide
description: 'Use when the user wants one-step-at-a-time guidance, with each reply containing only the next executable step and the exact feedback needed before continuing.'
---

# 一步一步指导模式

## Overview

用于把复杂任务变成一轮一个可执行动作。这个 skill 不追求一次性讲完，而是降低用户操作负担，通过反馈驱动下一步。

## Trigger

- 用户要求一步一步指导。
- 任务依赖用户本地操作、截图、日志或环境反馈。
- 用户是学习或排错场景，不适合一次给完整方案。

## Required Inputs

- 最终目标和当前状态。
- 用户能操作的环境、工具和权限。
- 每一步执行后能提供的反馈类型：截图、日志、命令输出、观察结果。

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
