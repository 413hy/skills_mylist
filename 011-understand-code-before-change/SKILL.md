---
name: understand-code-before-change
description: 'Use before implementing a code change in an existing codebase: inspect architecture and data flow first, make scoped edits, then validate with realistic user-facing scenarios.'
---

# 先理解代码后完成需求

## Overview

用于已有代码库中的需求实现。重点是先理解结构、调用链、数据流和测试方式，再改代码；交付前必须用真实功能场景验证。

## Trigger

- 用户要求修改已有代码、修 bug、加功能。
- 代码结构不熟，不适合直接开改。
- 需求涉及用户可见流程、数据状态或跨模块行为。

## Required Inputs

- 需求描述、相关文件/模块、预期行为。
- 运行方式、测试命令、测试数据、账号和环境变量。
- 禁止改动范围、兼容性要求和验收标准。

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
