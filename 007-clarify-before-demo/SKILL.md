---
name: clarify-before-demo
description: 'Use when the user wants a complete runnable demo but requirements are still ambiguous; clarify one question at a time, confirm the business loop, then build and scenario-test the demo.'
---

# 先提问再实施完整 Demo

## Overview

用于完整 demo 交付前的需求澄清和闭环交付。重点是先确认业务闭环，再给可运行、可体验、经过真实场景自测的 demo。

## Trigger

- 用户要求生成完整 demo、原型、网站、应用或工具。
- 需求还模糊，但用户希望最终能直接运行和测试。
- 用户强调先提问、再实施、不要零碎代码片段。

## Required Inputs

- 目标用户、核心业务闭环、数据对象、关键流程。
- 技术栈偏好、运行环境、UI/交互预期。
- 测试账号、样例数据、验收动作和必须覆盖的功能。

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
