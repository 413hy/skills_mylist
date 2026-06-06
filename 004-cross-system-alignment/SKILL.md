---
name: cross-system-alignment
description: 'Use when comparing implementation, requirements, task tracker state, documentation, and external system records to find inconsistencies and produce a correction plan.'
---

# 跨系统一致性对齐

## Overview

用于检查多个系统之间是否说的是同一件事：代码实现、需求文档、任务系统、设计稿、测试结果和外部同步系统。重点是找出差异、判断影响、给出修正顺序。

## Trigger

- 用户怀疑代码、需求、任务系统或外部系统不一致。
- 交付前需要确认实现是否覆盖需求和验收标准。
- 多个文档或系统里状态冲突，需要你做对齐。

## Required Inputs

- 需要对齐的系统/文档/代码位置。
- 权威来源优先级，例如需求文档优先还是线上行为优先。
- 对齐范围、验收标准和不应修改的系统。

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
